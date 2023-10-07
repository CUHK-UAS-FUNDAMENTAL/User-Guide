# # Fundamental System User Guide (main)



[![Releases](https://img.shields.io/badge/release-main-blue.svg) (opens new window)](https://github.com/PX4/PX4-Autopilot/releases) [![Discuss](https://img.shields.io/badge/discuss-px4-ff69b4.svg) (opens new window)](https://discuss.px4.io/) [![Discord](https://discordapp.com/api/guilds/1022170275984457759/widget.png?style=shield) (opens new window)](https://discord.gg/dronecode)

PX4 is the _Professional Autopilot_. Developed by world-class developers from industry and academia, and supported by an active world wide community, it powers all kinds of vehicles from racing and cargo drones through to ground vehicles and submersibles.

TIP

This guide contains everything you need to assemble, configure, and safely fly a PX4-based vehicle. Interested in contributing? Check out the [Development](broken-reference) section.

### [#](broken-reference) How Do I Get Started? <a href="#how-do-i-get-started" id="how-do-i-get-started"></a>

[Getting Started](.gitbook/assets/getting\_started) should be read by all users! It provides an overview of PX4, including features provided by the flight stack (flight modes and safety features) and the supported hardware (flight controller, vehicles, airframes, telemetry systems, RC control systems).

Depending on what you want to achieve, the following tips will help you navigate through this guide:

**I already have a drone and I just want to fly:**

If you have a Ready To Fly (RTF) vehicle that supports PX4:

* [Basic Configuration](.gitbook/assets/config) explains how to update your firmware to the latest version, calibrate the main sensors (compass, gyro/IMU, airspeed etc.), and setup your remote control and safety features.
* [Flying](.gitbook/assets/flying) teaches flight essentials, including where and how to fly safely, and how to debug arming and flight issues. It also provides detailed information about flight modes.

**I want to build a drone with PX4 from scratch:**

TIP

The "supported" vehicles are listed in the [Airframes Reference](broken-reference). These are vehicles that have tested and tuned configurations that you can download using _QGroundControl_.

If you want to build a vehicle from scratch:

* Choose a frame - [Airframe Builds](.gitbook/assets/airframes) lists the supported frames and provides detailed instructions for how to construct a subset of vehicles.
* Choose a flight controller - see [Getting Started > Flight Controllers](broken-reference) and [Autopilot Hardware](.gitbook/assets/flight\_controller).
* [Assembly](.gitbook/assets/assembly) explains how to wire up the important peripherals to your autopilot.
* [Basic Configuration](.gitbook/assets/config) shows how to update your firmware and configure it with settings appropriate for your airframe. This section also explains how to calibrate the main sensors (compass, gyro/IMU, airspeed etc.), and setup your remote control and safety features.

Once you are ready to fly your vehicle, visit the [Flying](.gitbook/assets/flying) section.

**I want to add payload or a camera:**

The payloads section describes how to add a camera or how to configure PX4 to enable you to deliver packages.

* [Payloads](.gitbook/assets/payloads) describes how to integrate payloads

**I am modifying a supported vehicle:**

Modifications of the flight controller and basic sensors are covered above. In order to use new sensors, or if you have made changes that significantly affect flight characteristics:

* [Peripheral Hardware](.gitbook/assets/peripherals) provides additional information about using external sensors.
* [Basic Configuration](.gitbook/assets/config) explains how to calibrate the main sensors.
* [Advanced Configuration](.gitbook/assets/advanced\_config) should be used to re/fine-tune the airframe.

**I want to run PX4 on new hardware and extend the platform:**

* [Development](broken-reference) explains how to support new airframes and types of vehicles, modify flight algorithms, add new modes, integrate new hardware, communicate with PX4 from outside the flight controller, and contribute to PX4.

### [#](broken-reference) Getting Help <a href="#getting-help" id="getting-help"></a>

The [Support](broken-reference) page explains how to get help from the core dev team and the wider community.

Among other things it covers:

* [Forums where you can get help](https://about/main/en/contribute/support.html#forums-and-chat)
* [Diagnosing issues](https://about/main/en/contribute/support.html#diagnosing-problems)
* [How to report bugs](https://about/main/en/contribute/support.html#issue-bug-reporting)
* [Weekly dev call](https://about/main/en/contribute/support.html#weekly-dev-call)

### [#](broken-reference) Reporting Bugs & Issues <a href="#reporting-bugs-issues" id="reporting-bugs-issues"></a>

If you have any problems using PX4 first post them on the [support forums](https://about/main/en/contribute/support.html#forums-and-chat) (as they may be caused by vehicle configuration).

If directed by the development team, code issues may be raised on [Github here (opens new window)](https://github.com/PX4/PX4-Autopilot/issues). Where possible provide [flight logs](broken-reference) and other information requested in the issue template.

### [#](broken-reference) Contributing <a href="#contributing" id="contributing"></a>

Information on how to contribute to code and documentation can be found in the [Contributing](.gitbook/assets/contribute) section:

* [Code](.gitbook/assets/contribute)
* [Documentation](broken-reference)
* [Translation](broken-reference)

### [#](broken-reference) Translations <a href="#translations" id="translations"></a>

There are several [translations](broken-reference) of this guide. You can access these from the Languages menu (top right):

### [#](broken-reference) License <a href="#license" id="license"></a>

PX4 code is free to use and modify under the terms of the permissive [BSD 3-clause license (opens new window)](https://opensource.org/licenses/BSD-3-Clause). This documentation is licensed under [CC BY 4.0 (opens new window)](https://creativecommons.org/licenses/by/4.0/). For more information see: [Licences](broken-reference).

### [#](broken-reference) Calendar & Events <a href="#calendar-events" id="calendar-events"></a>

The _Dronecode Calendar_ shows important community events for platform users and developers. Select the links below to display the calendar in your timezone (and to add it to your own calendar):

* [Switzerland – Zurich (opens new window)](https://calendar.google.com/calendar/embed?src=linuxfoundation.org\_g21tvam24m7pm7jhev01bvlqh8%40group.calendar.google.com\&ctz=Europe%2FZurich)
* [Pacific Time – Tijuana (opens new window)](https://calendar.google.com/calendar/embed?src=linuxfoundation.org\_g21tvam24m7pm7jhev01bvlqh8%40group.calendar.google.com\&ctz=America%2FTijuana)
* [Australia – Melbourne/Sydney/Hobart (opens new window)](https://calendar.google.com/calendar/embed?src=linuxfoundation.org\_g21tvam24m7pm7jhev01bvlqh8%40group.calendar.google.com\&ctz=Australia%2FSydney)

TIP

The calendar default timezone is Central European Time (CET).

#### [#](broken-reference) Icons <a href="#icons" id="icons"></a>

The following icons used in this library are licensed separately (as shown below):

&#x20;_placeholder_ icon made by [Smashicons](https://www.flaticon.com/authors/smashicons) from [www.flaticon.com](https://www.flaticon.com/) is licensed by [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/).

&#x20;_camera-automatic-mode_ icon made by [Freepik](https://www.freepik.com/) from [www.flaticon.com](https://www.flaticon.com/) is licensed by [CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/).

### [#](broken-reference) Governance <a href="#governance" id="governance"></a>

The PX4 flight stack is hosted under the governance of the [Dronecode Project (opens new window)](https://www.dronecode.org/).

[![Dronecode Logo](https://mavlink.io/assets/site/logo\_dronecode.png)](https://www.dronecode.org/) [![Linux Foundation Logo](https://mavlink.io/assets/site/logo\_linux\_foundation.png)](https://www.linuxfoundation.org/projects)

Last Updated: 7/27/2023, 10:38:31 PM
