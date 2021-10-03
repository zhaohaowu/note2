##### 未来不可避免的还要重装很多次系统，记录下重装后的事情

##### 1、安装系统

删除ubuntu硬盘，保留交换空间盘，使用软碟通制作系统盘，安装的时候只需要将所有ubuntu硬盘用于主分区，空间起始位置，ext4日志文件系统，挂载点为/

##### 2、安装后重启黑屏问题

选择第二项ubuntu高级设置，选择recovery模式，选择grub，选择resume，回车进入系统，
```
sudo gedit /etc/default/grub
```
将quiet splash修改为
```
quiet splash nomodeset
```
然后
```
sudo update-grub
```

##### 3、安装显卡驱动，解决外接显示屏无法使用以及屏幕亮度无法调节问题，解决触摸板问题

https://blog.csdn.net/zhaohaowu/article/details/114284288
https://blog.csdn.net/zhaohaowu/article/details/114287116

##### 4、安装chrome，方便登陆账号同步书签

https://www.google.com/chrome/


##### 5、安装输入法，重启后生效

https://pinyin.sogou.com/linux/
```
gedit ~/.config/sogoupinyin/conf/env.ini
```
将StatusAppearance设置为StatusAppearance=0


##### 6、gedit永久显示行号，tab键宽度设置为4和安装粘贴板，安装录屏，截图工具，视频播放器，rar

文本编辑器-首选项-编辑器-制表符宽度-4
```
gsettings set org.gnome.gedit.preferences.editor display-line-numbers true
sudo apt install parcellite
sudo apt install kazam
sudo apt install deepin-screenshot
sudo apt install vlc
sudo apt-get install rar unrar
sudo apt-get install rar rar
```

##### 7、双系统时间同步
 ```
sudo apt-get install ntpdate
sudo ntpdate time.windows.com
sudo hwclock --localtime --systohc
 ```

##### 8、安装ssr

https://github.com/shadowsocksrr/electron-ssr/releases


##### 9、安装ros

http://wiki.ros.org/cn/melodic/Installation/Ubuntu


rosdep update解决方法

https://blog.csdn.net/weixin_43311920/article/details/114796748

##### 10、安装aruco

https://sourceforge.net/projects/aruco/files/?source=navbar

```
cd aruco-3.1.2&&mkdir build&&cd build&&cmake ..&&sudo make install
```

##### 11、安装realsense

https://blog.csdn.net/zhaohaowu/article/details/119837948

##### 12、安装c++版opencv

https://blog.csdn.net/zhaohaowu/article/details/113749936

##### 13、安装升级pip3和pip

```
sudo apt-get install python3-pip
pip3 install --upgrade pip -i https://pypi.tuna.tsinghua.edu.cn/simple
sudo apt-get install python-pip
pip install --upgrade pip -i https://pypi.tuna.tsinghua.edu.cn/simple
```
豆瓣源：-i https://pypi.douban.com/simple

##### 14、安装python版opencv

```
pip3 install opencv-python -i https://pypi.tuna.tsinghua.edu.cn/simple
pip3 install opencv-contrib-python -i https://pypi.tuna.tsinghua.edu.cn/simple
```
##### 15、安装autoware

https://blog.csdn.net/zhaohaowu/article/details/119839147

##### 16、melodic代码解决bug

aruco代码只需要完成9，10，11，12就可以编译

问题
```
  Could not find a package configuration file provided by "move_base_msgs"
```
解决方法
```
sudo apt-get install ros-melodic-navigation
```
##### 17、解决carlike_robot_sim代码bug

代码：https://blog.csdn.net/qq_36754438/article/details/109125320

问题
```
Found unsuitable Qt version "" from NOTFOUND, this code requires Qt 4.x
```
解决方法
```
sudo apt-get install qt4-default
```
问题
```
package 'orocos-bfl' not found
```
解决方法
```
sudo apt-get install ros-melodic-bfl
```
##### 17、安装vscode

https://code.visualstudio.com/download

安装c++和中文插件

vscode安装完空格显示很短解决方案

ctrl + ,打开设置，搜索font family，将原内容修改为'monospace'

##### 18、ubuntu修改登录密码

```
sudo passwd zhw
```
##### 19、turtlebot3仿真

安装turtlebot3的ros包
```
sudo apt-get install ros-melodic-turtlebot3 ros-melodic-turtlebot3-description ros-melodic-turtlebot3-gazebo ros-melodic-turtlebot3-msgs ros-melodic-turtlebot3-slam ros-melodic-turtlebot3-teleop
sudo apt-get install ros-melodic-slam-gmapping
sudo apt-get install ros-melodic-navigation
```
建图
```
roslaunch turtlebot3_gazebo turtlebot3_house.launch
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
roslaunch turtlebot3_slam turtlebot3_slam.launch
```
保存地图
```
mkdir -p ~/maps/housemap
rosrun map_server map_saver -f ~/maps/housemap/housemap
```
导航
```
roslaunch turtlebot3_gazebo turtlebot3_house.launch
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=/home/zhw/maps/housemap/housemap.yaml #/home/zhw这里必须用绝对路径不能用~
```
##### 20、安装zed2，astra和kinect相机

```
cd ~/catkin_ws/src/ 
git clone https://github.com/stereolabs/zed-ros-wrapper.git
cd ~/catkin_ws
catkin_make -DCMAKE_BUILD_TYPE=Release
echo source $(pwd)/devel/setup.bash >> ~/.bashrc
source ~/.bashrc
roslaunch zed_wrapper zed.launch
```

```
cd ~/catkin_ws/src
git clone https://github.com/orbbec/ros_astra_camera
roscd astra_camera
./scripts/create_udev_rules
cd ~/catkin_ws
catkin_make --pkg astra_camera
roslaunch astra_camera astra.launch
```

```
sudo apt-get install ros-melodic-freenect-*
git clone https://github.com/avin2/SensorKinect.git
sudo ./install.sh 
roslaunch mrobot_bringup freenect.launch 
```

##### 21、安装evo

```
git clone https://github.com/MichaelGrupp/evo
cd evo
pip install --editable . --upgrade --no-binary evo
测试
cd test/data
evo_traj kitti KITTI_00_ORB.txt KITTI_00_SPTAM.txt --ref=KITTI_00_gt.txt -p --plot_mode=xz
然后出现ModuleNotFoundError: No module named 'tkinter'
sudo apt-get install python3-tk
```

##### 22、安装sophus

```
git clone https://github.com/strasdat/Sophus.git
cd Sophus && mkdir build && cd build && cmake .. && sudo make install
```

##### 23、安装pangolin

```
sudo apt-get install libglew-dev
sudo apt-get install libboost-dev libboost-thread-dev libboost-filesystem-dev
sudo apt-get install libpython2.7-dev
git clone https://github.com.cnpmjs.org/stevenlovegrove/Pangolin.git
cd Pangolin && mkdir build && cd build && cmake .. && cmake --build . && sudo make install
```

##### 24、安装ceres

```
sudo apt-get install liblapack-dev libsuitesparse-dev libcxsparse3 libgflags-dev libgoogle-glog-dev libgtest-dev
git clone https://github.com/ceres-solver/ceres-solver
cd ceres-solver && mkdir build && cd build && cmake .. && make  && sudo make install
```

##### 25、安装g2o

```
sudo apt install qt5-qmake qt5-default libqglviewer-dev-qt5 libsuitesparse-dev libcxsparse3 libcholmod3
cd g2o && mkdir build && cd build && cmake .. && make  && sudo make install
```





