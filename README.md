<h1>学习linux总结</h1>
<h3>1.安装linux</h3>
先安装VirtualBOX虚拟机搭建linux系统,VirtualBOX安装完成后,在点击新建出现新建虚拟电脑,在输入虚拟的相应的名称会自动识别相应的虚拟机类型和版本(如图1-1),一直点击下一步,新建完成后。选中刚创建的虚拟机,点击红色方框处的”设置”,进行相关参数设置。其他的设置不变，主要是设置”存储”,点击红色框找到相应的系统镜像文件(如图1-2),再点击”启动”虚拟机,安装相应的步骤安装linux系统。
<h3>2.安装组件</h3>

#### 2.1网络通讯
ifconfig命令用于显示或设置网络设备,使用ifconfig前要先安装net-tools,命令yum –y install net-tools(如图2-14)。

#### 2.2安装其他组件
输入yum -y install lrzsz 安装lrzsz ,输入yum –y install wget安装wget下载组件

