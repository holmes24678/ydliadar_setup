
# CONFIGURING YDLIDAR 

This project demonstrates how to configure and YDLIDAR in Linux OS.
In this project some changes were made in files to compensate errors during installation. I did not find proper installation resource on official Documentation. this is attempt to give clear Documentation about configuration.
### Disclaimer : All the code is belongs to YD_lidar developers. you can visit their official github repository at https://github.com/YDLIDAR/ydlidar_ros2_driver.
This Supports all types of YDLIDARs.

## Installation

### 1.Installing ROS
Make sure you have installed ROS on your Linux machine. if you are not installed you may check at official Installation guide Here https://docs.ros.org/en/jazzy/Installation.html. 

### 2. Installing YDLIDAR_SDK
Before you installing, make sure that you have installed YDLIDAR_SDK. Clone the github repository

```bash 
git clone https://github.com/YDLIDAR/sdk.git
```
Installing Depencencies

```bash 
sudo apt install cmake pkg-config
```
Follow the below steps

```bash
cd YDLidar-SDK
mkdir build
cmake ..
make
sudo make install
```
Compile YDLidar SDK

```bash
sudo cpack
```
Test the Lidar (connect the Lidar to PC)

```bash
./tri_test
```
you will the following output. if you get same output you have successfully installed the YDLIDAR SDK

### 3. Installing ydlidar_ros2_driver
Since there are some build errors in official files https://github.com/YDLIDAR/ydlidar_ros2_driver.git. I made some changes

#### Create a colcon workspace
```bash
mkdir -p ydlidar_ws/src
cd src
git clone 

cd ydlidar_ws
colcon build --symlink-install\

source ./install/setup.bash
```
This will build and source the workspace (add source file to your .bashrc to avoid sourcing again).
#### Running Ydlidar node
```bash
ros2 run ros2 run ydlidar_ros2_driver ydlidar_ros2_driver_node --ros-args --params-file src/ydlidar_ros2_driver/params/G2.yaml
```
you will get the follwing output

#### Launching ydlidar_lauch file
```bash
ros2 launch ydlidar_ros2_driver ydlidar_launch.launch.py 
```
you will see the output in RVIZ. 
Later you can use SLAM toolbox to perform various mapping algorithms.

Thank you for visit. if you face any problems feel free to reach me out at hsherlock366@gmail.com
