# 6-dof-robotic-arm
6 DOF Robotic Arm (ROS + Gazebo)

## Error
If you have error regarding " nlopt ", just do:

    sudo apt install libnlopt-cxx-dev




### Installation
Clone the repository using:

    git clone https://github.com/niweshsah/kinova_robo_Arm_test1.git

Run catkin build in your ROS source directory

    $ cd ~/catkin_ws
    $ catkin build

Start the simulation using:

    $ roslaunch owr_gazebo owr_spawn2.launch

Launch moveit and rviz:

    $ roslaunch owr_moveit_config owr_simulation_execution.launch
