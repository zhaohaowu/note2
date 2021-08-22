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

##### 3、安装显卡驱动
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```
然后去仓库选择最低版本的，不能选择server，重启按f2选择discrete graphic，重启

##### 4、安装chrome，方便登陆账号同步书签

https://www.google.com/chrome/


##### 5、安装输入法，重启后生效

https://pinyin.sogou.com/linux/


##### 6、gedit永久显示行号，tab键宽度设置为4和安装粘贴板

文本编辑器-首选项-编辑器-制表符宽度-4
```
gsettings set org.gnome.gedit.preferences.editor display-line-numbers true
sudo apt-get install parcellite
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













