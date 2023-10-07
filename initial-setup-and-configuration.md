# Initial Setup & Configuration

We recommend that developers obtain the basic equipment and software described below (or similar)

### [#](broken-reference) Basic Equipment <a href="#basic-equipment" id="basic-equipment"></a>

TIP

PX4 can be used with a much wider range of equipment than described here, but new developers will benefit from going with one of the standard setups. A Taranis RC plus a Note 4 tablet make up for a very inexpensive field kit.

The equipment below is highly recommended:

* **Remote control** for the safety pilot
  * Taranis Plus remote control (or equivalent)
* **Development computer**
  * MacBook Pro (early 2015 and later) with OSX 10.15 or later
  * Lenovo Thinkpad 450 (i5) with Ubuntu Linux 18.04 or later
* **Ground control station** (computer or tablet):
  * iPad (requires Wifi telemetry adapter)
  * Any MacBook or Ubuntu Linux laptop (can be the development computer)
  * Samsung Note 4 or equivalent (any recent Android tablet or phone with a large enough screen to run _QGroundControl_ effectively).
* **Vehicle capable of running PX4**:
  * [Get a prebuilt vehicle](.gitbook/assets/complete\_vehicles)
  * [Build your own](.gitbook/assets/airframes)
* **Safety glasses**
* **Tether** (multicopter only - for more risky tests)

### [#](broken-reference) Vehicle Configuration <a href="#vehicle-configuration" id="vehicle-configuration"></a>

Install the [QGroundControl Daily Build (opens new window)](https://docs.qgroundcontrol.com/master/en/releases/daily\_builds.html) for a **desktop OS**.

To configure the vehicle:

1. [Install PX4 firmware](https://about/main/en/config/firmware.html#installing-px4-master-beta-or-custom-firmware) (including "custom" firmware with your own changes).
2. Start with the airframe that best-matches your vehicle from the [airframe reference](broken-reference).
3. [Basic Configuration](.gitbook/assets/config) explains how to perform basic configuration.
4. Parameter Configuration explains how you can find and modify individual parameters.

Note

* _QGroundControl_ mobile variants do not support vehicle configuration.
* The _daily build_ includes development tools and new features that are not available in the official release.
* Configuration in the airframe reference have been flown on real vehicles, and are a good starting point for "getting off the ground".

Last Updated: 8/3/2022, 12:42:55 AM
