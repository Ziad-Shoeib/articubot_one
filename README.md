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


## Adding a Deapth Camera
I made 2 versions of depth camera, one is just `depth_camera.xacro` without any noise, and the other is an intel one with some noise `depth_camera_intel.xacro`.
Both ran in rviz and I got the point cloud, but I faced 2 issues, one is that the `image` can not be shown in rviz, the othe is that the point cloud does not detect colors.
Also I needed to make a static transformation as I did with the imu to get the point cloud visualized via rviz

### Useful Resources in adding the depth camera
- https://discuss.ardupilot.org/t/integrating-depth-camera-with-ardupilot-gazebo-for-obstacle-avoidance/112332

- https://robotics.stackexchange.com/questions/111522/i-need-to-simulate-a-realsense-depth-camera-in-gazebo-ignition-fortress-connec?utm_source=chatgpt.com

- https://articulatedrobotics.xyz/tutorials/mobile-robot/hardware/donotadd10-depth-camera/?utm_source=chatgpt.com

- https://www.youtube.com/watch?v=tzN0QT1id0M

- https://index.ros.org/p/ros_gz_sim_demos/?utm_source=chatgpt.com

- https://www.theconstruct.ai/ros2-qa-227-work-with-ros2-depth-camera-data/
- https://www.reddit.com/r/ROS/comments/1d397wb/i_need_to_simulate_a_realsense_depth_camera_in/?rdt=46909
- https://github.com/acceleration-robotics/ros2-igt/blob/e70d16ff4486b0a136afc1f7a1ed6f60fb6340e3/igt_ignition/models/igt_one/model.sdf#L236
- http://sdformat.org/spec?ver=1.12&elem=sensor