# Pixhawk Series

[Pixhawk® (opens new window)](https://pixhawk.org/) is an independent open-hardware project providing readily-available, low-cost, and high-end, _autopilot hardware designs_ to the academic, hobby and industrial communities.

Pixhawk is the reference hardware platform for PX4, and runs PX4 on the [NuttX (opens new window)](https://nuttx.apache.org/) OS.

Manufacturers have created many different boards based on the open designs, with form factors that are optimised for applications from cargo carrying though to first person view (FPV) racers.

TIP

For computationally intensive tasks (e.g. computer vision) you will need a separate companion computer (e.g. Raspberry Pi 2/3 Navio2) or a platform with an integrated companion solution.

### [#](broken-reference) Key Benefits <a href="#key-benefits" id="key-benefits"></a>

Key benefits of using a _Pixhawk series_ controller include:

* Software support - as PX4 reference hardware these are our best-maintained boards.
* Flexibility in terms of hardware peripherals that can be attached.
* High quality.
* Highly customizable in terms of form factor.
* Widely-used and thus well-tested/stable.
* Automated update of latest firmware via _QGroundControl_ (end-user friendly).

### [#](broken-reference) Supported Boards <a href="#supported-boards" id="supported-boards"></a>

The PX4 Project uses [Pixhawk Standard Autopilots](broken-reference) as reference hardware. These are the controllers that are fully compatible with the Pixhawk standard (including use of trademarks) and that are still being manufactured.

Note

The PX4 maintenance and test teams maintain and support these standard boards.

Pixhawk-like boards that are not fully compliant with the specification may be [manufacturer-supported](broken-reference), experimental/discontinued, or unsupported.

The rest of this topic explains a bit more about the Pixhawk series, but is not required reading.

### [#](broken-reference) Background <a href="#background" id="background"></a>

The [Pixhawk project (opens new window)](https://pixhawk.org/) creates open hardware designs in the form of schematics, which define a set of components (CPU, sensors, etc.) and their connections/pin mappings.

Manufacturers are encouraged to take the [open designs (opens new window)](https://github.com/pixhawk/Hardware) and create products that are best suited to a particular market or use case (the physical layout/form factor not part of the open specification). Boards based on the same design are binary compatible.

The project also creates reference autopilot boards based on the open designs, and shares them under the same [licence](broken-reference).

#### [#](broken-reference) FMU Versions <a href="#fmu-versions" id="fmu-versions"></a>

The Pixhawk project has created a number of different open designs/schematics. All boards based on a design should be binary compatible (run the same firmware).

Each design is named using the designation: FMUvX (e.g.: FMUv1, FMUv2, FMUv3, FMUv4, etc.). Higher FMU numbers indicate that the board is more recent, but may not indicate increased capability (versions can be almost identical - differing only in connector wiring).

PX4 _users_ generally do not need to know very much about FMU versions:

* _QGroundControl_ automatically downloads the correct firmware for a connected autopilot (based on its FMU version "under the hood").
* Choosing a controller is usually based on physical constraints/form factor rather than FMU version.

Note

The exception is that if you're using FMUv2 firmware it is [limited to 1MB of flash](https://about/main/en/flight\_controller/silicon\_errata.html#fmuv2-pixhawk-silicon-errata). In order to fit PX4 into this limited space, many modules are disabled by default. You may find that some [parameters are missing](https://about/main/en/advanced\_config/parameters.html#missing) and that some hardware does not work "out of the box".

PX4 _developers_ need to know the FMU version of their board, as this is required to build custom hardware.

At very high level, the main differences are:

* **FMUv2:** Single board with STM32427VI processor (Pixhawk 1 (Discontinued), pix32, Pixfalcon, Drotek DroPix)
* **FMUv3:** Identical to FMUv2, but usable flash doubled to 2MB (Hex Cube Black,CUAV Pixhack v3,mRo Pixhawk, Pixhawk Mini (Discontinued))
* **FMUv4:** Increased RAM. Faster CPU. More serial ports. No IO processor (Pixracer)
* **FMUv4-PRO:** Slightly increased RAM. More serial ports. IO processor (Pixhawk 3 Pro)
* **FMUv5:** New processor (F7). Much faster. More RAM. More CAN buses. Much more configurable. (Pixhawk 4,CUAV v5,CUAV V5+,CUAV V5 nano)
* **FMUv5X:** New processor (F7). Much faster, Modular design. More reliable. More Redundancy. More RAM. More CAN buses. Much more configurable & customizable .(Pixhawk 5X, Skynode)

#### [#](broken-reference) Licensing and Trademarks <a href="#licensing-and-trademarks" id="licensing-and-trademarks"></a>

Pixhawk project schematics and reference designs are licensed under [CC BY-SA 3 (opens new window)](https://creativecommons.org/licenses/by-sa/3.0/legalcode).

The license allows you to use, sell, share, modify and build on the files in almost any way you like - provided that you give credit/attribution, and that you share any changes that you make under the same open source license (see the [human readable version of the license (opens new window)](https://creativecommons.org/licenses/by-sa/3.0/) for a concise summary of the rights and obligations).

Note

Boards that are _derived directly_ from Pixhawk project schematic files (or reference boards) must be open sourced. They can't be commercially licensed as proprietary products.

Manufacturers can create (compatible) _fully independent products_ by first generating fresh schematic files that have the same pin mapping/components as the FMU designs. Products that are based on independently created schematics are considered original works, and can be licensed as required.

Product names/brands can also be trademarked. Trademarked names may not be used without the permission of the owner.

TIP

_Pixhawk_ is a trademark, and cannot be used in product names without permission.

### [#](broken-reference) Additional Information <a href="#additional-information" id="additional-information"></a>

#### [#](broken-reference) LEDs <a href="#leds" id="leds"></a>

All _Pixhawk-series_ flight controllers support:

* A user facing RGB _UI LED_ to indicate the current _readiness to fly_ status of the vehicle. This is typically a superbright I2C peripheral, which may or may not be mounted on the board (i.e. FMUv4 does not have one on board and typically uses an LED mounted on the GPS).
* Three _Status LED_s that provide lower level power status, bootloader mode and activity, and error information.

To interpret the LEDs see: LED Meanings.
