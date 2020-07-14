---
title: "Gazebo"
linkTitle: "Gazebo"
weight: 1
---

{{% pageinfo %}}
To be included : Definition of key terms, Intro to URDF and SDF, Intro to Gazebo Plugins, Basic Gazebo Tutorials, Intro to Gazebo Sensors and Actuators, Make your own robot(basic)
{{% /pageinfo %}}


Gazebo is the most popular simulator for robotics development. It can simulate robots in a
3D environment and can be fully integrated into ROS integrated with Gazebo using the
**gazebo_ros** ROS package. You can interface your robots in the simulation using ROS
and control them using ROS messages and services.

## 2.1 Installation

Gazebo is automatically installed when you install ROS. To make sure you have all the
ROS packages necessary for running Gazebo simulations are installed

`sudo apt-get install ros-melodic-gazebo-*`

## 2.2 Getting Started

You can launch the Gazebo GUI simulator window by just running the command gazebo
in the terminal. You can follow **[this](http://gazebosim.org/tutorials?tut=model_editor&cat=model_editor_top)** tutorial to get used to the gazebo GUI and make some
models.

## 2.3 Integration with ROS

Gazebo has tight integration with ROS to make simulation as convenient as possible.
For example you can publish a velocity to the **cmd_ve**l topic and this can cause a robot
in Gazebo to move.


