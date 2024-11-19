## System requirements

Tested systems and ROS2 distro
|systems|ROS2 distro|Build status
|--|--|--|
|Ubuntu 22.04|iron|![ROS2 CI](https://github.com/abizovnuralem/go2_ros2_sdk/actions/workflows/ros_build.yaml/badge.svg)
|Ubuntu 22.04|humble|![ROS2 CI](https://github.com/abizovnuralem/go2_ros2_sdk/actions/workflows/ros_build.yaml/badge.svg)
|Ubuntu 22.04|rolling|![ROS2 CI](https://github.com/abizovnuralem/go2_ros2_sdk/actions/workflows/ros_build.yaml/badge.svg)

## Installation

```shell
mkdir -p ros2_ws
cd ros2_ws
git clone --recurse-submodules https://github.com/abizovnuralem/go2_ros2_sdk.git src
sudo apt install ros-$ROS_DISTRO-image-tools
sudo apt install ros-$ROS_DISTRO-vision-msgs

sudo apt install python3-pip clang portaudio19-dev
cd src
pip install -r requirements.txt
sudo apt install python3-open3d
cd ..
```
Pay attention to any error messages. If `pip install` does not complete cleanly, various features will not work. For example, `open3d` does not yet support `python3.12` and therefore you will need to set up a 3.11 `venv` first etc.

Build `go2_ros_sdk`. You need to have `ros2` and `rosdep` installed. If you do not, follow these [instructions](https://docs.ros.org/en/humble/Installation.html). Then:
```shell
source /opt/ros/$ROS_DISTRO/setup.bash
rosdep install --from-paths src --ignore-src -r -y
colcon build
```

## Usage

Don't forget to set up your Go2 robot in Wifi-mode and obtain the IP. You can use the mobile app to get it. Go to Device -> Data -> Automatic Machine Inspection and look for STA Network: wlan0.

```shell
source install/setup.bash
export ROBOT_IP="robot_ip" #for muliple robots, just split by ,
export CONN_TYPE="webrtc"
ros2 launch go2_robot_sdk robot.launch.py
```
