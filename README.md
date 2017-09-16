<h1>学习linux总结</h1>
<h3>1.安装linux</h3>
先安装VirtualBOX虚拟机搭建linux系统,VirtualBOX安装完成后,在点击新建出现新建虚拟电脑,在输入虚拟的相应的名称会自动识别相应的虚拟机类型和版本(如图1-1),一直点击下一步,新建完成后。选中刚创建的虚拟机,点击红色方框处的”设置”,进行相关参数设置。其他的设置不变，主要是设置”存储”,点击红色框找到相应的系统镜像文件(如图1-2),再点击”启动”虚拟机,安装相应的步骤安装linux系统。

![image001.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image001.png)
![image002.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image002.png)
<h3>2.熟悉命令</h3>
<pre>学习linux最重要的是熟悉linux常用命令.</pre>

#### 2.1磁盘管理
ls命令用于查看目录有哪些文件,ls –al作用是查看全部文件(包括隐藏文件)显示文件的详细信息(如图2-1)。

![image003.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image003.png)
cd命令用于切换当前工作目录至目标目录,cd /usr切换到usr目录(图2-2),cd ~/cd 返回home目录(图2-3),cd .. 切换到上级目录(图2-4)。

![image004.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image004.png)
![image005.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image005.png)
![image006.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image006.png)

pwd命令用于显示工作目录(图2-5)
![image007.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image007.png) 

mkdir命令用于建立新的子目录。mkdir –p 确保目录名称存在，不存在的就建一个(如图2-6)

![image008.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image008.png) 

du会显示指定的目录或文件所占用的磁盘空间(图2-7)

![image009.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image009.png) 

#### 2.2文件管理
cat命令用于查看纯文本文件(较短的) (图2-8)

![image009.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image009.png) 

more命令用于查看纯文本文件(较长的)(如图2-9)

![image010.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image010.png) 

mv命令用来为文件或目录改名、或将文件或目录移入其它位置(如图2-10)
![image011.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image011.png) 
