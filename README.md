# Staubli RX160
<h1 style="border:none"> STAUBLI RX160 ROS Manipulation Package - Industrial robot for homework 2 - ESPOL</h1>
&copy; 2022, Javier Pagalo

<hr>

## 1. How to Install

### 1.1. System Requirements

This package is written an tested on **Ubuntu 20.04 + ROS Noetic** and **Ubuntu 18 + ROS Melodic** environment. Dependencies are also for this environment.

### 1.2. Dependencies Prerequisites

There are a number of dependencies in this package, since the ABB robot is operated by ROS-Industrial package. Please install all the packages listed below in your Ubuntu PC, in the given order. These packages can be installed by `apt` package manager.

* [ros-industrial-core](https://github.com/ros-industrial/industrial_core.git)
* ros-<ros_distro>-moveit
* ros-<ros_distro>-joint-state-publisheser-gui
* ros-<ros_distro>-joint-trajectory-controller

The following packages are also neccesary but you must install it by cloning from the github repository and building your workspace.

* [ros-staubli](https://github.com/ros-industrial/staubli.git)


To use grippers with this robot. You need clone:

1. The gripper package https://github.com/fryumbla/Robotiq-grippers.git, you have to put the inertias in every link before running Gazebo.
   ```
        <inertial>
            <mass value="0.1" />
            <origin xyz="0 0 0" rpy="0 0 0" />
            <inertia ixx="0.03" iyy="0.03" izz="0.03" ixy="0.0" ixz="0.0" iyz="0.0" />
        </inertial>
   ```
2. The gripper gazebo plugins compilation https://github.com/javierpagalo/Gazebo_utils.git

Now, Extract the metapackage `RX160` into `${ros_workspace}/src`. `catkin_make` your workspace.

## 2. Structure of Packages

* **rx160_description:** This package contains the URDF and XACRO files for diferents configuration of the robot with grippers.
* **rx160_gazebo:** This package contains the communication with Gazebo simulator as well as controllers including examples and scenes.
* **rx160_master:** This pasckage contains a diferrents examples of motion and files to test the robot movement.
* **rx160_moveit:** This package contains the diferent MoveIt configuration of diferents configuration of the robot

## 3. How to Use

### 3.1 Gazebo Simulation with gripper controllers

1. Launch the robot visualization Rviz
   ```
   roslaunch rx160_gazebo rx160_gazebo.launch
   ```
#### 3.2 Moveit for motion planning

1. Launch the Moveit configuration
   ```
   roslaunch rx160_moveit move_group.launch
   ```

2. Launch RVIZ for visualization
   ```
   roslaunch rx160_moveit moveit_rviz.launch

   ```
