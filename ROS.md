# 1. ROS installation

## 1.1 Configure your Ubuntu repositories

Configure your Ubuntu repositories to allow "restricted," "universe," and "multiverse."  

## 1.2 Setup your sources.list

    Ubuntu 14.04 (Trusty)

    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu trusty main" > /etc/apt/sources.list.d/ros-latest.list'

## 1.3 Set up your keys

    wget https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -O - | sudo apt-key add -

## 1.4 Installation

First, make sure your Debian package index is up-to-date:

    sudo apt-get update
    sudo apt-get install ros-indigo-desktop-full

## 1.5 Initialize rosdep

Before you can use ROS, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS.

    sudo rosdep init
    rosdep update

## 1.6 Environment setup

It's convenient if the ROS environment variables are automatically added to your bash session every time a new shell is launched:

    echo "source /opt/ros/indigo/setup.bash" >> ~/.zshrc
    source ~/.zshrc

If you have more than one ROS distribution installed, ~/.bashrc must only source the setup.bash for the version you are currently using.

If you just want to change the environment of your current shell, you can type:

    source /opt/ros/indigo/setup.bash

## 1.7 Getting rosinstall

rosinstall is a frequently used command-line tool in ROS that is distributed separately. It enables you to easily download many source trees for ROS packages with one command.

To install this tool on Ubuntu, run:

    sudo apt-get install python-rosinstall
