## Robot Package Template

This is a GitHub template. You can make your own copy by clicking the green "Use this template" button.

It is recommended that you keep the repo/package name the same, but if you do change it, ensure you do a "Find all" using your IDE (or the built-in GitHub IDE by hitting the `.` key) and rename all instances of `my_bot` to whatever your project's name is.

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).static_tf_imustatic_tf_imu


## Adding an IMU
An imu has been added to the main urdf via an `imu.xacro` file with the gazebo plugin in it. Also in `gz_bridge.yaml`, the topic bridge has been made. 

Note that I did not follow the `gz-sim` way of using a `.sdf` file, but just made an `.xacro` file and integrated it in a `.urdf`, which the same way for the camera and lidar.

To Visualize the imu in rviz:
```bash
sudo apt-get install ros-<YOUR_ROSDISTO>-imu-tools
```
And a static transformation has been added in `launch_sim.launch` instead of running the node manually everytime:
```bash
ros2 run tf2_ros static_transform_publisher 0 0 0 0 0 0 base_link my_bot/base_link/imu_sensor
```

### Useful Resources in Adding the IMU
- https://www.youtube.com/watch?v=fH4gkIFZ6W8&list=PLunhqkrRNRhYAffV8JDiFOatQXuU-NnxT&index=23
- https://gazebosim.org/docs/latest/sensors/
- https://www.youtube.com/watch?v=WcFyGPEfhHc&list=PL6FI-gIL5jiEd4Hv-NIAuO2Cbbs27UpAM&index=2
- https://github.com/CCNYRoboticsLab/imu_tools
- https://jeremypedersen.com/posts/2024-08-23-pt14-gazebo-sensors/?utm_source=chatgpt.com
- https://ibrahimmansur4.medium.com/migrating-from-gazebo-classic-to-gazebo-sim-a-practical-guide-804af2011011
- https://github.com/ros-controls/gz_ros2_control/issues/374
- https://robotics.stackexchange.com/questions/112321/how-to-use-imu-plugin-with-ros2-control/112322#112322
- https://github.com/gazebosim/gz-sim/blob/ign-gazebo6/examples/worlds/sensors.sdf
- https://github.com/gazebosim/ros_gz/issues/109
- https://github.com/olanrewajufarooq/VariableTiltHexacopter/blob/main/ros_ws/src/hexacopter_description/urdf/variable_tilt_hexacopter.urdf
