<h1>学习linux总结</h1>
<h3>1.安装linux</h3>
先安装VirtualBOX虚拟机搭建linux系统,VirtualBOX安装完成后,在点击新建出现新建虚拟电脑,在输入虚拟的相应的名称会自动识别相应的虚拟机类型和版本,一直点击下一步,新建完成后。选中刚创建的虚拟机,点击红色方框处的”设置”,进行相关参数设置。其他的设置不变，主要是设置”存储”,点击红色框找到相应的系统镜像文件,再点击”启动”虚拟机,安装相应的步骤安装linux系统。

![image001.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image001.png)
![image002.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image002.png)
<h3>2.熟悉命令</h3>
<pre>学习linux最重要的是熟悉linux常用命令.</pre>

#### 2.1磁盘管理
ls命令用于查看目录有哪些文件,ls –al作用是查看全部文件(包括隐藏文件)显示文件的详细信息。

![image003.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image003.png)
cd命令用于切换当前工作目录至目标目录,cd /usr切换到usr目录,cd ~/cd 返回home目录,cd .. 切换到上级目录。

![image004.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image004.png)
![image005.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image005.png)
![image006.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image006.png)

pwd命令用于显示工作目录
![image007.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image007.png) 

mkdir命令用于建立新的子目录。mkdir –p 确保目录名称存在，不存在的就建一个

![image008.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image008.png) 

du会显示指定的目录或文件所占用的磁盘空间

![image009.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image009.png) 

#### 2.2文件管理
cat命令用于查看纯文本文件(较短的)

![image009.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image009.png) 

more命令用于查看纯文本文件(较长的)

![image010.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image010.png) 

mv命令用来为文件或目录改名、或将文件或目录移入其它位置

![image011.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image011.png) 

rm命令用于删除一个文件或者目录,rm –rf 强制删除当前目录下的所有文件和子目录不能恢复

![image012.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image012.png)

cp命令主要用于复制文件或目录

![image013.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image013.png)

find命令用来在指定目录下查找文件

![image014.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image014.png)

#### 3.网络通讯
ifconfig命令用于显示或设置网络设备,使用ifconfig前要先安装net-tools,命令yum –y install net-tools

![image016.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image016.png)

#### 4.安装其他组件
输入yum -y install lrzsz 安装lrzsz ,输入yum –y install wget安装wget下载组件

<h3>3.虚拟机和本机相互通讯</h3>

在进行相互通讯的前要先安装SecureCRT,然后在使用ifconfig修改虚拟机IP地址,同时打开cmd,同时使用ping输入相应的ip地址.

![image017.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image017.png)

#### 3.1网络通讯
在虚拟机和本机通讯成功后,在SecureCRT上输入rz导入mysql,tomcat,jdk.

![image018.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image018.png)

#### 3.2安装环境

##### 3.3安装mysql
1.1 安装环境
1.1.1 mysql版本
mysql版本是5.7.17(64位)
1.1.2 linux版本
Linux版本是centos 7 mini版(64位)
1.1.3 虚拟机版本
Oracle VM VirtualBox 版本 5.1.12 r112440 (Qt5.6.2)
1.2 安装步骤
1.要先创建组:
 groupadd mysql。
2.用户:
 useradd -r -g mysql mysql。
3.新建目录:
 mkdir –p /work/program。
4.将mysql解压位置自定义(如图1-1):
 tar –xzvf mysql –C /work/program,。
注:如果mysql目录下没有data目录,可以手动创建一个。
5.进入到mysql目录下:
 cd /work/program/mysql。
6.同时将所有目录和组均设为mysql:
 chown mysql:mysql -R .  。
7.进行初始化:(注:path是你安装mysql的路径)
 /path/bin/mysqld –initialize --user=mysql --datadir=/path/data --basedir=/path
 会获取到MySQL登录密码。
8.现将mysql/support-files下的my-default.cnf改名为my.cnf，拷到/etc命令如:
 cp /work/program/mysql/support-files/my-default.cnf /etc/my.cnf。
9.修改关键配置: (如图1-2)
[mysqld]
basedir = /work/program/mysql
datadir = /work/program/mysql/data
port = 3306
socket = /work/program/mysql/tmp/mysql.sock
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES 
10.创建新目录:
同时要进入mysql目录新建tmp目录 # mkdir –p tmp。
11.在mysql运行服务器程序命令:
 ./bin/mysqld_safe& 。
12.将{mysql}./support-files/mysql.server拷贝为/etc/init.d/mysql:
 cp mysql.server etc/init.d/mysql。
13.设置权限:
 chmod +x /etc/init.d/mysql。
14.把mysql注册为开机启动服务:
 chkconfig --add mysql。
15. 手动进行服务的开启:
 /etc/init.d/mysql/start。
16.进行客户端连接测试:
 ./bin/mysql/ -uroot –p。
17.需要在在my.cnf中填加:
[client]
socket = /work/program/mysql/tmp/mysql.sock。
18. 这时要求输入密码,输入完密码,mysql会要求要改掉root的密码才能操作,最后mysql就运行了(如下图1-3)
