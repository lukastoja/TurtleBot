# TurtleBot

## Summary

My task was to prepare TurtleBot, so that people can work with them.
TurtleBot has many fuctions from basic fuctions(moving around or rotate) to mapping a room.

### Preparing my PC for work

First I had to install Ubuntu 16.04 on my remote PC. After that I had to install ROS and dependent ROS packages.
And I had to set my IP adress in bashrc file.
After that my PC was set up to work with TurtleBot.

### Preparing Raspberry Pi for work

I also had to set up TurtleBot. First I had to install OS on Raspberry Pi, so I had chosen Raspbian as OS.
After that I needed to set up IP adress of my remote PC and IP adress of my TurtleBot inside of bashrc file.

After this step my remote PC could connect to TurtleBot over ssh command, and I could finnaly start working with TurtleBot.

### Installing Firmware on OpenCR

Now I hade to communicate with motors so that TurtleBot could move around.
That was made over OpenCR board. I hade to upload OpenCR firmware on OpenCR board which I found on
robotis github repository.There were 2 ways of uploading Firmware to OpenCR.
First one is through terminal and second one is trough Arduino IDE.
After that I could press button SW 1 or SW 2 on OpenCR and robot would move forward or rotate.

### Bringup

First I had to make server on which would TurtleBot connect so that my PC and TurtleBot could communicate.
This procedure is called Bringup. To see if everything is working normally I loaded TurtleBot inside rviz program.
Inside rviz I could see that my TurtleBot is sending me data from his laser sensor. This data is used to see how far is the obstacle from TurtleBot. Rviz uses this data to visually show us where the obstacle is. It is shown to us with small red dots.

Now I could finally start with basic operation

### Basic Operation

There are many ways of how to control TurtleBot. You can use keyboard, PS3 Joystick, XBOX 360 Joystick,
Wii Remote, LEAP Motion, etc. just to move hime around your room (move forward, backwards, left, right, rotate right, rotate left).
Rviz program is giving us the ability to control TurtleBot (to move him around room).

TurtleBot has fuction to detect obstacle. It will move forward until it detects obstacle and will move very close to it without touching it. It will send data to our PC so we can see how far the obstacle is and when did it stop.

There is also point operation where we give TurtleBot x,y coordinates and z-angular and TurtleBot will move to point x,y and then rotates for z-angular.

One cool feature is called patrol.
We can say what type of patrol we want (rectangle, triangle and circle). So we give TurtleBot type of patrol, radius of patrol (for example if we say circle we must give him radius of that circle) and how many times do we want him to repeat that lap.

### SLAM (Simultaneous Localization and Mapping)

This feature gives us ability to make a map of a room and to navigate TurtleBot with that map.
Firstly I started SLAM program and used my keyboard to move robot around a room. After I made mape of a room I started navigation program in which you can tell estimated pose of robot. Then you move it around a little to get a precise pose of the robot. After that you can tell him point/goal where it needs to move and he will move to that point while avoiding obstacles.
Also we can use that map to run simulation so we dont need to use real robot. So first you make simulation and when everything works inside of simulation then you test it on real TurtleBot.