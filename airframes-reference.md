# Airframes Reference

This page lists all supported airframes and types including the motor assignment and numbering. The motors in **green** rotate clockwise, the ones in **blue** counterclockwise.

**AUX** channels may not be present on some flight controllers. If present, PWM AUX channels are commonly labelled **AUX OUT**.

### [#](broken-reference) Airship <a href="#airship" id="airship"></a>

#### [#](broken-reference) Airship <a href="#airship-2" id="airship-2"></a>

| Common Outputs                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------ |
| <ul><li>Motor1: starboard thruster</li><li>Motor2: port thruster</li><li>Motor3: tail thruster</li><li>Servo1: thrust tilt</li></ul> |

| Name      |                                                                                             |
| --------- | ------------------------------------------------------------------------------------------- |
| Cloudship | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 2507</p> |

### [#](broken-reference) Autogyro <a href="#autogyro" id="autogyro"></a>

#### [#](broken-reference) Autogyro <a href="#autogyro-2" id="autogyro-2"></a>

| Common Outputs                                                                               |
| -------------------------------------------------------------------------------------------- |
| <ul><li>Motor1: throttle</li><li>Servo1: rotor_head_L</li><li>Servo2: rotor_head_R</li></ul> |

| Name                                                                   |                                                                                                                                                                                                                                                                               |
| ---------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ThunderFly Auto-G2](https://github.com/ThunderFly-aerospace/Auto-G2/) | <p>Maintainer: ThunderFly s.r.o., Roman Dvorak &#x3C;dvorakroman@thunderfly.cz></p><p><code>SYS_AUTOSTART</code> = 17002</p><p>Specific Outputs:</p><ul><li>Servo3: elevator</li><li>Servo4: rudder</li><li>Servo5: rudder (second, optional)</li><li>Servo6: wheel</li></ul> |
| [ThunderFly TF-G2](https://github.com/ThunderFly-aerospace/TF-G2/)     | <p>Maintainer: ThunderFly s.r.o., Roman Dvorak &#x3C;dvorakroman@thunderfly.cz></p><p><code>SYS_AUTOSTART</code> = 17003</p><p>Specific Outputs:</p><ul><li>Servo3: rudder</li></ul>                                                                                          |

### [#](broken-reference) Balloon <a href="#balloon" id="balloon"></a>

#### [#](broken-reference) Balloon <a href="#balloon-2" id="balloon-2"></a>

### [#](broken-reference) Copter <a href="#copter" id="copter"></a>

#### [#](broken-reference) Dodecarotor cox <a href="#dodecarotor-cox" id="dodecarotor-cox"></a>

| Name                             |                                                                                                       |
| -------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Generic Dodecarotor cox geometry | <p>Maintainer: William Peale &#x3C;develop707@gmail.com></p><p><code>SYS_AUTOSTART</code> = 24001</p> |

#### [#](broken-reference) Helicopter <a href="#helicopter" id="helicopter"></a>

| Name                          |                                                                                              |
| ----------------------------- | -------------------------------------------------------------------------------------------- |
| Generic Helicopter (Tail ESC) | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 16001</p> |

#### [#](broken-reference) Hexarotor + <a href="#hexarotor" id="hexarotor"></a>

| Name                         |                                                                                              |
| ---------------------------- | -------------------------------------------------------------------------------------------- |
| Generic Hexarotor + geometry | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 7001</p> |

#### [#](broken-reference) Hexarotor Coaxial <a href="#hexarotor-coaxial" id="hexarotor-coaxial"></a>

| Common Outputs                                                                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Motor1: front right top, CW; angle:60; direction:CW</li><li>Motor2: front right bottom, CCW; angle:60; direction:CCW</li><li>Motor3: back top, CW; angle:180; direction:CW</li><li>Motor4: back bottom, CCW; angle:180; direction:CCW</li><li>Motor5: front left top, CW; angle:-60; direction:CW</li><li>Motor6: front left bottom, CCW;angle:-60; direction:CCW</li></ul> |

| Name                               |                                                                                               |
| ---------------------------------- | --------------------------------------------------------------------------------------------- |
| Generic Hexarotor coaxial geometry | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 11001</p> |

#### [#](broken-reference) Hexarotor x <a href="#hexarotor-x" id="hexarotor-x"></a>

| Name                         |                                                                                              |
| ---------------------------- | -------------------------------------------------------------------------------------------- |
| Generic Hexarotor x geometry | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 6001</p> |
| UVify Draco-R                | <p>Maintainer: Hyon Lim &#x3C;lim@uvify.com></p><p><code>SYS_AUTOSTART</code> = 6002</p>     |

#### [#](broken-reference) Octorotor + <a href="#octorotor" id="octorotor"></a>

| Name                          |                                                                                              |
| ----------------------------- | -------------------------------------------------------------------------------------------- |
| Generic Octocopter + geometry | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 9001</p> |

#### [#](broken-reference) Octorotor Coaxial <a href="#octorotor-coaxial" id="octorotor-coaxial"></a>

| Common Outputs                                                                                                                                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Motor1: motor 1</li><li>Motor2: motor 2</li><li>Motor3: motor 3</li><li>Motor4: motor 4</li><li>Motor5: motor 5</li><li>Motor6: motor 6</li><li>Motor7: motor 7</li><li>Motor8: motor 8</li></ul> |

| Name                              |                                                                                               |
| --------------------------------- | --------------------------------------------------------------------------------------------- |
| Generic 10" Octo coaxial geometry | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 12001</p> |

#### [#](broken-reference) Octorotor x <a href="#octorotor-x" id="octorotor-x"></a>

| Name                          |                                                                                              |
| ----------------------------- | -------------------------------------------------------------------------------------------- |
| Generic Octocopter X geometry | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 8001</p> |

#### [#](broken-reference) Quadrotor + <a href="#quadrotor" id="quadrotor"></a>

| Name                        |                                                                                              |
| --------------------------- | -------------------------------------------------------------------------------------------- |
| Generic 10" Quad + geometry | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 5001</p> |

#### [#](broken-reference) Quadrotor H <a href="#quadrotor-h" id="quadrotor-h"></a>

| Name                               |                                                                                                 |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| Reaper 500 Quad                    | <p>Maintainer: Blankered</p><p><code>SYS_AUTOSTART</code> = 4040</p>                            |
| BetaFPV Beta75X 2S Brushless Whoop | <p>Maintainer: Beat Kueng &#x3C;beat-kueng@gmx.net></p><p><code>SYS_AUTOSTART</code> = 4041</p> |

#### [#](broken-reference) Quadrotor x <a href="#quadrotor-x" id="quadrotor-x"></a>

| Name                                                                                                   |                                                                                                        |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| Generic Quadcopter                                                                                     | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 4001</p>           |
| S500 Generic                                                                                           | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 4014</p>           |
| Holybro S500                                                                                           | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 4015</p>           |
| PX4 Vision Dev Kit v1                                                                                  | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 4016</p>            |
| NXP HoverGames                                                                                         | <p>Maintainer: Iain Galloway &#x3C;iain.galloway@nxp.com></p><p><code>SYS_AUTOSTART</code> = 4017</p>  |
| Holybro X500 V2                                                                                        | <p>Maintainer: Farhang Naderi &#x3C;farhang.nba@gmail.com></p><p><code>SYS_AUTOSTART</code> = 4019</p> |
| PX4 Vision Dev Kit v1.5                                                                                | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 4020</p>            |
| Generic 250 Racer                                                                                      | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 4050</p>           |
| [HolyBro QAV250](https://docs.px4.io/main/en/frames\_multicopter/holybro\_qav250\_pixhawk4\_mini.html) | <p>Maintainer: Beat Kueng &#x3C;beat-kueng@gmx.net></p><p><code>SYS_AUTOSTART</code> = 4052</p>        |
| Holybro Kopis 2                                                                                        | <p>Maintainer: Beat Kueng &#x3C;beat@px4.io></p><p><code>SYS_AUTOSTART</code> = 4053</p>               |
| Advanced Technology Labs (ATL) Mantis EDU                                                              | `SYS_AUTOSTART` = 4061                                                                                 |
| UVify IFO                                                                                              | <p>Maintainer: Hyon Lim &#x3C;lim@uvify.com></p><p><code>SYS_AUTOSTART</code> = 4071</p>               |
| UVify IFO                                                                                              | <p>Maintainer: Hyon Lim &#x3C;lim@uvify.com></p><p><code>SYS_AUTOSTART</code> = 4073</p>               |
| COEX Clover 4                                                                                          | <p>Maintainer: Oleg Kalachev &#x3C;okalachev@gmail.com></p><p><code>SYS_AUTOSTART</code> = 4500</p>    |
| Crazyflie 2                                                                                            | <p>Maintainer: Dennis Shtatov &#x3C;densht@gmail.com></p><p><code>SYS_AUTOSTART</code> = 4900</p>      |
| Crazyflie 2.1                                                                                          | <p>Maintainer: Dennis Shtatov &#x3C;densht@gmail.com></p><p><code>SYS_AUTOSTART</code> = 4901</p>      |

#### [#](broken-reference) Simulation <a href="#simulation" id="simulation"></a>

| Name             |                                                                                                              |
| ---------------- | ------------------------------------------------------------------------------------------------------------ |
| HIL Quadcopter X | <p>Maintainer: Lorenz Meier &#x3C;lorenz@px4.io></p><p><code>SYS_AUTOSTART</code> = 1001</p>                 |
| SIH Quadcopter X | <p>Maintainer: Romain Chiappinelli &#x3C;romain.chiap@gmail.com></p><p><code>SYS_AUTOSTART</code> = 1100</p> |

#### [#](broken-reference) Tricopter Y+ <a href="#tricopter-y" id="tricopter-y"></a>

| Common Outputs                                                                                              |
| ----------------------------------------------------------------------------------------------------------- |
| <ul><li>Motor1: motor 1</li><li>Motor2: motor 2</li><li>Motor3: motor 3</li><li>Servo1: yaw servo</li></ul> |

| Name                         |                                                                                              |
| ---------------------------- | -------------------------------------------------------------------------------------------- |
| Generic Multirotor with tilt | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 14001</p> |

### [#](broken-reference) Plane <a href="#plane" id="plane"></a>

#### [#](broken-reference) Flying Wing <a href="#flying-wing" id="flying-wing"></a>

| Name                |                                                                                             |
| ------------------- | ------------------------------------------------------------------------------------------- |
| Generic Flying Wing | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 3000</p> |

#### [#](broken-reference) Plane A-Tail <a href="#plane-a-tail" id="plane-a-tail"></a>

| Common Outputs                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Motor1: throttle</li><li>Servo1: aileron right</li><li>Servo2: aileron left</li><li>Servo3: v-tail right</li><li>Servo4: v-tail left</li><li>Servo5: wheel</li><li>Servo6: flaps right</li><li>Servo7: flaps left</li></ul> |

| Name                          |                                                                                                         |
| ----------------------------- | ------------------------------------------------------------------------------------------------------- |
| Applied Aeronautics Albatross | <p>Maintainer: Andreas Antener &#x3C;andreas@uaventure.com></p><p><code>SYS_AUTOSTART</code> = 2106</p> |

#### [#](broken-reference) Simulation <a href="#simulation-2" id="simulation-2"></a>

| Name           |                                                                                                              |
| -------------- | ------------------------------------------------------------------------------------------------------------ |
| SIH plane AERT | <p>Maintainer: Romain Chiappinelli &#x3C;romain.chiap@gmail.com></p><p><code>SYS_AUTOSTART</code> = 1101</p> |

#### [#](broken-reference) Standard Plane <a href="#standard-plane" id="standard-plane"></a>

| Name                   |                                                                                             |
| ---------------------- | ------------------------------------------------------------------------------------------- |
| Generic Standard Plane | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 2100</p> |

### [#](broken-reference) Rover <a href="#rover" id="rover"></a>

#### [#](broken-reference) Rover <a href="#rover-2" id="rover-2"></a>

| Name                                                    |                                                                                                                                                                                |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Generic Ground Vehicle (Ackermann)                      | <p><code>SYS_AUTOSTART</code> = 50000</p><p>Specific Outputs:</p><ul><li>Motor1: throttle</li><li>Servo1: steering</li></ul>                                                   |
| [Aion Robotics R1 UGV](https://www.aionrobotics.com/r1) | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 50003</p>                                                                                   |
| NXP Cup car: DF Robot GPX                               | <p>Maintainer: Katrin Moritz</p><p><code>SYS_AUTOSTART</code> = 50004</p><p>Specific Outputs:</p><ul><li>Motor1: Speed of left wheels</li><li>Servo1: Steering servo</li></ul> |

### [#](broken-reference) Underwater Robot <a href="#underwater-robot" id="underwater-robot"></a>

#### [#](broken-reference) Underwater Robot <a href="#underwater-robot-2" id="underwater-robot-2"></a>

| Name                                          |                                                                                                          |
| --------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Generic Underwater Robot                      | `SYS_AUTOSTART` = 60000                                                                                  |
| HippoCampus UUV (Unmanned Underwater Vehicle) | <p>Maintainer: Daniel Duecker &#x3C;daniel.duecker@tuhh.de></p><p><code>SYS_AUTOSTART</code> = 60001</p> |

#### [#](broken-reference) Vectored 6 DOF UUV <a href="#vectored-6-dof-uuv" id="vectored-6-dof-uuv"></a>

| Common Outputs                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Motor1: motor 1 CCW, bow starboard horizontal, , propeller CCW</li><li>Motor2: motor 2 CCW, bow port horizontal, propeller CCW</li><li>Motor3: motor 3 CCW, stern starboard horizontal, propeller CW</li><li>Motor4: motor 4 CCW, stern port horizontal, propeller CW</li><li>Motor5: motor 5 CCW, bow starboard vertical, propeller CCW</li><li>Motor6: motor 6 CCW, bow port vertical, propeller CW</li><li>Motor7: motor 7 CCW, stern starboard vertical, propeller CW</li><li>Motor8: motor 8 CCW, stern port vertical, propeller CCW</li></ul> |

| Name                           |                                                                                                                  |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| BlueROV2 (Heavy Configuration) | <p>Maintainer: Thies Lennart Alff &#x3C;thies.lennart.alff@tuhh.de></p><p><code>SYS_AUTOSTART</code> = 60002</p> |

### [#](broken-reference) VTOL <a href="#vtol" id="vtol"></a>

#### [#](broken-reference) Simulation <a href="#simulation-3" id="simulation-3"></a>

| Common Outputs                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Motor1: motor right</li><li>Motor2: motor left</li><li>Servo1: elevon right</li><li>Servo2: elevon left</li></ul> |

| Name               |                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------ |
| SIH Tailsitter Duo | <p>Maintainer: Romain Chiappinelli &#x3C;romain.chiap@gmail.com></p><p><code>SYS_AUTOSTART</code> = 1102</p> |

#### [#](broken-reference) Standard VTOL <a href="#standard-vtol" id="standard-vtol"></a>

| Name                            |                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| HIL Standard VTOL QuadPlane     | <p>Maintainer: Roman Bapst &#x3C;roman@auterion.com></p><p><code>SYS_AUTOSTART</code> = 1002</p>                                                                                                                                                                                                                                                                    |
| Generic Standard VTOL           | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 13000</p>                                                                                                                                                                                                                                                                        |
| Vertical Technologies DeltaQuad | <p>Maintainer: Sander Smeets &#x3C;sander@droneslab.com></p><p><code>SYS_AUTOSTART</code> = 13013</p><p>Specific Outputs:</p><ul><li>Motor1: motor 1</li><li>Motor2: motor 2</li><li>Motor3: motor 3</li><li>Motor4: motor 4</li><li>Servo1: Right elevon</li><li>Servo2: Left elevon</li><li>Servo3: Pusher motor</li><li>Servo4: Pusher reverse channel</li></ul> |
| BabyShark VTOL                  | <p>Maintainer: Silvan Fuhrer &#x3C;silvan@auterion.com></p><p><code>SYS_AUTOSTART</code> = 13014</p><p>Specific Outputs:</p><ul><li>Motor1: motor 1</li><li>Motor2: motor 2</li><li>Motor3: motor 3</li><li>Motor4: motor 4</li><li>Motor5: Pusher motor</li><li>Servo1: Ailerons</li><li>Servo2: A-tail left</li><li>Servo3: A-tail right</li></ul>                |

#### [#](broken-reference) VTOL Tailsitter <a href="#vtol-tailsitter" id="vtol-tailsitter"></a>

| Name                    |                                                                                              |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| Generic VTOL Tailsitter | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 13200</p> |

#### [#](broken-reference) VTOL Tiltrotor <a href="#vtol-tiltrotor" id="vtol-tiltrotor"></a>

| Name                             |                                                                                              |
| -------------------------------- | -------------------------------------------------------------------------------------------- |
| Generic Quadplane VTOL Tiltrotor | `SYS_AUTOSTART` = 13030                                                                      |
| Generic Tiltrotor VTOL           | <p>Maintainer: John Doe &#x3C;john@example.com></p><p><code>SYS_AUTOSTART</code> = 13100</p> |

Last Updated: 11/22/2022, 5:10:17 PM
