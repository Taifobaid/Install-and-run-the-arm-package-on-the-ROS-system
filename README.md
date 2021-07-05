# Install-and-run-the-arm-package-on-the-ROS-system<br/>
## Ubuntu version :<br/>
Ubuntu 18.04  Which corresponds to ROS melodic.<br/>

## Install ROS melodic : <br/>
### 1-Setup your sources.list :<br/>
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'<br/>
```
### 2-Set up your keys : <br/>
```
sudo apt install curl # if you haven't already installed curl<br/>
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -<br/>
```
### 3-Installation : <br/>
```
sudo apt update<br/>
```
#### Choose Desktop-Full Install: (Recommended) : ROS, rqt, rviz, robot-generic libraries, 2D/3D simulators and 2D/3D perception : <br/>
```
sudo apt install ros-melodic-desktop-full sudo <br/>
```
### 4-Environment setup : <br/>
```
  echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc <br/>
  source ~/.bashrc <br/>
```
### 5-Dependencies for building packages : <br/>
```
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential <br/>
```
#### Initialize rosdep <brl>
  ```
  sudo apt install python-rosdep <br/>
  sudo rosdep init<br/>
  rosdep update <br/>
  ``` 
## Create a workspace by using catkin_make :<br/>
  ```source /opt/ros/melodic/setup.bash <br/>
  mkdir -p ~/catkin_ws/src <br/>
  cd ~/catkin_ws/ <br/>
  catkin_make <br/>
  ```
  
## Installing the package arduino_robot_arm : 
#### Add the “arduino_robot_arm” package to “src” folder :
    cd ~/catkin_ws/src
    sudo apt install git
    git clone https://github.com/smart-methods/arduino_robot_arm 
#### Install all the dependencies :
    cd ~/catkin_ws
    rosdep install --from-paths src --ignore-src -r -y
    sudo apt-get install ros-melodic-moveit
    sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
    sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
    sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
#### Compile the package :
    catkin_make 
## launch arduino_robot_arm :
  ```
  sudo nano ~/.bashrc
  (source /home/ system name /catkin_ws/devel/setup.bash 
  source ~/.bashrc 
  roslaunch robot_arm_pkg check_motors.launch 
  ```
  ![9](https://user-images.githubusercontent.com/67175109/124523079-20673b00-ddfe-11eb-8562-27a92242e963.PNG)




