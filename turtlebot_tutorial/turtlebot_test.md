Reference : https://www.ncnynl.com/archives/201903/2884.html

Modified by Yan CHEN



## Requirement

* Ubuntu 18.04
* Ros melodic

## Create workplace

1. Install independence packages

   ```commend
   $ sudo apt-get install ros-melodic-kobuki-*
   $ sudo apt-get install ros-melodic-ecl-streams
   $ sudo apt-get install libusb-dev
   $ sudo apt-get install libspnav-dev
   $ sudo apt-get install ros-melodic-joystick-drivers
   $ sudo apt-get install bluetooth
   $ sudo apt-get install libbluetooth-dev
   $ sudo apt-get install libcwiid-dev
   $ sudo apt-get install ros-melodic-bfl
   ```

2. Create workplace and install packages

   ```
   $ mkdir -p ~/turtlebot_ws/src 
   $ cd ~/turtlebot_ws/src 
   
   $ git clone https://github.com/turtlebot/turtlebot_simulator
   $ git clone https://github.com/turtlebot/turtlebot.git
   $ git clone https://github.com/turtlebot/turtlebot_apps.git
   $ git clone https://github.com/udacity/robot_pose_ekf
   $ git clone https://github.com/ros-perception/depthimage_to_laserscan.git 
   $ git clone https://github.com/yujinrobot/kobuki_msgs.git
   $ git clone https://github.com/yujinrobot/kobuki_desktop.git
   $ cd kobuki_desktop/
   $ rm -r kobuki_qtestsuite
   $ git clone https://github.com/toeklk/orocos-bayesian-filtering.git
   $ git clone https://github.com/turtlebot/turtlebot_msgs.git
   $ git clone https://github.com/ros-drivers/joystick_drivers.git
   $ git clone https://github.com/ncnynl/turtlebot_viz
   ```

3. Copy ```kobuki``` and ```yujin_ocs``` packages to workplace ```turtlebot_ws/src```

   ```
   $ mkdir -p ~/repos/
   $ cd ~/repos/
   $ git clone https://github.com/yujinrobot/kobuki.git
   $ cp -r kobuki/* ~/turtlebot_ws/src/
   $ git clone https://github.com/yujinrobot/yujin_ocs.git
   $ cp -r yujin_ocs/yocs_cmd_vel_mux/ yujin_ocs/yocs_controllers ~/turtlebot_ws/src/
   ```

4. Build workplace

   ```
   $ cd ~/turtlebot_ws
   $ catkin_make
   ```

5. Add path

   ```
   $ echo "source ~/turtlebot_ws/devel/setup.bash" >> ~/.bashrc
   $ source ~/.bashrc 
   ```

## Launch turtlebot 

1. Open a new terminal on netbook and run ```$ roscore``` 

2. Open a new terminal on netbook and run ```$ ls /dev/kobuki ``` for observing equipment. If not  and have a information like ```ls: cannot access '/dev/kobuki': No such file or directory```, run ```rosrun kobuki_ftdi create_udev_rules``` and unplug, replug robot and type ```ls /dev/kobuki ``` again. If display ```/dev/kobuki```, you are successful.

3. Launch turtlebot

   ```
   $ roslaunch turtlebot_bringup minimal.launch
   ```


## Keyboard control

1. Control turtlebot with keyboard

   ```
   $ roslaunch turtlebot_teleop keyboard_teleop.launch
   ```

## Test camera

* Install ```openni2_camera```

  ```
  $ sudo apt-get install ros-melodic-openni2-*
  $ rospack profile
  ```

* Set environment path

  ```
  $ echo $TURTLEBOT_3D_SENSOR
  # Output : asus_xtion_pro
  
  $ echo "export TURTLEBOT_3D_SENSOR=asus_xtion_pro" >> .bashrc
  ```

* Launch camera

  ```
  roslaunch openni2_launch openni2.launch depth_registration:=true
  ```

* Open color image

  ```
  $ rosrun image_view image_view image:=/camera/rgb/image_raw
  ```

* Open depth image

  ```
  $ rosrun image_view image_view image:=/camera/depth_registered/image_raw
  ```

## Example of Rviz

```
roslaunch turtlebot_stage turtlebot_in_stage.launch 
```

<img src="turtlebot_test.assets/Screenshot from 2021-03-21 13-19-18.png" alt="Screenshot from 2021-03-21 13-19-18.png" style="zoom: 25%;" />



