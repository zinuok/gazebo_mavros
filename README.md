# gazebo_mavros
gazebo simulation using SITL for mavros px4


+ gazebo simulation with mavros
from [here](https://dev.px4.io/v1.9.0/en/simulation/ros_interface.html) and [engcang](https://github.com/engcang/mavros-gazebo-application)

```
# preparation
$ sudo apt install ros-melodic-gazebo-plugins
$ sudo apt install -y python3-pip
$ pip3 install --user jinja2 toml empy pyros-genmsg packaging numpy
$ sudo apt install -y libgstreamer-plugins-base1.0-dev

# download Firmware
$ git clone -b v1.10.0 https://github.com/PX4/Firmware.git --recursive
```

add followings into '~/.bashrc': we use 'mavros_posix_sitl' launch file in which gazebo simulation and mavros are executed.
```
alias sim='cd ~/Firmware && DONT_RUN=1 make px4_sitl_default gazebo && source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default && export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd) && export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)/Tools/sitl_gazebo && roslaunch px4 mavros_posix_sitl.launch'
```

+ Offboard control using mavros ROS wrapper
Offboard control package
refer 'tx2_test' directory.
<br>
usage
```
$ roslaunch tx2_test [type]_traj_[mode].launch
```
