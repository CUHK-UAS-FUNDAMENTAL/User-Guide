# Basic Concepts

This topic provides a basic introduction to drones and using PX4 (it is meant mostly for novice users but is also a good introduction for experienced users).

If you are already familiar with the basic concepts, you can move on to [Basic Assembly](.gitbook/assets/assembly) to learn how to wire your specific autopilot hardware. To load firmware and set up the vehicle with _QGroundControl_, see [Basic Configuration](.gitbook/assets/config).

### [#](broken-reference) What is a Drone? <a href="#what-is-a-drone" id="what-is-a-drone"></a>

A drone is an unmanned "robotic" vehicle that can be remotely or autonomously controlled.

Drones are used for many [consumer, industrial, government and military applications (opens new window)](https://px4.io/ecosystem/commercial-systems/). These include (non exhaustively): aerial photography/video, carrying cargo, racing, search and surveying etc.

Different types of drones are used for air, ground, sea, and underwater. These are (more formally) referred to as Unmanned Aerial Vehicles (UAV), Unmanned Aerial Systems (UAS), Unmanned Ground Vehicles (UGV), Unmanned Surface Vehicles (USV), Unmanned Underwater Vehicles (UUV).

The "brain" of the drone is called an autopilot. It consists of _flight stack_ software running on _vehicle controller_ ("flight controller") hardware.

Some drones also have a separate on-vehicle [companion computer](broken-reference). These provide powerful general-purpose computing platform for networking, computer vision, and many other tasks.

### [#](broken-reference) PX4 Autopilot <a href="#px4-autopilot" id="px4-autopilot"></a>

[PX4 (opens new window)](https://px4.io/) is powerful open source autopilot _flight stack_.

Some of PX4's key features are:

* Controls [many different vehicle frames/types](broken-reference), including: aircraft (multicopters, fixed wing aircraft and VTOLs), ground vehicles and underwater vehicles.
* Great choice of hardware for [vehicle controller](broken-reference), sensors and other peripherals.
* Flexible and powerful [flight modes](broken-reference) and [safety features](broken-reference).
* Robust and deep integration with [companion computers](broken-reference) and [robotics APIs](.gitbook/assets/robotics) (ROS 2, [MAVSDK (opens new window)](http://mavsdk.mavlink.io/)).

PX4 is a core part of a broader drone platform that includes the [QGroundControl](broken-reference) ground station, [Pixhawk hardware (opens new window)](https://pixhawk.org/), and [MAVSDK (opens new window)](http://mavsdk.mavlink.io/) for integration with companion computers, cameras and other hardware using the MAVLink protocol. PX4 is supported by the [Dronecode Project (opens new window)](https://www.dronecode.org/).

### [#](broken-reference) QGroundControl <a href="#qgroundcontrol" id="qgroundcontrol"></a>

The Dronecode ground control station is called [QGroundControl (opens new window)](http://qgroundcontrol.com/). You can use _QGroundControl_ to load (flash) PX4 onto the [vehicle control hardware](broken-reference), you can setup the vehicle, change different parameters, get real-time flight information and create and execute fully autonomous missions.

_QGroundControl_ runs on Windows, Android, MacOS or Linux. Download and install it from [here (opens new window)](http://qgroundcontrol.com/downloads/).

### [#](broken-reference) Vehicle/Flight Controller Board <a href="#vehicle-flight-controller-board" id="vehicle-flight-controller-board"></a>

PX4 was initially designed to run on [Pixhawk Series](broken-reference) controllers, but can now run on Linux computers and other hardware. You should select a board that suits the physical constraints of your vehicle, the activities you wish to perform, and of course cost.

For more information see: [Flight Controller Selection](broken-reference).

### [#](broken-reference) Sensors <a href="#sensors" id="sensors"></a>

PX4 uses sensors to determine vehicle state (needed for stabilization and to enable autonomous control). The system _minimally requires_ a gyroscope, accelerometer, magnetometer (compass) and barometer. A GPS or other positioning system is needed to enable all automatic [modes](https://about/main/en/getting\_started/flight\_modes.html#categories), and some assisted modes. Fixed wing and VTOL-vehicles should additionally include an airspeed sensor (very highly recommended).

For more information see:

* Sensors
* [Peripherals](.gitbook/assets/peripherals)

### [#](broken-reference) Outputs: Motors, Servos, Actuators <a href="#outputs-motors-servos-actuators" id="outputs-motors-servos-actuators"></a>

PX4 uses _outputs_ to control: motor speed (e.g. via [ESC](broken-reference)), flight surfaces like ailerons and flaps, camera triggers, parachutes, grippers, and many other types of payloads.

The outputs may be PWM ports or DroneCAN nodes (e.g. DroneCAN motor controllers). The images below show the PWM output ports for Pixhawk 4 and Pixhawk 4 mini.

The outputs are divided into `MAIN` and `AUX` outputs, and individually numbered (i.e. `MAINn` and `AUXn`, where `n` is 1 to usually 6 or 8). They might also be marked as `IO PWM Out` and `FMU PWM OUT` (or similar).

WARNING

A flight controller may only have `MAIN` PWM outputs (like the _Pixhawk 4 Mini_), or may have only 6 outputs on either `MAIN` or `AUX`. Ensure that you select a controller that has enough ports/outputs for your [airframe](broken-reference).

You can connect almost any output to any motor or other actuator, by assigning the associated function ("Motor 1") to the desired output ("AUX1") in QGroundControl: Actuator Configuration and Testing. Note that the functions (motor and control surface actuator positions) for each frame are given in the [Airframe Reference](broken-reference).

**Notes:**

* Pixhawk controllers have an FMU board and _may_ have a separate IO board. If there is an IO board, the `AUX` ports are connected directly to the FMU and the `MAIN` ports are connected to the IO board. Otherwise the `MAIN` ports are connected to the FMU, and there are no `AUX` ports.
* The FMU output ports can use D-shot or _One-shot_ protocols (as well as PWM), which provide much lower-latency behaviour. This can be useful for racers and other airframes that require better performance.
* There are only 6-8 outputs in `MAIN` and `AUX` because most flight controllers only have this many PWM/Dshot/Oneshot outputs. In theory there can be many more outputs if the bus supports it (i.e. a UAVCAN bus is not limited to this few nodes).

### [#](broken-reference) ESCs & Motors <a href="#escs-motors" id="escs-motors"></a>

Many PX4 drones use brushless motors that are driven by the flight controller via an Electronic Speed Controller (ESC) (the ESC converts a signal from the flight controller to an appropriate level of power delivered to the motor).

For information about what ESC/Motors are supported by PX4 see:

* ESC & Motors
* ESC Calibration
* [ESC Firmware and Protocols Overview (opens new window)](https://oscarliang.com/esc-firmware-protocols/) (oscarliang.com)

### [#](broken-reference) Battery/Power <a href="#battery-power" id="battery-power"></a>

PX4 drones are mostly commonly powered from Lithium-Polymer (LiPo) batteries. The battery is typically connected to the system using a _Power Module_ or _Power Management Board_, which provide separate power for the flight controller and to the ESCs (for the motors).

Information about batteries and battery configuration can be found in Battery Configuration and the guides in [Basic Assembly](.gitbook/assets/assembly) (e.g. [Pixhawk 4 Wiring Quick Start > Power](https://about/main/en/assembly/quick\_start\_pixhawk4.html#power)).

### [#](broken-reference) Manual Control <a href="#manual-control" id="manual-control"></a>

Pilots can control a vehicle manually using either a [Radio Control (RC) System](broken-reference) or a [Joystick/Gamepad](broken-reference) controller connected via QGroundControl.

Note

PX4 does not _require_ a manual control system for autonomous flight modes.

Note

Both methods can be used for most manual control use cases, such as surveys. RC systems are recommended when first tuning/testing a new frame design or when flying racers/acrobatically (and in other cases where low latency is important).

#### [#](broken-reference) Radio Control (RC) <a href="#radio-control-rc" id="radio-control-rc"></a>

Radio Control (RC) systems can be used to manually control PX4.

They consist of a ground based RC controller that uses a radio transmitter to communicate stick/control positions to a receiver on the vehicle. Some RC systems can additionally receive telemetry information back from the autopilot.

RC System Selection explains how to choose an RC system. Other related topics include:

* Radio/Remote Control Setup - Remote control configuration in _QGroundControl_.
* Flying 101 - Learn how to fly with a remote control.
* FrSky Telemetry - Set up the RC transmitter to receive telemetry/status updates from PX4.

#### [#](broken-reference) GCS Joystick Controller <a href="#gcs-joystick-controller" id="gcs-joystick-controller"></a>

A Joystick/Gamepad connected through _QGroundControl_ can also be used to manually control PX4.

With this approach, QGroundControl translates stick/button information from a connected Joystick into MAVLink-protocol messages, which are then sent to PX4 using the shared telemetry radio link. The telemetry radio must have sufficient bandwidth for both manual control and other telemetry messages, and of course this approach means that you must have a ground station running QGroundControl.

Joysticks are also used to manually fly PX4 in a [simulator](.gitbook/assets/simulation).

### [#](broken-reference) Safety Switch <a href="#safety-switch" id="safety-switch"></a>

Some vehicles have a _safety switch_ that must be engaged before the vehicle can be [armed](broken-reference) (when armed, motors are powered and propellers can turn).

Commonly the safety switch is integrated into a GPS unit, but it may also be a separate physical component.

### [#](broken-reference) Data/Telemetry Radios <a href="#data-telemetry-radios" id="data-telemetry-radios"></a>

[Data/Telemetry Radios](.gitbook/assets/telemetry) can provide a wireless MAVLink connection between a ground control station like _QGroundControl_ and a vehicle running PX4. This makes it possible to tune parameters while a vehicle is in flight, inspect telemetry in real-time, change a mission on the fly, etc.

### [#](broken-reference) Offboard/Companion Computer <a href="#offboard-companion-computer" id="offboard-companion-computer"></a>

A [Companion Computer](.gitbook/assets/companion\_computer) (also referred to as "mission computer" or "offboard computer"), is a separate on-vehicle computer that communicates with PX4 to provide higher level command and control.

The companion computer usually runs Linux, as this is a much better platform for "general" software development, and allows drones to leverage pre-existing software for computer vision, networking, and so on.

The flight controller and companion computer may be pre-integrated into a single baseboard, simplifying hardware development, or may be separate, and are connected via a serial cable, Ethernet cable, or wifi. The companion computer typically communicates with PX4 using a high level Robotics API such as [MAVSDK (opens new window)](https://mavsdk.mavlink.io/) or ROS 2.

Relevant topics include:

* [Companion Computers](.gitbook/assets/companion\_computer)
* Off-board Mode - Flight mode for offboard control of PX4 from a GCS or companion computer.
* [Robotics APIs](.gitbook/assets/robotics)

### [#](broken-reference) SD Cards (Removable Memory) <a href="#sd-cards-removable-memory" id="sd-cards-removable-memory"></a>

PX4 uses SD memory cards for storing [flight logs](broken-reference), and they are also required in order to use UAVCAN peripherals and fly missions.

By default, if no SD card is present PX4 will play the [format failed (2-beep)](https://about/main/en/getting\_started/tunes.html#format-failed) tune twice during boot (and none of the above features will be available).

TIP

The maximum supported SD card size on Pixhawk boards is 32GB. The _SanDisk Extreme U3 32GB_ is [highly recommended](https://about/main/en/dev\_log/logging.html#sd-cards).

SD cards are never-the-less optional. Flight controllers that do not include an SD Card slot may:

* Disable notification beeps are disabled using the parameter [CBRK\_BUZZER](https://about/main/en/advanced\_config/parameter\_reference.html#CBRK\_BUZZER).
* [Stream logs](https://about/main/en/dev\_log/logging.html#log-streaming) to another component (companion).
* Store missions in RAM/FLASH.

### [#](broken-reference) Arming and Disarming <a href="#arming-and-disarming" id="arming-and-disarming"></a>

A vehicle is said to be _armed_ when all motors and actuators are powered, and _disarmed_ when nothing is powered. There is also a _prearmed_ state when only actuators are powered.

WARNING

Armed vehicles can be dangerous as propellors will be spinning.

Arming is triggered by default (on Mode 2 transmitters) by holding the RC throttle/yaw stick on the _bottom right_ for one second (to disarm, hold stick on bottom left). It is alternatively possible to configure PX4 to arm using an RC switch or button (and arming MAVLink commands can also be sent from a ground station).

To reduce accidents, vehicles should be armed as little as possible when the vehicle is on the ground. By default, vehicles are:

* _Disarmed_ or _Prearmed_ (motors unpowered) when not in use, and must be explicitly _armed_ before taking off.
* Automatically disarm/prearm if the vehicle does not take off quickly enough after arming (the disarm time is configurable).
* Automatically disarm/prearm shortly after landing (the time is configurable).
* Arming is prevented if the vehicle is not in a "healthy" state.
* Arming is prevented if the vehicle has a [safety switch](broken-reference) that has not been engaged.
* Arming is prevented if a VTOL vehicle is in fixed-wing mode ([by default](https://about/main/en/advanced\_config/parameter\_reference.html#CBRK\_VTOLARMING)).

When prearmed you can still use actuators, while disarming unpowers everything. Prearmed and disarmed should both safe, and a particular vehicle may support either or both.

TIP

Sometimes a vehicle will not arm for reasons that are not obvious. QGC v4.2.0 (Daily build at time of writing) and later provide an arming check report in [Fly View > Arming and Preflight Checks (opens new window)](https://docs.qgroundcontrol.com/master/en/FlyView/FlyView.html#arm). From PX4 v1.14 this provides comprehensive information about arming problems along with possible solutions.

A detailed overview of arming and disarming configuration can be found here: Prearm, Arm, Disarm Configuration.

### [#](broken-reference) Flight Modes <a href="#flight-modes" id="flight-modes"></a>

Flight modes provide different types/levels of vehicle automation and autopilot assistance to the user (pilot). _Autonomous modes_ are fully controlled by the autopilot, and require no pilot/remote control input. These are used, for example, to automate common tasks like takeoff, returning to the home position, and landing. Other autonomous modes execute pre-programmed missions, follow a GPS beacon, or accept commands from an offboard computer or ground station.

_Manual modes_ are controlled by the user (via the RC control sticks/joystick) with assistance from the autopilot. Different manual modes enable different flight characteristics - for example, some modes enable acrobatic tricks, while others are impossible to flip and will hold position/course against wind.

TIP

Not all flight modes are available on all vehicle types, and some modes can only be used when specific conditions have been met (e.g. many modes require a global position estimate).

An overview of the available flight modes can be found here. Instructions for how to set up your remote control switches to turn on different flight modes is provided in Flight Mode Configuration.

### [#](broken-reference) Safety Settings (Failsafe) <a href="#safety-settings-failsafe" id="safety-settings-failsafe"></a>

PX4 has configurable failsafe systems to protect and recover your vehicle if something goes wrong! These allow you to specify areas and conditions under which you can safely fly, and the action that will be performed if a failsafe is triggered (for example, landing, holding position, or returning to a specified point).

Note

You can only specify the action for the _first_ failsafe event. Once a failsafe occurs the system will enter special handling code, such that subsequent failsafe triggers are managed by separate system level and vehicle specific code.

The main failsafe areas are listed below:

* Low Battery
* Remote Control (RC) Loss
* Position Loss (global position estimate quality is too low).
* Offboard Loss (e.g. lose connection to companion computer)
* Data Link Loss (e.g. lose telemetry connection to GCS).
* Geofence Breach (restrict vehicle to flight within a virtual cylinder).
* Mission Failsafe (prevent a previous mission being run at a new takeoff location).
* Traffic avoidance (triggered by transponder data from e.g. ADSB transponders).

For more information see: Safety (Basic Configuration).

### [#](broken-reference) Heading and Directions <a href="#heading-and-directions" id="heading-and-directions"></a>

All the vehicles, boats and aircraft have a heading direction or an orientation based on their forward motion.

Note

For a VTOL Tailsitter the heading is relative to the multirotor configuration (i.e. vehicle pose during takeoff, hovering, landing).

It is important to know the vehicle heading direction in order to align the autopilot with the vehicle vector of movement. Multicopters have a heading even when they are symmetrical from all sides! Usually manufacturers use a colored props or colored arms to indicate the heading.

In our illustrations we will use red coloring for the front propellers of multicopter to show heading.

You can read in depth about heading in Flight Controller Orientation
