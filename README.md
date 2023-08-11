# SOFOR_OBJECTING_FOLLOWING_ROBOT_ROS
This is the final Assignment of the our course Software Architectures for Robotics (SofAR) in which we are asked to build a simulation with ROS in which a robot follows a moving target (e.g., a person or another robot) at a fixed distance.

## Two ways to impliment this 
* Using nav2 (ROS 2)
* Using OpenCV (ROS)

  ## nav2
Intially installed the Nav2 pkg  which is used in ROS2 for the navigation of robots in the environment. We used spacific part of the nav2 to the simulation to implement the  "following dynamic point" maintaining a fixed distance.

![14c633ce-da26-44c6-8ab1-409e551f2424](https://user-images.githubusercontent.com/105802251/211937880-61b5d775-c529-4a37-bd1c-de328b86b204.jpg)

Basiclly here we use Nav2 for a task going from point A to point B. In this case, we will use Nav2 to follow a moving object at a spacified distance, the point changes continously and updates the goal to the robot and makes it to moves in given direction.This task is useful in cases such as robot following a person (suitcase follows you as you walk) or another robot.

## INSTALLATION
first you have to install the Nav2 workspace at the following:
link https://navigation.ros.org/build_instructions/index.html. Then:
* replace the nav2_bringup and nav2_bt_navigator packages with the ones I modified inside the navigation2 package
* clone the nav2_test_utilis package inside the Nav2 workspace.

Before to build the environment with the colcon build ROS2 command, remember to modify the path for the parameter default_nav_to_pose_bt_xml inside nav2_params.yaml, that you can find in nav2_ws -> src -> navigation2 -> nav2_bringup -> bringup -> params.

To execute the project, you must execute the following commands on two different terminals:

ros2 run nav2_test_utils clicked_point_to_pose

ros2 launch nav2_bringup tb3_simulation_launch.py

## SOFTWARE ARCHITECTURE
 
![image](https://user-images.githubusercontent.com/105802251/211948878-c4479d72-d032-441b-bd5f-5768ba9b8d4b.png)

We will use the “clicked point” button on the toolbar to substitute object detections to provide goal updates to Nav2. This button allows you to publish coordinates in the topic /clicked_point. This point needs to be sent to the behavior tree, using the program clicked_point_to_pose

## TREE BEHAVIOUR
![image](https://user-images.githubusercontent.com/105802251/211949157-2d073ff7-5f9c-4979-8420-f7ae1a08e171.png)
 

 
 
# OpenCV

This project aims to make the robot follow a particular object while also keeping a minimum safe distance from it.

The software stacks implemented in this project are ROS and Python. We also made use of OpenCV for the object detection part.

We aim to further expand this project and make it a person-follower.
## Clone the Object Follower package

Now go ahead and clone this repository inside the "src" folder of the catkin workspace you just created by executing the command given below in your terminal.

https://github.com/furqan41/SOFOR_OBJECTING_FOLLOWING_ROBOT_ROS

Now launch the the file by using the following command in terminal

roslaunch bridge_example gazeebo_ex.launch

![image](https://user-images.githubusercontent.com/105802251/211953307-90abc088-8a61-4256-bba6-f46542aecd1b.png)


Here after launching the package, you will see the two windows, In one you will see two robots one(Robot_1) moves and other(Robot_2) looking for the robot_1 by using CV detecting operation when in seach the defined colour it lock it and then it will try to allign itself in center of that colour to keep detecting to follows it and in sencond window you will see the camrea view of the robot_2 to visualize the detection process. 

