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
然后去仓库选择最低版本的，重启按f2选择discrete graphic，重启

##### 4、安装chrome，方便登陆账号同步书签
```
https://www.google.com/chrome/
```

##### 5、安装输入法
```
https://pinyin.sogou.com/linux/
```

##### 6、gedit永久显示行号
```
gsettings set org.gnome.gedit.preferences.editor display-line-numbers true
```

##### 7、双系统时间同步
 ```
sudo apt-get install ntpdate
sudo ntpdate time.windows.com
sudo hwclock --localtime --systohc
 ```

##### 8、安装ssr
```
https://github.com/shadowsocksrr/electron-ssr/releases，
```

##### 9、安装ros
```
http://wiki.ros.org/cn/melodic/Installation/Ubuntu
```

























