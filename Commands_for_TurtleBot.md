# Commands for using TurtleBot

## Bringup

[Remote PC]
1. $ roscore
3. $ export TURTLEBOT3_MODEL=${TB3_MODEL}		${TB3_MODEL} = burger, waffle, waffle_pi
4. $ roslaunch turtlebot3_bringup turtlebot3_remote.launch

[TurtleBot]
2. $ roslaunch turtlebot3_bringup turtlebot3_robot.launch

To load TurtleBot on your rviz command:
- $ rosrun rviz rviz -d `rospack find turtlebot3_description`/rviz/model.rviz

## Basic Operation

To control TurtleBot you can use keyboard, PS3 Jostick, XBOX 360 Jostick, Wii Remote,...
Run Bringup.

### Keyboard

- $ export TURTLEBOT3_MODEL=%{TB3_MODEL}
- $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

### PS3 Joystick

On your Remote PC install packages for teleoperation using PS3 Joystick
- $ sudo apt-get install ros-kinetic-joy ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-joy
- $ roslaunch teleop_twist_joy teleop.launch

### XBOX 360 Joystick

On your Remote PC install packages for teleoperation using XBOX 360 Joystick
- $ sudo apt-get install xboxdrv ros-kinetic-joy ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-joy
- $ sudo xboxdrv --silent
- $ roslaunch teleop_twist_joy teleop.launch

### Wii Remote

On your Remote PC install packages for teleoperation using Wii Remote
- $ sudo apt-get install ros-kinetic-wiimote libbluetooth-dev libcwiid-dev
- $ cd ~/catkin_ws/src
- $ git clone https://github.com/ros-drivers/joystick_drivers.git  
- $ cd ~/catkin_ws && catkin_make
- $ rosrun wiimote wiimote_node
- $ rosrun wiimote teleop_wiimote


### Move using interactive markers

- $ export TURTLEBOT3_MODEL=${TB3_MODEL}
- $ roslaunch turtlebot3_bringup turtlebot3_remote.launch
- $ roslaunch turtlebot3_example interactive_markers.launch
- $ rosrun rviz rviz -d `rospack find turtlebot3_example`/rviz/turtlebot3_interactive.rviz

### Obstacle Detection

- $ roslaunch turtlebot3_example turtlebot3_obstacle.launch

### Point Operation

- $ roslaunch turtlebot3_example turtlebot3_pointop_key.launch

### Patrol

- $ rosrun turtlebot3_example turtlebot3_server
- $ roslaunch turtlebot3_example turtlebot3_client.launch

## SLAM (Simultaneous Localization and Mapping)

Run Bringup.

[Remote PC]
- $ export TURTLEBOT3_MODEL=${TB3_MODEL}
- $ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

We need to use cartographer packages.

- $ sudo apt-get install ninja-build libceres-dev libprotobuf-dev protobuf-compiler libprotoc-dev
- $ cd ~/catkin_ws/src
- $ git clone https://github.com/googlecartographer/cartographer.git
- $ git clone https://github.com/googlecartographer/cartographer_ros.git
- $ cd ~/catkin_ws
- $ src/cartographer/scripts/install_proto3.sh
- $ rm -rf protobuf/
- $ rosdep install --from-paths src --ignore-src -r -y --os=ubuntu:xenial
- $ catkin_make_isolated --install --use-ninja
- $ source ~/catkin_ws/install_isolated/setup.bash

- $ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=cartographer

After that you can run any method to move TurtleBot around and make map of a room you are using right now.

### Save map
- $ rosrun map_server map_saver -f ~/map

## Navigation

Run Bringup.

- $ export TURTLEBOT3_MODEL=${TB3_MODEL}
- $ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml

After that you can run teleoperation command to move TurtleBot around your map so it can estimate actual position of robot.
Than you can give him navigation goal and TurtleBot will move to that point while avoiding obstacles

## Simulation
After you make a map of a room you can do simulations inside of gazebo.

- $ roscore
- $ roslaunch turtlebot3_gazebo turtlebot3_house.launch	(launch gazebo)
- $ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=/home/luka/novaMapa.yaml (loading map)

Now we can tell TurtleBot his goal and he will start moving in that direction while avoiding obstacles





