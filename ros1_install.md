##ROS1 Noetic install (for ubuntu20.04)
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

```
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

```
sudo apt update
sudo apt install ros-noetic-desktop
```

bash
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc source ~/.bashrc
```

```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator
python3-wstool build-essential python3-rosdep
```

```
sudo rosdep init
rosdep update
```
