# Flight Controller Selection

Flight controllers are the "brains" of an unmanned vehicle. PX4 can run on [many flight controller boards](.gitbook/assets/flight\_controller).

You should select a board that suits the physical constraints of your vehicle, the activities you wish to perform, and of course cost.

### [#](broken-reference) Pixhawk Series <a href="#pixhawk-series" id="pixhawk-series"></a>

[Pixhawk Series](broken-reference) open-hardware flight controllers run PX4 on NuttX OS. With many form factors, there are versions targeted towards many use cases and market segments.

[Pixhawk Standard Autopilots](broken-reference) are used as the PX4 reference platform. They are supported and tested by the PX4 development team, and are highly recommended.

### [#](broken-reference) Manufacturer-supported Controllers <a href="#manufacturer-supported-controllers" id="manufacturer-supported-controllers"></a>

Other flight controllers are [manufacturer-supported](broken-reference). This includes FCs that are heavily based on the Pixhawk standard (but which are not fully compliant), and many others.

Note that manufacturer-supported controllers can be just as "good" (or better) than those which are Pixhawk-standard.

### [#](broken-reference) Autopilots for Computationally Intensive Tasks <a href="#autopilots-for-computationally-intensive-tasks" id="autopilots-for-computationally-intensive-tasks"></a>

Dedicated flight controllers like Pixhawk are not usually well-suited for general purpose computing or running computationally intensive tasks. For more computing power, the most common approach is to run those applications on a separate onboard [Companion Computer](.gitbook/assets/companion\_computer).

Integrated companion computer/flight controller solutions include:

* [Holybro Pixhawk RPI CM4 Baseboard](broken-reference)
* Other options in [Companion Computer > Integrated Companion/Flight Controller Boards](https://about/main/en/companion\_computer/#integrated-companion-flight-controller-boards)

PX4 can also run natively on Raspberry Pi (this approach is not generally considered as "robust" as having a separate companion):

* Raspberry Pi 2/3 Navio2
* Raspberry Pi 2/3/4 PilotPi Shield

### [#](broken-reference) Commercial UAVs that can run PX4 <a href="#commercial-uavs-that-can-run-px4" id="commercial-uavs-that-can-run-px4"></a>

PX4 is available on many popular commercial drone products, including some that ship with PX4 and others that can be updated with PX4 (allowing you to add mission planning and other PX4 Flight modes to your vehicle).

For more information see [Complete Vehicles](.gitbook/assets/complete\_vehicles).

Last Updated: 7/10/2023, 10:18:46 PM
