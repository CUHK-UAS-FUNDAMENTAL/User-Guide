# Source Code Management

### Introduction

Source Code Management (SCM) is an integral part of the Fundamental System, which runs on the Robot Operating System (ROS). This chapter aims to outline how source code is managed, how to interact with the ROS-based codebase, and what best practices to follow.

### Code Repository and ROS

The source code for the Fundamental System is hosted on a version control platform. The project is ROS-based, meaning it follows the ROS directory structure and makes use of ROS functionalities like nodes, topics, and services.

1. **Contact CUHK-UAS-FUNDAMENTAL**: Send an email or fill out the access request form provided by CUHK-UAS-FUNDAMENTAL.
2. **Wait for Approval**: Once your request is reviewed, you will receive a notification about the status of your access request.
3. **Repository URL**: After receiving approval, you will be provided with the URL to the private repository.

#### How to Request Access

The source code for the Fundamental System is hosted on a version control platform and is currently set to private. Access is restricted and can be granted through a permit from CUHK-UAS-FUNDAMENTAL.

### ROS Directory Structure

The ROS workspace may have a structure similar to the following:

```bash
bashCopy code- /src - /core_pkg - /planning_pkg - /control_pkg - /simulation_pkg - /launch - /config - CMakeLists.txt - package.xml
```

### Code Explanation

#### ROS Packages

The `/src` directory contains various ROS packages (`_pkg`) corresponding to different components of the system.

**Core Package (`core_pkg`)**

This package houses the base functionalities, including the Pixhawk4 firmware interface.

**Planning and Control Packages (`planning_pkg`, `control_pkg`)**

These packages contain ROS nodes that implement task planning, motion planning, and control algorithms.

**Simulation Package (`simulation_pkg`)**

This package contains nodes for simulating the UAV in different environments and conditions.

#### Launch Files and Configuration

The `/launch` and `/config` directories contain ROS launch files and configuration files, respectively, to initialize nodes and set parameters.

### Contributing to the ROS Codebase

If you're interested in contributing, please consult the `CONTRIBUTING.md` file for guidelines on how to contribute code, report issues, and submit pull requests. Due to the ROS-based nature of the project, familiarity with ROS conventions and practices is recommended.
