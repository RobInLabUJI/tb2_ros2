# tb2_ros2

**IMPORTANT**: check the value of ROS_IP in `docker-compose.yaml`

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
docker compose up
```

### Terminal 4
```
xhost +
docker run --env="USER=eiforamr" --name ei4amr-full \
  --env="DISPLAY=$DISPLAY" -v /tmp/.X11-unix:/tmp/.X11-unix -v $(pwd)/config:/config \
  --network host --ipc host --rm -it eiforamr-full-flavour-sdk:2022.3 \
  /bin/bash

rviz2 -d /config/nav.rviz
```

### Terminal 5
```
docker exec -it ei4amr-full /bin/bash
source /opt/ros/foxy/setup.bash
ros2 launch nav2_bringup naviga tion_launch.py use_sim_time:=false
```

### Terminal 6
```
docker exec -it ei4amr-full /bin/bash
source /opt/ros/foxy/setup.bash
ros2 launch slam_toolbox online_async_launch.py use_sim_time:=false
```

### Terminal 7
```
docker exec -it ei4amr-full /bin/bash
source /opt/ros/foxy/setup.bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
