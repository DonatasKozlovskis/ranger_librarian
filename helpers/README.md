ranger_librarian_helpers
------------

This ROS package contains nodes/launchers helping to run ranger as library assistant.

Dependencies
------------

- [ranger_ros](https://github.com/chili-epfl/ranger_ros) (branch - ranger_librarian) for running robot wheels and getting sensor data.
- [ranger_description](https://github.com/chili-epfl/ranger_description) (branch - ranger_librarian)  for getting robot description model in RVIZ.

## Usage

Firstly, connect to the same wifi (configuration is done with 'mobots24' network). Connection can be checked using [asebastudio](https://www.thymio.org/en:asebastudio). 

Robot motor control and sensor data publishing bringup:
```
roslaunch ranger_ros bringup.launch
```
Robot model in RVIZ:
```
roslaunch ranger_description display.launch
```
Robot can be moved around in the environment using ROS package `teleop_twist_keyboard`
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
Bringup of RGB-D camera and fake laser scan:
```
roslaunch ranger_ros 3dsensor.launch
```

After bringing the robot as described above, new 3D environment map can be created using launcher from this package:
```
roslaunch ranger_librarian ranger_mapping.launch
```
During the mapping robot can be teleoperated or moved by hands. New waypoints can be added using  [android application](https://github.com/DonatasKozlovskis/ranger_app) or computer keyboard after running:
```
rosrun ranger_librarian keyboard_talker.py
```
where buttons:
- "a": allows to add new waypoint,
- "d": deletes last added waypoint,
- "ctrl+s" triggers action of finishing mapping, saving all waypoints, and switching to localization mode of RGB-D mapping.



