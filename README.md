# scoutrobot

We have successfully implemented the autonomous navigation of UAV with our custom python node using LiDAR ; 
2D mapping with Hector SLAM and 3D mapping using Octomap algorithms in the ROS simulation environment. 
We also implemented an algorithm to manage the battery life of the UAV though which the UAV can use to return
home when the battery-level drops down to a certain percentage.
We added a takeoff and lad override to the ROS teleop_twist keyboard 

This is built on the existing hector_SLAM, octomap and cvg_sim_gazebo packages 

BASIC SETUP:

Install ROS Kinectic: http://wiki.ros.org/kinetic/Installation

Install Gazebo: sudo apt-get install ros-kinetic-gazebo-ros-pkgs ros-kinetic-gazebo-ros-control

Install all octomap dependencies: sudo apt-get install ros-kinetic-octomap*

Clone this scoutrobot repository which already contains the cvg_sim_gazebo, hector_mapping and octomap_mapping

Edit mapping_default.launch in hector_mapping package to suit your project

Edit octomap_mapping.launch in octomap_server package also

cd to scoutrobot_ws

Run catkin_make

Run source devel/setup.bash

LAUNCH COMMAND:

SOURCE CATKIN WORKSPACE:
cd catkin_ws
source devel/setup.bash 

GAZEBO and RVIZ:
roslaunch cvg_sim_gazebo scoutrobot_world2.launch (it launches octomap so you don't need to launch it separately)

roslaunch hector_mapping mapping_default.launch (it rviz octomap so you don't need to launch it separately)

CONTROL NODE:
rosrun scoutrobot_control nav2Original_command.py

KEYBOARD:
rosrun teleop_twist_keyboard teleop_twist_keyboard_custom.py

OCTOMAP (optional)
roslaunch octomap_server octomap_mapping.launch


Packages:
 
•	Ardrone_simulator_gazebo7: This is an open source ROS package used as a base library for the ScoutRobot simulation.  It contains Gazebo object and sensor models, quadrotor models, test fly world and launch files for each objects and empty environments.

•	Scoutrobot_control: This package contains the pyhon ROS node that implements the ScoutRobot Algorithm. It is the control center for the ScoutRobot.

•	Teleop_twist_keyboard: Generic keyboard control package for ROS. This has been modified with some custom commands to suit the objectives of the project

•	hector_slam: Another open source metapackage that contains nodes for implementing algorithm for performing SLAM by translating continuous laser scans to 2D maps.It learns the map of the environment and simultaneously estimates the UAV pose at laser scanner frame rate.

•	Octomap_mapping: a package for implementing 3D occupancy grid from pointcloud generated by the depth camera (kinect sensor) on the UAV. It is an open source package that has been modified to work with other ScoutRobot packages
