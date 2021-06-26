# ROS-Configuration-Task
First task of Smart-Method which is installing and operating the robot-arm package on ROS.


Steps

1.Download Arduino on Unbuntu using the link given in presentation
![Screenshot 2021-06-17 203008](https://user-images.githubusercontent.com/85634276/123524968-5efe4680-d6d6-11eb-95c9-d3827f0ec7ad.png)

2.Open Terminal and change directory to Arduino file to install it using the command "$ cd ~/Downloads/arduino/arduino-1.8.15"

3.Then use the command "ls" to look for the install text

4.Use the command "$ sudo ./install.sh" to install arduino

![Screenshot 2021-06-17 203522](https://user-images.githubusercontent.com/85634276/123524988-848b5000-d6d6-11eb-9477-4366d872e248.png)

5.Install rosserial using the 2 commands:

$ sudo apt-get install ros-melodic-rosserial-arduino

$sudo apt-get install ros-melodic-rosserial
![Screenshot 2021-06-17 204347](https://user-images.githubusercontent.com/85634276/123525062-f95e8a00-d6d6-11eb-9ff5-d6ad9add7410.png)
![Screenshot 2021-06-17 204417](https://user-images.githubusercontent.com/85634276/123525088-185d1c00-d6d7-11eb-95d0-e20788ca8ade.png)


6.Install arduino_robot_arm package by using the commands:

$ cd ~/catkin_ws/src

$ sudo apt install git

$ git clone https://github.com/smart-methods/arduino_robot_arm

7.Install all the dependencies by using the commands

$ cd ~/catkin_ws

$  rosdep install --from-paths src --ignore-src -r -y

8. encountered an error at command" $  rosdep install --from-paths src --ignore-src -r -y "
because rosdep installation has not been initialized yet.

9.Initialize rosdep by using the 2 commands:

$ sudo rosdep init

$ rosdep update
![Screenshot 2021-06-17 205916](https://user-images.githubusercontent.com/85634276/123525276-18115080-d6d8-11eb-8ebc-88884bbd4940.png)

10.Reuse the command " $ rosdep install --from-paths src --ignore-src -r -y" 
![InkedScreenshot 2021-06-17 210546_blueInk](https://user-images.githubusercontent.com/85634276/123525424-375cad80-d6d9-11eb-9c0c-6c2ef3041ae5.jpg)

11.Type the commands:

$ sudo apt-get install ros-melodic-moveit
![Screenshot 2021-06-17 210732](https://user-images.githubusercontent.com/85634276/123525475-a63a0680-d6d9-11eb-88a4-fa211b551dcc.png)


$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui

$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
![Screenshot 2021-06-17 210933](https://user-images.githubusercontent.com/85634276/123525489-be118a80-d6d9-11eb-924f-6e786b4508c5.png)

$  sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
![Screenshot 2021-06-17 211101](https://user-images.githubusercontent.com/85634276/123525503-d08bc400-d6d9-11eb-872d-9b9f76eaf54c.png)
11.Compile the package by using the command " $ catkin_make"
![Screenshot 2021-06-17 211258](https://user-images.githubusercontent.com/85634276/123525529-08930700-d6da-11eb-8340-4dace406440e.png)

12.Control the motors by using the command "$ roslaunch robot_arm_pkg check_motors.launch "
![Screenshot 2021-06-17 214658](https://user-images.githubusercontent.com/85634276/123525557-42fca400-d6da-11eb-92db-6a9dbc9583ff.png)

but I got an error saying" [check_motors.launch] is neither a launch file in package [robot_arm_pkg] nor is [robot_arm_pkg] a launch file name

13. type the commands:

" $ sudo nano ~/.bashrc"

scroll down at the end of the page then copy "setup.bash" path, then type " source /home/linux/catkin_ws/devel/setup.bash", then press ctrl+o,
then type command "source ~/bashrc"

14. use command " roslaunch robot_arm_pkg check_motors.launch "  so Rviz will run
 ![Screenshot 2021-06-18 214834](https://user-images.githubusercontent.com/85634276/123525592-88b96c80-d6da-11eb-873f-2aee7f145100.png)

15. Type the following commands:
$ cd ~/Arduino/libraries


$ rm -rf ros_lib rosrun rosserial_arduino make_libraries.py ~/Arduino/libraries
![Screenshot 2021-06-18 224158](https://user-images.githubusercontent.com/85634276/123525640-eb126d00-d6da-11eb-8ea7-ff5879cdcdf9.png)


16. could not upload Arduino code so I did the commands:

ls /dev/ttyS0

ls -l /dev/ttyS0

sudo usermod -a -G dialout linux

sudo chmod a+w /dev/ttyS0

then I logged out then in and it worked

17.run RViz by using the command " $ roslaunch robot_arm_pkg check_motors.launch

18. run Gazebo by using the command "roslaunch robot_arm_pkg check_motors_gazebo.launch

but I encountered a problem that got fixed by using the "export SVGA_VGPU10=0" command
![Screenshot 2021-06-18 234346](https://user-images.githubusercontent.com/85634276/123525676-1f862900-d6db-11eb-9e68-a1b4b36c21f3.png)

19. try linking RViz and Gazebo by using "cd catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts

sudo chmod +x joint_states_to_gazebo.py

rosrun robot_arm_pkg joint_states_to_gazebo.py
![Screenshot 2021-06-18 234538](https://user-images.githubusercontent.com/85634276/123525744-a3d8ac00-d6db-11eb-83ef-4a2203820c1b.png)

![Screenshot 2021-06-18 234633](https://user-images.githubusercontent.com/85634276/123525765-cff42d00-d6db-11eb-9cab-79e68377101d.png)

20. launching moveit by using the command "roslaunch moveit_setup_assistant setup_assistant.launch"

21. use command roslaunch moveit_pkg demo_gazebo.launch to run gazebo and rviz
![Screenshot 2021-06-19 000918](https://user-images.githubusercontent.com/85634276/123525773-e0a4a300-d6db-11eb-927a-ba0c2e55c877.png)


