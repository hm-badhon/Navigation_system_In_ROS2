# ROS Humble Navigation Package Installation

To install the ROS Humble Navigation packages, follow the steps below:

## 1. Open a terminal.

## 2. Run the following command to install the necessary packages:

```bash
sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-turtlebot3*
```

   This command installs the ROS Humble Navigation core, bringup, and TurtleBot3-related packages.

## 3. Wait for the installation process to complete.

## 4. Once the installation is finished, you can proceed with the configuration and usage of the installed packages as per the documentation.


```bash
gedit ~/.bashrc
```

## Add export line

```bash
export TURTLEBOT3_MODEL=waffle
```


```bash
source .bashrc
```

```bash
printenv | grep TURTLE
```
OUTPUT:

```bash
TURTLEBOT3_MODEL=waffle
```
## Gazebo
```bash
gazebo
```


# Start 1st terminal for launch Gazebo

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

```bash
source ~/.bashrc
```
```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

# Start 2nd terminal for RViz

```bash
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
```
# Start 3rd terminal for control robot

```bash
ros2 run turtlebot3_teleop teleop_keyboard
```


# How to save the maps
create a folder in root diractory name as 'maps' . Following this command

```bash
ls /ros2_humble/src/
```
```bash
mkdir maps
```

```bash
ros2 run nav2_map_server map_saver_cli -f maps/my_maps
```

```bash
ls
```
Now you can find this file:

![Alt text](image-1.png)



# *** If get any issue for map dds

```bash
sudo apt update
```
```bash
sudo apt install ros-humble-rmw-cyclonedds-cpp
```

## Add in bashrc 
```bash
gedit .bashrc
```
```bash
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
```
# Go to below this directory

```bash
cd /opt/ros/humble/share/turtlebot3_navigation2/param/
```

```bash
ls
```

```bash
sudo gedit waffle.yaml
```



 ## Change 
```bash
robot_model_type: "differential"
```
 ## to

```bash

robot_model_type: "nav2_amcl::DifferentialMotionModel"

```


## Close all the terminals.

# Then

## Open two terminal
### First terminals for launch the specific world
               
```bash
  ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
### Second for saved maps yaml file
```bash
  ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=ros2_humble/src/maps/my_maps.yaml
```











## Author

- **H.M. Mehedi Hasan (Badhon)**

![85755347](https://github.com/hm-badhon/Natural_Language_Processing_NLP_with_hmb/assets/85755347/1c4c9b08-71fe-463d-8117-cc2b23acb3d9)

  - [GitHub Profile](https://github.com/hm-badhon)
  - [LinkedIn Profile](https://bd.linkedin.com/in/h-m-mehedi-hasan-575563159)
  - [Email](mailto:h.m.badhoneee@gmail.com)
  - Associate Robotics Engineer, NSL


For more information, refer to the official ROS documentation and package-specific README files.
