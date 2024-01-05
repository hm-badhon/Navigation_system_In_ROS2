# Navigation_system_In_ROS2

# ROS Humble Navigation Package Installation

To install the ROS Humble Navigation packages, follow the steps below:

1. Open a terminal.

2. Run the following command to install the necessary packages:

    ```bash
    sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-turtlebot3*
    ```

   This command installs the ROS Humble Navigation core, bringup, and TurtleBot3-related packages.

3. Wait for the installation process to complete.

4. Once the installation is finished, you can proceed with the configuration and usage of the installed packages as per the documentation.

For more information, refer to the official ROS documentation and package-specific README files.

* 
```bash
gedit ~/.bashrc
```

* change and add export line

```bash
TURTLEBOT3_MODEL=waffle
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
*
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
mkdir maps
```

```bash
ros2 run nav2_map_server map_server_cli -f maps/m 
```
```bash
ls
```
Now you can find this file:
![image-1](https://github.com/hm-badhon/Navigation_system_In_ROS2/assets/85755347/a05ba16e-a0ba-414c-b7d7-7f6acddaf526)



```bash

/opt/ros/humble/share

```

# Navigation
```bash

ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=ros2_humble/src/maps/my_map.yaml

```
