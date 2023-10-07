# Holybro Pixhawk RPi CM4 Baseboard

The [Holybro Pixhawk RPi CM4 Baseboard (opens new window)](https://holybro.com/products/pixhawk-rpi-cm4-baseboard) is a single-board solution that pre-integrates a (swappable) Pixhawk flight controller with the Raspberry Pi CM4 companion computer ("RPi"). The baseboard has a compact form factor with all the connections needed for development.

The flight controller module is internally connected to RPi CM4 through `TELEM2`, but may alternatively be connected using Ethernet with the provided external cable.

This baseboard is plug-in compatible with Holybro Pixhawk 5X, Holybro Pixhawk 6X, and any other Pixhawk controller that follows the [Pixhawk Autopilot Bus Standard (opens new window)](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-010%20Pixhawk%20Autopilot%20Bus%20Standard.pdf) guidelines for mechanical compatibility across vendors.

### [#](broken-reference) Purchase <a href="#purchase" id="purchase"></a>

*   [Holybro Pixhawk RPi CM4 Baseboard (opens new window)](https://holybro.com/products/pixhawk-rpi-cm4-baseboard) (www.holybro.com)

    The baseboard can be purchased with or without an RPi CM4 and/or flight controller:

    * The Raspberry Pi CM4 (CM4008032) supplied by Holybro has the following specification:
      * RAM: 8GB
      * eMMC: 32GB
      * Wireless: No
    * The recommended minimum specification for the RPi CM4 is:
      * RAM: 4GB (or 8GB)
      * eMMC: 16GB
      * Wireless: Yes

### [#](broken-reference) Connections & Ports <a href="#connections-ports" id="connections-ports"></a>

The diagram below shows all the connectors and ports on the baseboard.

#### [#](broken-reference) RPi CM4 & FC Serial Connection <a href="#rpi-cm4-fc-serial-connection" id="rpi-cm4-fc-serial-connection"></a>

The flight controller `TELEM2` port is internally connected to RPi CM4 as shown:

| RPi CM4 | FC TELEM2 (FMU) |
| ------- | --------------- |
| GPIO14  | TXD             |
| GPIO15  | RXD             |
| GPIO16  | CTS             |
| GPIO17  | RTS             |

Note

The connection must be also be [configured in both RPi and PX4](broken-reference) (unless [Ethernet](broken-reference) is used instead).

### [#](broken-reference) Installing the Flight Controller <a href="#installing-the-flight-controller" id="installing-the-flight-controller"></a>

A plug-compatible flight controller such as Holybro Pixhawk 5X and Holybro Pixhawk 6X can simply be pushed into the module slot.

Flight controllers that have a different form factor will need additional wiring.

### [#](broken-reference) Installing the RPi CM4 Companion <a href="#installing-the-rpi-cm4-companion" id="installing-the-rpi-cm4-companion"></a>

This section shows how to install/attach a Raspberry Pi CM4 to the baseboard.

To install the Raspberry Pi CM4 companion computer:

1. Disconnect the `FAN` wiring.
2. Remove these 4 screws on the back side of the baseboard.
3. Remove the baseboard case, install the CM4, and use the 4 screws to attach it (as shown):
4. Reattach the cover.

### [#](broken-reference) Power Module Wiring <a href="#power-module-wiring" id="power-module-wiring"></a>

The PM03D power module is supplied with the board.

The RPi CM4 and flight controller must be powered separately:

* The flight controller is powered via the CLIK-Mate cable to `POWER1` or `POWER2` port
* The RPi CM4 is powered by the `USB C` (CM4 Slave) connection. You can also use your own power supply to power the RPi CM4 baseboard.

The image below shows the wiring in greater detail.

### [#](broken-reference) Flashing the RPi CM4 <a href="#flashing-the-rpi-cm4" id="flashing-the-rpi-cm4"></a>

This section explains how you install your preferred Linux distro, such as "Raspberry Pi OS 64bit" onto the RPi EMCC.

Notes:

* If you are using PX4, you will need to use PX4 version 1.13.1 or newer for PX4 to recognize this baseboard.
* The fan does not indicate if the RPi CM4 is powered/running or not.
* The power module plugged into Power1/2 does not power the RPi part. You can use the additional USB-C Cable from the PM03D power module to the CM4 Slave USB-C port.
* The Micro-HDMI port is an output port.
* RPi CM4 boards that do not have Wifi device will not connect automatically. In this case you will need to plug it into a router or plug a compatible Wifi dongle into the CM4 Host ports.

#### [#](broken-reference) Flash EMMC <a href="#flash-emmc" id="flash-emmc"></a>

To flash a RPi image onto EMMC.

1. Switch Dip-Switch to `RPI`.
2. Connect computer to USB-C _CM4 Slave_ port used to power & flash the RPi.
3. Get `usbboot`, build it and run it.
4. You can now install your preferred Linux distro using The `rpi-imager`. Make sure you add WiFi and SSH settings (hidden behind the gear/advanced symbol).
5. Once done, unplugging USB-C CM4 Slave (this will unmount the volumes, and power off the CM4).
6. Switch Dip-Switch back to `EMMC`.
7. Power on CM4 by providing power to USB-C CM4 Slave port.
8. To check if it’s booting/working you can either:
   * Check there is HDMI output
   * Connect via SSH (if set up in rpi-imager, and WiFi is available).

### [#](broken-reference) Configure PX4 to CM4 MAVLink Serial Connection <a href="#configure-px4-to-cm4-mavlink-serial-connection" id="configure-px4-to-cm4-mavlink-serial-connection"></a>

Note

If you are using [Ethernet](broken-reference) to connect the FC and RPi, this setup is not needed.

The Pixhawk FC module is [internally connected to the RPi CM4](broken-reference) using `TELEM2` (`/dev/ttyS4`). The FC and RPi CM4 must both be configured to communicate over this port.

#### [#](broken-reference) FC Serial Port Setup <a href="#fc-serial-port-setup" id="fc-serial-port-setup"></a>

The FC should be set up to connect to the `TELEM2` port correctly by default. If not, you can configure the port using the parameters as shown.

To enable this MAVLink instance on the FC:

1. Connect a computer running QGroundControl via USB Type C port on the baseboard labeled `FC`
2. Set the parameters:
   * `MAV_1_CONFIG` = `102`
   * `MAV_1_MODE = 2`
   * `SER_TEL2_BAUD` = `921600`
3. Reboot the FC.

#### [#](broken-reference) RPi Serial Port Setup <a href="#rpi-serial-port-setup" id="rpi-serial-port-setup"></a>

On the RPi side:

1. Connect to the RPi (using WiFi, a router, or a Wifi Dongle).
2. Enable the RPi serial port by running `RPi-config`
   * Go to `3 Interface Options`, then `I6 Serial Port`. Then choose:
     * `login shell accessible over serial → No`
     * `serial port hardware enabled` → `Yes`
3. Finish, and reboot. (This will add `enable_uart=1` to `/boot/config.txt`, and remove `console=serial0,115200` from `/boot/cmdline.txt`
4. Now MAVLink traffic should be available on `/dev/serial0` at a baudrate of 921600.

### [#](broken-reference) Try out MAVSDK-Python <a href="#try-out-mavsdk-python" id="try-out-mavsdk-python"></a>

1. Make sure the CM4 is connected to the internet, e.g. using a wifi, or ethernet.
2. Install MAVSDK Python:
3. Copy an example from the [MAVSDK-Python examples (opens new window)](https://github.com/mavlink/MAVSDK-Python/tree/main/examples).
4. Change the `system_address="udp://:14540"` to `system_address="serial:///dev/serial0:921600"`
5. Try out the example. Permission for the serial port should already be available through the `dialout` group.

### [#](broken-reference) Ethernet Connection (Optional) <a href="#ethernet-connection-optional" id="ethernet-connection-optional"></a>

The flight controller module is [internally connected to RPi CM4](broken-reference) from `TELEM2` (Serial).

You can also set up a local Ethernet connection between them using the supplied cable. Ethernet connectivity provides a fast, reliable, and flexible communication alternative to using USB or other serial connections.

#### [#](broken-reference) Connect the Cable <a href="#connect-the-cable" id="connect-the-cable"></a>

To set up a local ethernet connection between CM4 and the flight computer, the two ethernet ports need to be connected using the provided 8 pin to 4 pin connector.

The pinout of the cable is:

| CM4 Eth 8 Pin | FC ETH 4 Pin |
| ------------- | ------------ |
| A             | B            |
| B             | A            |
| C             | D            |
| D             | C            |
| -             | N/A          |
| -             | N/A          |
| -             | N/A          |
| -             | N/A          |

#### [#](broken-reference) IP Setup on CM4 <a href="#ip-setup-on-cm4" id="ip-setup-on-cm4"></a>

Since there is no DHCP server active in this configuration, the IP addresses have to be set manually:

First, connect to the CM4 via SSH by connecting to the CM4’s WiFi (or use a Wifi dongle). Once the ethernet cables are plugged in, the `eth0` network interface seems to switch from DOWN to UP.

You can check the status using:

You can also try to enable it manually:

It then seems to automatically set a link-local address, for this example it looks like this:

This means the CM4’s ethernet IP is 169.254.21.183.

[**#**](broken-reference) **IP Setup on FC**

Now connect to the NuttX shell (using a console, or the MAVLink shell), and check the status of the link:

For this example, it is DOWN at first.

To set it to UP:

Now check the config again:

However, it doesn’t have an IP yet. Set one that is similar to the one on the RPi CM4:

Then check it:

Now the devices should be able to ping each other.

Note that this configuration is ephemeral and will be lost after a reboot, so we’ll need to find a way to configure it statically.

[**#**](broken-reference) **Ping Test**

First from the CM4:

Then from the flight controller in NuttShell:

[**#**](broken-reference) **MAVLink/MAVSDK Test**

For this, we need to set the MAVLink instance to send traffic to the CM4's IP address:

For an initial test we can do:

This will send MAVLink traffic on UDP to port 14540 (the MAVSDK/MAVROS port) to that IP which means MAVSDK can just listen to any UDP arriving at that default port.

To run a MAVSDK example, install mavsdk via pip, and try out an example from [MAVSDK-Python/examples (opens new window)](https://github.com/mavlink/MAVSDK-Python/tree/main/examples).

For instance:

### [#](broken-reference) See Also <a href="#see-also" id="see-also"></a>

* [Get The Pixhawk Raspberry Pi CM4 Baseboard By Holybro Talking With PX4 (opens new window)](https://px4.io/get-the-pixhawk-raspberry-pi-cm4-baseboard-by-holybro-talking-with-px4/) (px4.io blog):
  * Tutorial showing how to connect Pixhawk 6X + Raspberry Pi on CM4 baseboard via wired Ethernet.
