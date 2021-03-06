# Project Title: Mapless collision avoidance of turtlebot3 using DDPG
The paper is accepted in SII 2021. Paper title 'Accelerated Sim-to-Real Deep Reinforcement Learning: Learning Collision Avoidance from Human Player'

This code is for training and testing ddpg algorithm on turtlebot3 waffle pi.


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. 

### Prerequisites

What things you need to install the software

```
Ubuntu 16.04
ROS Kinetic
Tensorflow
Keras
```

### Installing

The next step is to install dependent packages for TurtleBot3 control on Remote PC. For more details, please refer to [turtlebot3](http://emanual.robotis.com/docs/en/platform/turtlebot3/setup/#setup).

```
$ sudo apt-get update
$ sudo apt-get upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh && chmod 755 ./install_ros_kinetic.sh && bash ./install_ros_kinetic.sh

$ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers

$ cd ~/catkin_ws/src/
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ cd ~/catkin_ws && catkin_make
```


## Setting up the network between PC and turtlebot

Please refer to [Turtlebot3 Setup](http://emanual.robotis.com/docs/en/platform/turtlebot3/pc_setup/#install-ubuntu-on-remote-pc)

## Git clone ddpg scripts

```
$ cd ~/catkin_ws/src/
$ git clone https://github.com/hanlinniu/UGV_CA_ddpg.git
$ cd ~/catkin_ws && catkin_make

```

### Start gazebo world (Change your world file location based on your setting)
To launch the corridor world
```
$ roslaunch turtlebot_ddpg turtlebot3_empty_world.launch world_file:='/home/hanlin/catkin_ws/src/turtlebot_ddpg/worlds/turtlebot3_modified_corridor2.world'
```
To launch the maze world
```
$ roslaunch turtlebot_ddpg turtlebot3_empty_world.launch world_file:='/home/hanlin/catkin_ws/src/turtlebot_ddpg/worlds/turtlebot3_modified_maze.world'

```

### Start a new terminal and Open python virtual environment

```
$ source ~/ddpg_env/bin/activate
```

For train and play with original ddpg

```
$ cd ~/catkin_ws/src/UGV_CA_ddpg/turtlebot_ddpg/scripts/original_ddpg
$ rosrun turtlebot_ddpg ddpg_network_turtlebot3_original_ddpg.py
```


For train and play with ddpg with human data
```
$ cd ~/catkin_ws/src/UGV_CA_ddpg/turtlebot_ddpg/scripts/fd_replay/play_human_data
$ rosrun turtlebot_ddpg ddpg_network_turtlebot3_amcl_fd_replay_human.py

```

For training
```
please change train_indicator=1 under ddpg_network_turtlebot3_original_ddpg.py or ddpg_network_turtlebot3_amcl_fd_replay_human.py
```

For playing trained weights
```
 please change train_indicator=0 under ddpg_network_turtlebot3_original_ddpg.py or ddpg_network_turtlebot3_amcl_fd_replay_human.py

```



## Authors

* **Hanlin Niu** - *Initial work* - [Personal Page](https://www.research.manchester.ac.uk/portal/hanlin.niu.html)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
