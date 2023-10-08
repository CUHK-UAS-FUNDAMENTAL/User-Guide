# An open-source SLAM integration package

An open-source SLAM integration package for [_CUHK UAS fundamental group_](http://www.mae.cuhk.edu.hk/\~usr/)

## Menu

* [open-source-SLAM-package](broken-reference)
  * [Menu](broken-reference)
  * [1. Introduction](broken-reference)
  * [2. Overall Architecture](broken-reference)
  * [3. Summary Table](broken-reference)
  * [4. Setup Guide](broken-reference)
    * [4.1 Dependency](broken-reference)
      * [4.1.1 General Dependency](broken-reference)
      * [4.1.2 A-LOAM & F-LOAM](broken-reference)
      * [4.1.3 LIO-SAM](broken-reference)
      * [4.1.4 Fast-LIO2](broken-reference)
      * [4.1.5 VINS-Fusion](broken-reference)
    * [4.2 Compilation](broken-reference)
      * [4.2.1 download A-LOAM and build it](broken-reference)
      * [4.2.2 download F-LOAM and build it](broken-reference)
      * [4.2.3 download LIO-SAM and build it](broken-reference)
      * [4.2.4 download Fast-LIO and build it](broken-reference)
      * [4.2.5 download VINS-Fusion and build it](broken-reference)
  * [5. Quick Test](broken-reference)
    * [5.1 Test with PX4 Fundamental Simulator](broken-reference)
  * [6. Updates](broken-reference)
  * [7. TODO](broken-reference)
  * [8. Q&\&A](broken-reference)
  * [9. Related Works](broken-reference)
  * [10. Related Publications](broken-reference)

[_Table of contents generated with markdown-toc_](http://ecotrust-canada.github.io/markdown-toc/)

## 1. Introduction

![image](https://user-images.githubusercontent.com/58619142/182330364-2e35f0b0-6fae-4314-a9b9-2444ce8b64a7.png)

This package presents a set of state-of-art open-sourced lidar-based Simultaneous Localization and Mapping(SLAM) software for UAV localization in a 3D factory environment, targeting:

* Lightweight(both hardware and software);
* Robust;
* High precision;
* integration with other algorithms(navigation, task planning, and so on).

Up to now, we have collected and tested four kinds of lidar SLAM, including pure lidar SLAM algorithms and lidar-inertial SLAM algorithms. Integration of autonomous UAV software and the development of a low-cost SLAM algorithm will be our future work directions.

## 2. Overall Architecture

![Autonomous UAV system overview](https://user-images.githubusercontent.com/58619142/182335315-06c7d47d-3a23-47c4-83db-734fab28334e.png)\
Figure 1: Autonomous UAV system overview\


The SLAM module plays a role in perceiving and analyzing environment information gathered by navigation sensors. In a GPS-deny environment, Unmanned vehicles depend on the SLAM algorithm to get accurate localization information. In general, SLAM algorithms can be divided into lidar SLAM and visual SLAM. The visual SLAM algorithm is low-cost and lightweight, which benefits from camera sensors. However, visual SLAM suffers mostly from illumination variation and motion distortion. The lidar SLAM methods, by contrast, have a stable performance in a challenging environment. This is one important reason why engineers prefer lidar SLAM whether in autonomous driving or service robots.

\


In this project, we take more concern on the lidar or lidar-inertial fusion SLAM algorithm. The lidar SLAM mostly contains below sub-modules:

* Offline calibration
* Point cloud preprocessing & sensor data preprocessing
* Motion distortion compensation
* Front-end lidar odometry or lidar-inertial odometry
* Back-end optimization
* Visualization

![Lidar-inertial SLAM system pipeline](https://user-images.githubusercontent.com/58619142/181915418-cd55e434-fdb4-4f30-98fb-386c2b324990.PNG)\
Figure 2: Lidar-inertial SLAM system pipeline\


## 3. Summary Table

Here is a summary table for four lidar SLAM methods in our package. As shown in this table, there are two pure lidar SLAM methods(A-LOAM and F-LOAM) and two lidar-inertial SLAM methods(LIO-SAM and Fast-LIO2).

| SLAM method | Lidar | IMU | Front-end odometry | Back-end optimization     | Loop-closure | feature                        | Processor |
| ----------- | ----- | --- | ------------------ | ------------------------- | ------------ | ------------------------------ | --------- |
| A-LOAM      | ✔     | ✖   | Edge-planar        | ✖                         | ✖            | benchmark                      | x86       |
| F-LOAM      | ✔     | ✖   | Edge-planar        | ✖                         | ✖            | Faster than A-LOAM             | x86       |
| LIO-SAM     | ✔     | ✔   | Edge-planar        | Factor graph optimization | ✔            | Can handle aggressive rotation | x86       |
| Fast-LIO2   | ✔     | ✔   | Direct             | Iterated kalman filter    | ✖            | Lightweight                    | x86/ARM   |

Table 1: A comparison of different SLAM methods in this package\


> A-LOAM is an Advanced implementation of LOAM (J. Zhang and S. Singh. LOAM: Lidar Odometry and Mapping in Real-time), which uses Eigen and Ceres Solver to simplify code structure. This code is modified from LOAM. This code is clean and simple without complicated mathematical derivation and redundant operations. It is a good learning material for SLAM beginners.

> F-LOAM is an optimized version of A-LOAM and LOAM with the computational cost reduced by up to 3 times.

> LIO-SAM is a real-time lidar-inertial odometry package developed by [Tixiao Shan](https://github.com/TixiaoShan). The biggest feature of LIO-SAM is that it can handle aggressive rotation.

> FAST-LIO (Fast LiDAR-Inertial Odometry) is a computationally efficient and robust LiDAR-inertial odometry package. It fuses LiDAR feature points with IMU data using a tightly-coupled iterated extended Kalman filter to allow robust navigation in fast-motion, noisy or cluttered environments where degeneration occurs

## 4. Setup Guide

Before starting the test, we strongly recommend that users follow the following steps to configure the computer environment. These steps have been tested under **Ubuntu 64-bit 18.04**.

### 4.1 Dependency

#### 4.1.1 General Dependency

1. ROS ROS Melodic: [ROS Installation](http://wiki.ros.org/ROS/Installation)
2. Eigen Eigen >= 3.3.4, Follow [Eigen Installation](http://eigen.tuxfamily.org/index.php?title=Main\_Page).

#### 4.1.2 A-LOAM & F-LOAM

1. Ceres Solver Follow [Ceres Installation](http://ceres-solver.org/installation.html).
2. PCL Follow [PCL Installation](http://www.pointclouds.org/downloads/linux.html).
3. Trajectory visualization For a visualization purpose, this package uses hector trajectory sever, you may install the package by

```
sudo apt-get install ros-melodic-hector-trajectory-server
```

Alternatively, you may remove the hector trajectory server node if trajectory visualization is not needed.

#### 4.1.3 LIO-SAM

1. ROS dependency

Open a new terminal and type the following command：

```bash
sudo apt-get install -y ros-melodic-navigation
sudo apt-get install -y ros-melodic-robot-localization
sudo apt-get install -y ros-melodic-robot-state-publisher
```

2. [GTSAM](https://gtsam.org/get\_started/) (Georgia Tech Smoothing and Mapping library)

Again, type the following command:

```bash
sudo add-apt-repository ppa:borglab/gtsam-release-4.0
sudo apt install libgtsam-dev libgtsam-unstable-dev
```

#### 4.1.4 Fast-LIO2

1. livox\_ros\_driver Follow [livox\_ros\_driver Installation](https://github.com/Livox-SDK/livox\_ros\_driver).

_Remarks:_

* Since the FAST-LIO must support Livox serials LiDAR firstly, so the **livox\_ros\_driver** must be installed and **sourced** before running any FAST-LIO launch file.
* How to source? The easiest way is add the line `source $Licox_ros_driver_dir$/devel/setup.bash` to the end of file `~/.bashrc`, where `$Licox_ros_driver_dir$` is the directory of the livox ros driver workspace (should be the `ws_livox` directory if you completely followed the livox official document).

#### 4.1.5 VINS-Fusion

Follow [Ceres Installation](http://ceres-solver.org/installation.html).

### 4.2 Compilation

Firstly, you need to create a ros workspace and initial it. Open a new terminal and type the following command：

```bash
mkdir 3d_SLAM_ws && cd 3d_SLAM_ws
mkdir src && cd src
catkin_init_workspace
cd .. && catkin_make
```

#### 4.2.1 download A-LOAM and build it

Clone the repository and catkin\_make:

```bash
    cd ~/3d_SLAM_ws/src
    git clone https://github.com/CUHK-UAS-FUNDAMENTAL/A-LOAM.git -b dev_v1.0
    cd ../
    catkin_make
```

#### 4.2.2 download F-LOAM and build it

Clone the repository and catkin\_make:

```bash
    cd ~/3d_SLAM_ws/src
    git clone -b gzx_dev https://github.com/CUHK-UAS-FUNDAMENTAL/F-loam.git 
    cd ..
    catkin_make
```

#### 4.2.3 download LIO-SAM and build it

Clone the repository and catkin\_make:

```bash
 cd ~/3d_SLAM_ws/src
 git clone -b gzx_dev https://github.com/CUHK-UAS-FUNDAMENTAL/LIO_SAM.git
 cd ..
 catkin_make
```

#### 4.2.4 download Fast-LIO and build it

Clone the repository and catkin\_make:

```bash
   cd ~/3d_SLAM_ws/src
    git clone https://github.com/hku-mars/FAST_LIO.git
    cd FAST_LIO
    git submodule update --init
    cd ../..
    catkin_make
    source devel/setup.bash
```

* Remember to source the livox\_ros\_driver before build (follow 1.3 **livox\_ros\_driver**)
* If you want to use a custom build of PCL, add the following line to \~/.bashrc `export PCL_ROOT={CUSTOM_PCL_PATH}`

#### 4.2.5 download VINS-Fusion and build it

Clone the repository and catkin\_make:

```bash
 cd ~/3d_SLAM_ws/src
 git clone https://github.com/CUHK-UAS-FUNDAMENTAL/VINS-Fusion.git
 cd ..
 catkin_make
```

## 5. Quick Test

### 5.1 Test with PX4 Fundamental Simulator

The PX4 Fundamental Simulator is a UAV simulator developed by [yizhou Chen 陈奕州](https://github.com/JINXER000). If you are not familiar with this simulator, I recommend that you get to start with this [wiki](https://github.com/JINXER000/FundamentalSimulatorPX4/wiki). Now, the simulator is still under revision. More details can be seen [here](https://github.com/CUHK-UAS-FUNDAMENTAL/FundamentalSimulatorPX4/tree/xtdrone/gzx\_dev).

![simulator environment](https://user-images.githubusercontent.com/58619142/182297052-886127c5-dbb1-455f-8755-402507335062.png)

Figure 2: a factory environment in PX4 fundamental simulator

Users can remotely control a small drone to explore a simulation environment(e.g., a factory). Meanwhile, the pose of UAV and a point cloud map incrementally constructed will be output by SLAM algorithms. The program runs in the following order:

1. start the PX4 simulator

```bash
    roslaunch px4 powerplant_lidar.launch
```

2. run the control python file

```bash
cd ~/${usr_path_to_XTDrone}/XTDrone/control/keyboard/
python multirotor_keyboard_control.py iris 1 vel
```

3. run the communication python file

```bash
cd ~/${usr_path_to_XTDrone}/XTDrone/communication/
python multirotor_communication.py iris 0
```

4. run lidar SLAM algorithm

* A-LOAM

```bash
  cd ~/3d_SLAM_ws
 source ~/3d_SLAM_ws/devel/setup.bash
 roslaunch aloam_velodyne aloam_velodyne_VLP_16.launch
```

* F-LOAM

```bash
  cd ~/3d_SLAM_ws
 source ~/3d_SLAM_ws/devel/setup.bash
 roslaunch floam floam_gazebo.launch
```

* LIO-SAM

```bash
  cd ~/3d_SLAM_ws
 source ~/3d_SLAM_ws/devel/setup.bash
roslaunch lio_sam run.launch
```

* Fast-LIO

```bash
    cd ~/3d_SLAM_ws
    source ~/3d_SLAM_ws/devel/setup.bash
    roslaunch fast_lio mapping_velodyne.launch
```

* VINS-Fusion

```bash
    cd ~/3d_SLAM_ws
    source ~/3d_SLAM_ws/devel/setup.bash
    rosrun vins vins_node ~/3d_SLAM_ws/src/VINS-Fusion/config/xtdrone_sitl/px4_sitl_stereo_imu_config.yaml &
    roslaunch vins vins_rviz.launch
```

## 6. Updates

2022-08-02 update the readme file.

## 7. TODO

## 8. Q&\&A

## 9. Related Works

* A-LOAM

[A-LOAM: Advanced implementation of LOAM](https://github.com/HKUST-Aerial-Robotics/A-LOAM)

* F-LOAM

[F-LOAM: Fast LiDAR Odometry and Mapping](https://github.com/wh200720041/floam)

* LIO-SAM

[LIO-SAM: Tightly-coupled Lidar Inertial Odometry via Smoothing and Mapping](https://github.com/TixiaoShan/LIO-SAM)

* Fast-LIO

[ikd-Tree: An Incremental K-D Tree for robotic applications](https://arxiv.org/abs/2102.10808)

[Robust Real-time LiDAR-inertial Initialization](https://github.com/hku-mars/LiDAR\_IMU\_Init)

[IKFoM: Iterated Kalman Filters on Manifolds](https://github.com/hku-mars/IKFoM)

[FAST-LIO2: Fast Direct LiDAR-inertial Odometry](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9697912)

[FAST-LIO: A Fast, Robust LiDAR-inertial Odometry Package by Tightly-Coupled Iterated Kalman Filter](https://arxiv.org/abs/2010.08196)

* VINS-Fusion

[VINS-Mono: A Robust And Versatile Monocular Visual-Inertial State Estimator](https://arxiv.org/abs/1708.03852)

## 10. Related Publications

1. Zhang J, Singh S. LOAM: Lidar odometry and mapping in real-time\[C]//Robotics: Science and Systems. 2014, 2(9): 1-9.
2. Wang H, Wang C, Chen C L, et al. F-loam: Fast lidar odometry and mapping\[C]//2021 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS). IEEE, 2021: 4390-4396.
3. Shan T, Englot B, Meyers D, et al. Lio-sam: Tightly-coupled lidar inertial odometry via smoothing and mapping\[C]//2020 IEEE/RSJ international conference on intelligent robots and systems (IROS). IEEE, 2020: 5135-5142.
4. Xu W, Cai Y, He D, et al. Fast-lio2: Fast direct lidar-inertial odometry\[J]. IEEE Transactions on Robotics, 2022.
5. Qin T, Li P, Shen S. Vins-mono: A robust and versatile monocular visual-inertial state estimator. IEEE Transactions on Robotics. 2018 Jul 27;34(4):1004-20.
