# Quickstart

## PC set up

First you will need is Ubuntu 16.04 on your desktop PC or laptop PC
Download: https://ubuntu.com/download/alternative-downloads

After you install Ubuntu 16.04 you will need to install ROS
Run the following command in terminal window
$ sudo apt-get update
$ sudo apt-get upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh && chmod 755 ./install_ros_kinetic.sh && bash ./install_ros_kinetic.sh

Install dependent ROS packages.
$ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers
$ cd ~/catkin_ws/src/
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ cd ~/catkin_ws && catkin_make

In bashrc you will need to write your PC IP adress and port.
export ROS_MASTER_URI=http://192.168.0.100:11311
export ROS_HOSTNAME=192.168.0.100
Than run this command in terminal: source ~/.bashrc

And your PC set up for work.

## Raspberry Pi set up

You will need to install OS on Raspberry Pi.Its recommended to install one of the following 3:
- Ubuntu MATE
- Raspbian
- webOS Robotics Platform

How to install them follow the steps on given link.
Link for Ubuntu MATE: http://emanual.robotis.com/docs/en/platform/turtlebot3/raspberry_pi_3_setup/#install-linux-ubuntu-mate
Link for Raspbian: http://emanual.robotis.com/docs/en/platform/turtlebot3/raspberry_pi_3_setup/#install-linux-based-on-raspbian
Link for webOS Robotics Platform: https://github.com/ros/meta-ros/wiki/OpenEmbedded-Build-Instructions

After you install your OS on Raspberry Pi you will need to install ROS.
$ sudo apt-get update
$ sudo apt-get upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh && chmod 755 ./install_ros_kinetic.sh && bash ./install_ros_kinetic.sh

Install dependent packages:
$ cd ~/catkin_ws/src
$ git clone https://github.com/ROBOTIS-GIT/hls_lfcd_lds_driver.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ cd ~/catkin_ws/src/turtlebot3
$ sudo rm -r turtlebot3_description/ turtlebot3_teleop/ turtlebot3_navigation/ turtlebot3_slam/ turtlebot3_example/
$ sudo apt-get install ros-kinetic-rosserial-python ros-kinetic-tf
$ cd ~/catkin_ws && catkin_make

In bashrc you need to configure IP adresses for your turtlebot and server ip adress.
- export ROS_MASTER URI=http://192.168.0.100:11311 (IP adress from your PC)
- export ROS_HOSTNAME= 192.168.0.200 (IP adress from your turtlebot)

Your Raspberry Pi is set up for work

## Hardware setu up
You will need to buy your own TurtleBot and Assembl him.
Link: http://emanual.robotis.com/docs/en/platform/turtlebot3/hardware_setup/#hardware-setup

Any other kinds of tutorials or information you can find on link below.
http://emanual.robotis.com/docs/en/platform/turtlebot3/getting_started/
