# Debian 的安装

## 硬件准备

* 电脑一个（准备用于装 Debian 的电脑，我的是一个古老的 Dell 电脑）

> **注意，由于 Ubuntu 已经不支持 32 位系统了，只支持 64 位系统，所以没有办法，只好安装 Debian了**

* U 盘一个（格式最好是 FAT32，大小至少 2 G，我的是 32 G）

* 一个用于制作启动 U 盘的电脑（我的是一个 MacOS 电脑）

## 资料准备 

* Debian 系统一个，在 Debian 官网 [https://www.debian.org/](https://www.debian.org/) ，点击**下载 Debian** 一侧的**更多**跳转到新的页面，在“更多”页面里点击**下载**进入下载页面下，然后在**下载一个安装映像**中点击**较庞大的完整安装映像**，在跳转的新页面中点击**通过 HTTP 下载 CD/DVD 映像文件**，选择 **debian-cd 档案库的已注册镜像** 中的 **瑞典的主要 CD 映像服务器** 进行下载

* 上述步骤实际的地址就是 **[https://cdimage.debian.org/debian-cd/](https://cdimage.debian.org/debian-cd/)** 我选择了 current 中的 i386 的 iso-dvd

* 下载页面中有多个 iso，一般选择第一个，因为**第一片光盘包含安装系统及最流行的软件包**。第二片光盘包含较不流行的。第三片光盘则是更不流行的，以此类推。 您可能只需要第一片 DVD (或是前两片光盘)，除非你有非常特殊的需求。（参见**常见问答集** [https://www.debian.org/CD/faq/#which-cd](https://www.debian.org/CD/faq/#which-cd)）

* Etcher（balenaEtcher） 软件一个，用于将 Debian 系统制作成启动 U 盘，下载地址 [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

* Chrome 浏览器的下载列表是 chrome://downloads/ 可以观察你下载的进度

## 创建一个启动 U 盘

* 将 U 盘插到 Mac 电脑上
* 格式化 U 盘
	
	> 温馨提示: 格式化 U 盘前，一定要记得备份哟，文件删了就没了。
	
	* 打开 Mac 的磁盘工具
	* 在磁盘工具中，选中刚刚插入的 U 盘（在外置 tab 下边）
	* 点击抹掉按钮，格式选择 `MS-DOS (FAT)`，scheme 选择 `GUID Partition Map`（如果要求选的话），开始格式化
	* 安装 balenaEtcher
	* 打开 balenaEtcher，选择之前下载的 Debian 系统，选择刚刚格式化的 U 盘，点击 Flash 开始烧制启动 U 盘，烧制结束后，会弹出弹框提示弹出 U 盘

## 在电脑上安装 Debian 系统

* 开机（注意，在安装系统过程中最好一直插着电源）

* 在开机的同时，按住 F12 （有时是 ESC，F10），用于触发开机的 boot menu

	> 如何确定是哪个键呢？
	> 
	> * google 或百度
	> * 查看电脑的说明书
	> * 仔细看开机启动时的提示，提示中有哪个键是 boot menu
	
* 打开 boot menu 后，将从 USB 设备启动设置成第一项，并保存，然后重启开机，这个时候就会进入从 U 盘启动安装 Debian 页面

* 安装结束记得将 boot menu 设置成从本机硬盘启动设置成第一项，将从 USB 设备启动设置回后边。



