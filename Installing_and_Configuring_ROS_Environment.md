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

    echo "source /opt/ros/indigo/setup.zsh" >> ~/.zshrc
    source ~/.zshrc

If you have more than one ROS distribution installed, ~/.bashrc must only source the setup.bash for the version you are currently using.

If you just want to change the environment of your current shell, you can type:

    source /opt/ros/indigo/setup.bash

## 1.7 Getting rosinstall

rosinstall is a frequently used command-line tool in ROS that is distributed separately. It enables you to easily download many source trees for ROS packages with one command.

To install this tool on Ubuntu, run:

    sudo apt-get install python-rosinstall

# 2. Create a ROS Workspace

> These instructions are for ROS Groovy and later. For ROS Fuerte and earlier, select rosbuild. 

Let's create a catkin workspace:

    $ mkdir -p ~/catkin_ws/src
    $ cd ~/catkin_ws/src
    $ catkin_init_workspace

Even though the workspace is empty (there are no packages in the 'src' folder, just a single CMakeLists.txt link) you can still "build" the workspace:

    $ cd ~/catkin_ws/
    $ catkin_make

The catkin_make command is a convenience tool for working with catkin workspaces. If you look in your current directory you should now have a 'build' and 'devel' folder. Inside the 'devel' folder you can see that there are now several setup.*sh files. Sourcing any of these files will overlay this workspace on top of your environment. To understand more about this see the general catkin documentation: catkin. Before continuing source your new setup.*sh file:

    $ source devel/setup.zsh
or add to ~/.zshrc
    source ~/catkin_ws/devel/setup.zsh
    
To make sure your workspace is properly overlayed by the setup script, make sure ROS_PACKAGE_PATH environment variable includes the directory you're in.

    $ echo $ROS_PACKAGE_PATH
    /home/youruser/catkin_ws/src:/opt/ros/indigo/share:/opt/ros/indigo/stacks
