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

To get the two launch commands working, we have to replace the launch files.  Simply replace the files found in ydlidar_ros2_driver/launch (inside of the workspace) with the other two files. 

Now build the workspace by using 
>colcon build





The ros2 commands 
>ros2 launch ydlidar_ros2_driver ydlidar_launch.py
>
>ros2 launch ydlidar_ros2_driver ydlidar_launch_view.py

should now work.  



Credit to [https://qiita.com/Yuya-Shimizu/items/c516b076ecc15864c0c5](url) for discovering the syntax issues that made these fixes possible. 

