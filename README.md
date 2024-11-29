
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
git clone https://github.com/YDLIDAR/YDLidar-SDK.git
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
![Screenshot from 2024-11-27 00-38-10](https://github.com/user-attachments/assets/37f281f4-024e-46a9-b01f-ed684797bf9e)

### 3. Installing ydlidar_ros2_driver
Since there are some build errors in official files https://github.com/YDLIDAR/ydlidar_ros2_driver.git. I made some changes

#### Create a colcon workspace
```bash
mkdir -p ydlidar_ws/src
cd src
git clone https://github.com/holmes24678/ydlidar_setup.git

cd ydlidar_ws
colcon build --symlink-install

source ./install/setup.bash
```
This will build and source the workspace (add source file to your .bashrc to avoid sourcing again).
#### Running Ydlidar node
```bash
ros2 run ros2 run ydlidar_ros2_driver ydlidar_ros2_driver_node --ros-args --params-file src/ydlidar_ros2_driver/params/G2.yaml
```
you will get the follwing output
![Screenshot from 2024-11-27 00-38-10](https://github.com/user-attachments/assets/e8d52ce3-8471-4942-b994-00c00c017556)


#### Launching ydlidar_lauch file
```bash
ros2 launch ydlidar_ros2_driver ydlidar_launch.launch.py 
```
you will see the output in RVIZ. 
![Screenshot from 2024-11-27 01-01-04](https://github.com/user-attachments/assets/ab9add48-6603-4fb7-b794-a6ce740eb115)

Later you can use SLAM toolbox to perform various mapping algorithms.

Thank you for visit. if you face any problems feel free to reach me out at hsherlock366@gmail.com
