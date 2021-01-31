
# 硬件

* 树莓派 4B
* 显示屏一个
* 8G 以上的 SD 卡和读卡器（推荐 32 G 及以上的 SD 卡）
* 树莓派电源线一根（type C），树莓派与显示屏数据线一根（HDMI）、树莓派与显示屏供电线一个根（USB）
*  鼠标、键盘、耳机
*  网线（可选）

> 注意: 树莓派支持连接两个显示屏 
 
# 系统镜像与树莓派启动

* 下载镜像
  
	- 树莓派官网地址 [https://www.raspberrypi.org](https://projects.raspberrypi.org/en)
	
	- 选择 software tab，然后点击 Our software
	
	- 下载树莓派 Imager
	
	- 安装 Imager
	
	- 写入前需要用 Imager 将 SD 卡格式化成 FAT32 格式
	
	- 运行 Imager 将磁盘镜像写入 SD 卡

	- 修改屏幕分辨率

	 把 SD 卡插在电脑上，打开根目录的 config.txt 文件并在文件末尾加上如下代码
	
	```
	max_usb_current=1
	hdmi_force_hotplug=1
	config_hdmi_boost=7
	hdmi_group=2
	hdmi_mode=1
	hdmi_mode=87
	hdmi_drive=1
	display_rotate=0
	hdmi_cvt 1024 600 60 6 0 0 0 
	```
	其中，hdmi_cvt 后边的 1024 600 是显示器的分辨率
	
*  树莓派启动

	- 将 SD 卡插入树莓派
	
	- 将树莓派、显示器连接（2 根），将树莓派连接电源 

	- 开机，然后像正常配置电脑一样配置树莓派（如时区、地区、键盘设置、语言、账号密码、wifi 等）
		
		- 树莓派的默认用户名是 pi 密码是 raspberry

		- 方便的话需要接上鼠标和键盘

	> 注意: 
	>
	> * 一定要将电线连接好，不可松动，不可没有插到位造成接触不良，否则出现问题很难排查
	> * 目前树莓派启动不支持 ExFAT 所以需要格式化成 FAT32，可以用 Imager 格式化，也可以用自己的格式化工具格式化一下。
	> * 烧制好 SD 卡后，如果之前树莓派没有关机，一定要将树莓派完全断电关机，然后再插入 SD 卡开机。如果不这样做，可能会开机后屏幕不亮，但是却不知道是什么原因。
	
# 几种连接树莓派的方法

* 有屏幕

	- 直接键盘、鼠标像操作一个电脑一样操作就行了

	- 注意一定要获取 IP 信息

* 无屏幕，有网线
	
	- 在 SD 卡的根目录创建一个名为 ssh 的文件

	- 将网线一端连接树莓派、另一端连接路由器（也可与电脑连接，通过共享网络的方式获取树莓派的 IP）

	- 在路由器的后台获取到树莓派的 IP 或者通过 Advanced IP Scanner 获取
	
	- ssh 远程登录树莓派 

* 无屏幕，无网线

	- 在 SD 卡的根目录创建一个名为 ssh 的文件和一个 wpa_supplicant.conf 文件

	- 在 wpa_supplicant.conf 中写如下内容

	```
	country=CN
	ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
	update_config=1
	
	network={
		ssid="第一个 wifi 的名字，不能有中文，引号不能删除"
		psk="第一个 wifi 的密码，引号不能删除"
		priority=数字，表示权限，越大优先级越高
	}
	
	network={
		ssid="第二个 wifi 的名字，不能有中文，引号不能删除"
		psk="第二个 wifi 的密码，引号不能删除"
		priority=数字，表示权限，越大优先级越高
	}
	```

	- 在路由器的后台获取到树莓派的 IP 或者通过 Advanced IP Scanner 获取

	- ssh 远程登录树莓派 

# 无线网的配置方法

* 有显示器

	- 在界面上直接配置，就像配置电脑一样

* 只有终端

	- 修改 /etc/wpa_supplicant/wpa_supplicant.conf 

* 在 SD 卡的根目录创建一个 wpa_supplicant.conf 文件

- 在 wpa_supplicant.conf 中写如下内容

	```
	country=CN
	ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
	update_config=1
	
	network={
		ssid="第一个 wifi 的名字，不能有中文，引号不能删除"
		psk="第一个 wifi 的密码，引号不能删除"
		priority=数字，表示权限，越大优先级越高
		key_mgmt=WPA-PSK // 这个是加密方式，如果不知道，可以不写，一般可以连上
	}
	
	network={
		ssid="第二个 wifi 的名字，不能有中文，引号不能删除"
		psk="第二个 wifi 的密码，引号不能删除"
		priority=数字，表示权限，越大优先级越高
		key_mgmt=WPA-PSK // 这个是加密方式，如果不知道，可以不写，一般可以连上
	}
	```

# 开启 ssh 的方法

* 在 SD 卡根目录创建一个 ssh 文件

*  在树莓派上 sudo /etc/init.d/ssh start （当次有效，重启后要重开）

* 在图形化界面上 菜单 -> 偏好设置 -> Raspberry Pi Configuration -> enable ssh

* sudo raspi-config -> Interfacing Options -> SSH -> Enabled

# 开启 VNC 的方法

* 树莓派上执行 vncserver 命令（当次有效，重启后要重开）

* 在图形化界面上 菜单 -> 偏好设置 -> Raspberry Pi Configuration -> enable VNC

* sudo raspi-config -> Interfacing Options -> VNC -> Enabled

* 个人电脑上使用 VNC Viewer 等工具连接

> 可能出问题的情况
> 
> * 树莓派没有连网
> * 树莓派没有开启 VNC
> * 客户端使用的 IP、账号、密码不对

# 获取树莓派的 IP

* 树莓派上执行 ifconfig 命令

* 路由器后台查询

* Advanced IP Scanner

# 设置静态 IP

* 查看 /etc/network/interfaces 注释中指出了静态 IP 的配置位置

* 一般在 /etc/dhcpcd.conf

* 加上如下配置

```
interface eth0 # 有线

static ip_address=192.168.47.133/24 # 静态 IP，注意后边要接 /24
static routers=192.168.0.1 # 网关
static domain_name_servers=192.168.0.1 # DNS

interface wlan0 # 无线

static ip_address=192.168.47.133/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```

* 配置好后重启树莓派

	- 界面重启

	- sudo reboot

# 如何进入路由器后台

* 如果你的电脑和树莓派在一个局域网，可以在电脑上查看路由器地址（Mac 是在网络偏好设置 -> 高级 -> TCP/IP 配置中）。也可以去路由器上看下，一般上边写了。

* 其次你需要路由器的账号和密码

* 浏览器输入登录路由器的 IP，输入账号和密码就好了
 	
# 其他 

* 常用网站 [https://projects.raspberrypi.org/en](https://projects.raspberrypi.org/en)

* 树莓派初始化相关文档 [https://projects.raspberrypi.org/zh-CN/projects/raspberry-pi-getting-started](https://projects.raspberrypi.org/zh-CN/projects/raspberry-pi-getting-started)

* 官方文档（software tab -> help -> documentation） [https://www.raspberrypi.org/documentation/installation/](https://www.raspberrypi.org/documentation/installation/)


      