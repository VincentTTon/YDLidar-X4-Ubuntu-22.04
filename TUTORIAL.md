# YDLidar-X4-Ubuntu-22.04

Like many others before me, I ran into trouble running the ros2 commands for YDLidar X4 on ROS2 Humble or later.  As it turns out, the SDK contains many errors that need to be corrected for the lidar to operate correctly.  

**This guide is intended to be used after installing the YDLidar X4 SDK and building the ROS2 workspace, as described in** [https://github.com/YDLIDAR/ydlidar_ros2_driver](url)


## Step One:

First ensure that the port has proper permissions to connect to the LiDAR.  This can be done by running
> sudo chmod 777 /dev/ttyUSB0

Test out the LiDAR by running the commands:
>cd ~/YDLidar-SDK/build
>
>./tri_test


At this point, the LiDAR should spin and output "Scan Received".  If not, double check the SDK install and check the ports.  Alternatively, try different baud rates until one works. 

## Step Two:
Replace the ydlidar_ros2_driver_node.cpp file found inside of /ydlidar_ros2_driver/src (which is usually inside your ros2 workspace) with the file in this repo. 

