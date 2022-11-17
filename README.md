# tb2_ros2

### Terminal 1
```
ssh pi@192.168.0.114

source /opt/ros/noetic/setup.bash
source ~/catkin_ws/devel/setup.bash
export ROS_IP=192.168.0.114
export ROS_MASTER_URI=http://192.168.0.114:11311
export TURTLEBOT_BATTERY=None
roslaunch turtlebot_bringup minimal.launch
```

### Terminal 2
```
ssh pi@192.168.0.114

source /opt/ros/noetic/setup.bash
source ~/catkin_ws/devel/setup.bash
export ROS_IP=192.168.0.114
export ROS_MASTER_URI=http://192.168.0.114:11311
rosparam load bridge_ros2/config.yaml 
export TURTLEBOT_3D_SENSOR=astra
roslaunch turtlebot_navigation scan.launch
```

### Terminal 3
```
```

### Terminal 4
```
```

### Terminal 5
```
```

### Terminal 6
```
```

### Terminal 7
```
```
