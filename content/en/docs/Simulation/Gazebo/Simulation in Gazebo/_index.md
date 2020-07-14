---
title: "Simulation in Gazebo"
linkTitle: "Simulation in Gazebo"
weight: 1
---

{{% pageinfo %}}
This section contains tutorials focused on simulating the following robots in Gazebo : Turtlebot3, Husky, Jackal, PR2, RotorS, MavROS(IRIS)
{{% /pageinfo %}}

## 1. Turtlebot

Turtlebot is a differential drive robot which is completely open source. This means everything from its design to its code is available online. You can read more about turtlebot [**here**](https://www.turtlebot.com/). The latest version of turtlebot is Turtlebot 3 and comes in 3 variants :
**Turtlebot3 Burger**, **Turtlebot3 Waffle** and **Turtlebot3 Waffle Pi**.

### 1.1 Installation of Turtlebot

Use the command :

`sudo apt install ros-melodic-turtlebot3-*`

To install the basic packages. After installation, make sure to add the following to your `~/.bashrc` file:

`export TURTLEBOT3_MODEL=burger`

This defines which model of turtlebot to use for simulation. You can use **waffle** or **waffle_pi** instead of **burger**.

A brief description of some these packages which are very frequently used are given below:  

● **turtlebot3_bringup** : Used to launch actual turtlebot. Not used in simulations  

● **turtlebot3_gazebo** : Contains all the files necessary for simulating the turtlebot in Gazebo  

● **turtlebot3_msgs** : Contains all the message and service definitions used by the turtlebot  

● **turtlebot3_description** : Provides complete 3D model of turtlebot, different environments (worlds) for simulation and visualisation. You can see all the urdf files in the urdf folder of this package  

● **turtlebot3_teleop** : Provides launch files and nodes for **teleoperation** of turtlebot using different input devices (like keyboard, joysticks and even video game controllers!)  

● **turtlebot3_navigation** : Contains the roslaunch scripts for starting **autonomous navigation**  

● **turtlebot3_slam** : Contains the roslaunch scripts for starting **SLAM** (Simultaneous Localization and Mapping) in turtlebot

### 1.2 Controlling turtlebot inside Gazebo

The best way to see turtlebot in action is to use teleop - a ROS node which lets you publish to cmd_vel using your keyboard. For this you will need to run the following commands in separate terminal windows:

1.`roslaunch turtlebot3_gazebo turtlebot3_world.launch`  
2.`roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`  

The first command launches gazebo and spawns Turtlebot3 in a field of obstacles. The second runs the teleop node which lets you drive turtlebot using arrow keys. Check out
this **[link](http://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/#turtlebot3-simulation-using-gazebo)** for more.

Let's examine the ROS topics initialised by these commands. Open another terminal
window and run

`rostopic list`

This will list out all of the active topics. Among them you should see cmd_vel. To see
more information about it, run

`rostopic info cmd_vel`

You should see the message type for the topic being Twist as well as who is
publishing and subscribing to the topic. To see the message being published, you can
run -

`rostopic echo cmd_vel`

This will print out the message continuously into the terminal. To get more info on the
message type Twist you can run -

`rosmsg info Twist`

This will tell you that Twist is part of `geometry_msgs` (an inbuilt set of message types
you can learn about [**here**](http://wiki.ros.org/geometry_msgs)) as well as its structure.

All four of the above commands come in very handy when getting to know a new
system of ROS nodes or even debugging your own, so do get familiarized with them.
You can learn more about them in the last section of **Chapter 20** in Morgan Quigley.
While we examined the `cmd_vel` topic, you can go ahead and try it on any of the topics
you see with `rostopic list`

From the above exploration we saw that the `turtlebot3_teleop_keyboard` node
publishes a message of type Twist on the topic `cmd_vel`. This topic is subscribed to
by the gazebo node which moves the turtlebot inside the simulator accordingly. If you
are unsure about any of the terms we just used, you should go over the ROS basics
document again.

The two main topics you will be using for interacting with turtle bot are cmd_vel and
odom

### 1.2.2 cmd_vel

All you have to do to make the turtlebot move in the simulator is write a node that
publishes appropriate `Twist` messages on `cmd_vel`. For a tutorial, check out this
**[video](https://www.youtube.com/watch?v=yEwi1__NJrE)** (Note that they use an online ROS development environment but you can do the
same thing on any platform)

### 1.2.3 odom

To get the location of turtlebot in the environment you will be using odom. Again, to see
more information about the topic, run - 

`rostopic info /odom`

You will see that odom carries a message of type **Odometry** which is part of the
`nav_msgs` package. Like `geometry_msgs` this is also a set of messages. You can learn
more about it **[here](http://wiki.ros.org/nav_msgs)**. You can explore Odometry using `rosmsgs info`
