# Turtlebot3-SLAM-map
## Use Turtlebot3 with SLAM approach to create and save a map - Task 3 for track AI at Smart-Methods summer training

>*Note: You should have VMware and ubuntu18.04 and installed ROS melodic first.*

**Type in the terminal these commands:**

1.	Install ROS 1 on Remote PC:</br>
```
$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh
$ chmod 755 ./install_ros_melodic.sh 
$ bash ./install_ros_melodic.sh
```

2. Install Dependent ROS 1 Packages:</br>
```
$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
```
3.	Install TurtleBot3 Packages:</br>
```
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
```
4.	Install simulation packages:</br>
```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
$ cd
$ source ~/catkin_ws/devel/setup.bash
```
5. Launch the simulation world:</br>
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
6. Launch the SLAM Node (New terminal):</br>
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
7. interact and control the robot (New terminal):</br>
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
control the robot using the keys WASDX </br>
Exploring the map with your robot 

	![ ](control.png)
    ![ ](map.png)
8. Save the map:</br>
```
$ rosrun map_server map_saver -f ~/map
```
![ ](save.png)

