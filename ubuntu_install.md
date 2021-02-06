# Ubuntu 的安装

## 硬件准备

* 电脑一个（准备用于装 Ubuntu 的电脑，我的是一个古老的 Dell 电脑）

> **注意，Ubuntu 已经不支持 32 位系统了，只支持 64 位系统，所以安装前一定要鉴别下你的系统是 32 位还是 64 位**

* U 盘一个（格式最好是 FAT32，大小至少 2 G，我的是 32 G）

* 一个用于制作启动 U 盘的电脑（我的是一个 MacOS 电脑）

## 资料准备 

* Ubuntu 系统一个，在 Ubuntu 官网 [https://ubuntu.com/](https://ubuntu.com/) 的**下载栏**里下载你所需要的版本的安装包

* Etcher（balenaEtcher） 软件一个，用于将 Ubuntu 系统制作成启动 U 盘，下载地址 [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

* 在 Ubuntu 官网**下载栏**中有一个 **TUTORIALS** 栏，用于教用户如何制作启动 U 盘，安装和升级 Ubuntu 系统。

* Chrome 浏览器的下载列表是 chrome://downloads/ 可以观察你下载的进度

## 创建一个启动 U 盘

* 将 U 盘插到 Mac 电脑上
* 格式化 U 盘
	
	> 温馨提示: 格式化 U 盘前，一定要记得备份哟，文件删了就没了。
	
	* 打开 Mac 的磁盘工具
	* 在磁盘工具中，选中刚刚插入的 U 盘（在外置 tab 下边）
	* 点击抹掉按钮，格式选择 `MS-DOS (FAT)`，scheme 选择 `GUID Partition Map`（如果要求选的话），开始格式化
	* 安装 balenaEtcher
	* 打开 balenaEtcher，选择之前下载的 Ubuntu 系统，选择刚刚格式化的 U 盘，点击 Flash 开始烧制启动 U 盘，烧制结束后，会弹出弹框提示弹出 U 盘

## 在电脑上安装 Ubuntu 系统

* 开机（注意，在安装系统过程中最好一直插着电源）

* 在开机的同时，按住 F12 （有时是 ESC，F10），用于触发开机的 boot menu

	> 如何确定是哪个键呢？
	> 
	> * google 或百度
	> * 查看电脑的说明书
	> * 仔细看开机启动时的提示，提示中有哪个键是 boot menu
	
* 打开 boot menu 后，将从 USB 设备启动设置成第一项，并保存，然后重启开机，这个时候就会进入从 U 盘启动安装 Ubuntu 页面

* 安装结束记得将 boot menu 设置成从本机硬盘启动设置成第一项，将从 USB 设备启动设置回后边。

>  小插曲
> 
>  在安装过程中，会出现卡在紫屏处，屏幕上什么都没有的情况。这个时候，我采取了连接网线、在开机启动时进行硬件检测等操作，但是看起来并不生效。然后，等了很长时间就好了。可能是电脑太旧了，反应慢，当时正在进行处理。但是后来又试了一下，发现又不好使了。最后发现 Ubuntu 已经不支持 32 位系统了。没有办法，在老的 32 位系统上安装 Ubuntu 失败。但是本文流程是正确的。
>
> Ubuntu 的所有的镜像的下载地址 [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) 


