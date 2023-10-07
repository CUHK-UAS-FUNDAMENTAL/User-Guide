# PX4 Architectural Overview

PX4 consists of two main layers: the [flight stack](broken-reference) is an estimation and flight control system, and the [middleware](broken-reference) is a general robotics layer that can support any type of autonomous robot, providing internal/external communications and hardware integration.

All PX4 [airframes](.gitbook/assets/airframes) share a single codebase (this includes other robotic systems like boats, rovers, submarines etc.). The complete system design is [reactive (opens new window)](http://www.reactivemanifesto.org/), which means that:

* All functionality is divided into exchangeable and reusable components
* Communication is done by asynchronous message passing
* The system can deal with varying workload

### [#](broken-reference) High-Level Software Architecture <a href="#high-level-software-architecture" id="high-level-software-architecture"></a>

The diagram below provides a detailed overview of the building blocks of PX4. The top part of the diagram contains middleware blocks, while the lower section shows the components of the flight stack.

The source code is split into self-contained modules/programs (shown in `monospace` in the diagram). Usually a building block corresponds to exactly one module.

TIP

At runtime, you can inspect which modules are executed with the `top` command in shell, and each module can be started/stopped individually via `<module_name> start/stop`. While `top` command is specific to NuttX shell, the other commands can be used in the SITL shell (pxh>) as well. For more information about each of these modules see the Modules & Commands Reference.

The arrows show the information flow for the _most important_ connections between the modules. In reality, there are many more connections than shown, and some data (e.g. for parameters) is accessed by most of the modules.

Modules communicate with each other through a publish-subscribe message bus named uORB. The use of the publish-subscribe scheme means that:

* The system is reactive — it is asynchronous and will update instantly when new data is available
* All operations and communication are fully parallelized
* A system component can consume data from anywhere in a thread-safe fashion

Note

This architecture allows every single one of these blocks to be rapidly and easily replaced, even at runtime.

#### [#](broken-reference) Flight Stack <a href="#flight-stack" id="flight-stack"></a>

The flight stack is a collection of guidance, navigation and control algorithms for autonomous drones. It includes controllers for fixed wing, multirotor and VTOL airframes as well as estimators for attitude and position.

The following diagram shows an overview of the building blocks of the flight stack. It contains the full pipeline from sensors, RC input and autonomous flight control (Navigator), down to the motor or servo control (Actuators).

An **estimator** takes one or more sensor inputs, combines them, and computes a vehicle state (for example the attitude from IMU sensor data).

A **controller** is a component that takes a setpoint and a measurement or estimated state (process variable) as input. Its goal is to adjust the value of the process variable such that it matches the setpoint. The output is a correction to eventually reach that setpoint. For example the position controller takes position setpoints as inputs, the process variable is the currently estimated position, and the output is an attitude and thrust setpoint that move the vehicle towards the desired position.

A **mixer** takes force commands (such as "turn right") and translates them into individual motor commands, while ensuring that some limits are not exceeded. This translation is specific for a vehicle type and depends on various factors, such as the motor arrangements with respect to the center of gravity, or the vehicle's rotational inertia.

#### [#](broken-reference) Middleware <a href="#middleware" id="middleware"></a>

The [middleware](.gitbook/assets/middleware) consists primarily of device drivers for embedded sensors, communication with the external world (companion computer, GCS, etc.) and the uORB publish-subscribe message bus.

In addition, the middleware includes a [simulation layer](.gitbook/assets/simulation) that allows PX4 flight code to run on a desktop operating system and control a computer modeled vehicle in a simulated "world".

### [#](broken-reference) Update Rates <a href="#update-rates" id="update-rates"></a>

Since the modules wait for message updates, typically the drivers define how fast a module updates. Most of the IMU drivers sample the data at 1kHz, integrate it and publish with 250Hz. Other parts of the system, such as the `navigator`, don't need such a high update rate, and thus run considerably slower.

The message update rates can be inspected in real-time on the system by running `uorb top`.

### [#](broken-reference) Runtime Environment <a href="#runtime-environment" id="runtime-environment"></a>

PX4 runs on various operating systems that provide a POSIX-API (such as Linux, macOS, NuttX or QuRT). It should also have some form of real-time scheduling (e.g. FIFO).

The inter-module communication (using uORB) is based on shared memory. The whole PX4 middleware runs in a single address space, i.e. memory is shared between all modules.

Note

The system is designed such that with minimal effort it would be possible to run each module in separate address space (parts that would need to be changed include `uORB`, `parameter interface`, `dataman` and `perf`).

There are 2 different ways that a module can be executed:

* **Tasks**: The module runs in its own task with its own stack and process priority.
*   **Work queue tasks**: The module runs on a shared work queue, sharing the same stack and work queue thread priority as other modules on the queue.

    * All the tasks must behave co-operatively as they cannot interrupt each other.
    * Multiple _work queue tasks_ can run on a queue, and there can be multiple queues.
    * A _work queue task_ is scheduled by specifying a fixed time in the future, or via uORB topic update callback.

    The advantage of running modules on a work queue is that it uses less RAM, and potentially results in fewer task switches. The disadvantages are that _work queue tasks_ are not allowed to sleep or poll on a message, or do blocking IO (such as reading from a file). Long-running tasks (doing heavy computation) should potentially also run in a separate task or at least a separate work queue.

Note

Tasks running on a work queue do not show up in [`top`](https://about/main/en/modules/modules\_command.html#top) (only the work queues themselves can be seen - e.g. as `wq:lp_default`). Use [`work_queue status`](https://about/main/en/modules/modules\_system.html#work-queue) to display all active work queue items.

#### [#](broken-reference) Background Tasks <a href="#background-tasks" id="background-tasks"></a>

`px4_task_spawn_cmd()` is used to launch new tasks (NuttX) or threads (POSIX - Linux/macOS) that run independently from the calling (parent) task:

#### [#](broken-reference) OS-Specific Information <a href="#os-specific-information" id="os-specific-information"></a>

[**#**](broken-reference) **NuttX**

[NuttX (opens new window)](https://nuttx.apache.org/) is the primary RTOS for running PX4 on a flight-control board. It is open source (BSD license), light-weight, efficient and very stable.

Modules are executed as tasks: they have their own file descriptor lists, but they share a single address space. A task can still start one or more threads that share the file descriptor list.

Each task/thread has a fixed-size stack, and there is a periodic task which checks that all stacks have enough free space left (based on stack coloring).

[**#**](broken-reference) **Linux/macOS**

On Linux or macOS, PX4 runs in a single process, and the modules run in their own threads (there is no distinction between tasks and threads as on NuttX).
