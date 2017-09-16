<h1>学习linux总结</h1>
<h3>1.安装linux</h3>
先安装VirtualBOX虚拟机搭建linux系统,VirtualBOX安装完成后,在点击新建出现新建虚拟电脑,在输入虚拟的相应的名称会自动识别相应的虚拟机类型和版本,一直点击下一步,新建完成后。选中刚创建的虚拟机,点击红色方框处的”设置”,进行相关参数设置。其他的设置不变，主要是设置”存储”,点击红色框找到相应的系统镜像文件,再点击”启动”虚拟机,安装相应的步骤安装linux系统。

![image001.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image001.png)
![image002.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image002.png)
<h3>2.熟悉命令</h3>
<pre>学习linux最重要的是熟悉linux常用命令.</pre>

<h4>2.1磁盘管理</h4>
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

<h4>2.2文件管理</h4>
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

<h3>3.网络通讯</h3>
ifconfig命令用于显示或设置网络设备,使用ifconfig前要先安装net-tools,命令yum –y install net-tools

![image016.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image016.png)

<h3>4.安装其他组件</h3>
输入yum -y install lrzsz 安装lrzsz ,输入yum –y install wget安装wget下载组件

<h3>5.虚拟机和本机相互通讯</h3>

在进行相互通讯的前要先安装SecureCRT,然后在使用ifconfig修改虚拟机IP地址,同时打开cmd,同时使用ping输入相应的ip地址.

![image017.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image017.png)

<h4>5.1网络通讯</h4>
在虚拟机和本机通讯成功后,在SecureCRT上输入rz导入mysql,tomcat,jdk.

![image018.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image018.png)

<h4>5.2安装环境</h4>

<h5>5.2.1安装mysql</h5>
1.要先创建组:<br/>
 groupadd mysql。<br/>
2.用户:<br/>
 useradd -r -g mysql mysql。<br/>
3.新建目录:<br/>
 mkdir –p /work/program。<br/>
4.将mysql解压位置自定义:<br/>
 tar –xzvf mysql –C /work/program,<br/>
注:如果mysql目录下没有data目录,可以手动创建一个。<br/>
5.进入到mysql目录下:<br/>
 cd /work/program/mysql。<br/>
6.同时将所有目录和组均设为mysql:<br/>
 chown mysql:mysql -R .  。<br/>
7.进行初始化:(注:path是你安装mysql的路径)<br/>
 /path/bin/mysqld –initialize --user=mysql --datadir=/path/data --basedir=/path <br/>
 会获取到MySQL登录密码。<br/>
8.现将mysql/support-files下的my-default.cnf改名为my.cnf，拷到/etc命令如:<br/>
 cp /work/program/mysql/support-files/my-default.cnf /etc/my.cnf。<br/>
9.修改关键配置:<br/>
[mysqld] <br/>
basedir = /work/program/mysql <br/>
datadir = /work/program/mysql/data <br/>
port = 3306 <br/>
socket = /work/program/mysql/tmp/mysql.sock <br/>
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES  <br/>
10.创建新目录: <br/>
同时要进入mysql目录新建tmp目录 # mkdir –p tmp。<br/>
11.在mysql运行服务器程序命令: <br/>
 ./bin/mysqld_safe& 。 <br/>
12.将{mysql}./support-files/mysql.server拷贝为/etc/init.d/mysql: <br/>
 cp mysql.server etc/init.d/mysql。 <br/>
13.设置权限: <br/>
 chmod +x /etc/init.d/mysql。<br/>
14.把mysql注册为开机启动服务:<br/>
 chkconfig --add mysql。<br/>
15. 手动进行服务的开启:<br/>
 /etc/init.d/mysql/start。<br/>
16.进行客户端连接测试: <br/>
 ./bin/mysql/ -uroot –p。 <br/>
17.需要在在my.cnf中填加: <br/>
[client] <br/>
socket = /work/program/mysql/tmp/mysql.sock。<br/>
18. 这时要求输入密码,输入完密码,mysql会要求要改掉root的密码才能操作,最后mysql就运行了<br/>

![image019.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image019.png)
![image020.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image020.png)
![image021.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image021.png)

<h5>5.2.2安装java环境</h5>
2.1 jdk版本<br/>
Jdk版本: jdk-8u121-linux-x64.tar<br/>
2.2 安装步骤<br/>
新建java文件夹# mkdir –p /usr/java/,解压到tar –xzvf jdk-8u121-linux-x64.tar.gz –C /usr/java/,回到home目录,编辑vi /etc/profile,在文件最后添加<br/>
export JAVA_HOME=/usr/java/jdk <br/>
export PATH=$JAVA_HOME/bin:$PATH <br/>
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar, <br/>
添加完后:wq保存完退出, <br/>

![image022.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image022.png)

在输入命令生效配置的java环境: <br/>
source /etc/profile,  <br/>
再输入java会跳出很多提示信息(如图2-2), 再输入java –version <br/>


![image023.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image023.png)
![image024.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image024.png)

<h5>5.2.3.安装tomcat</h5>
3.1 tomcat版本 <br/>
apache-tomcat-8.5.11.tar <br/>
3.2 安装步骤 <br/>
1.解压tomcat,命令行: <br/>
 tar -xzvf apache-tomcat-8.5.11.tar.gz -C /usr/java/  <br/>
2.将tomcat解压到/usr/java/下,重命名tomcat:  <br/>
 mv apache-tomcat-8.5.11.tar.gz tomcat,  <br/>
3.进入到/tomcat/bin/的目录,运行:  <br/>
 ./startup.sh,  <br/>
如果出现commit start,就是安装成功,在通过elinks进行访问(如图3-1):  <br/>
elinks http:localhost:8080,  <br/>

![image035.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image035.png)

<h5>5.2.4.svn安装和使用</h5>
 svn版本
 
![image036.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image036.png)

svn 版本是1.7.14

4.2 安装步骤 <br/>
1.先通过yum进行安装subversion先输入命令: <br/>
 yum install subversion <br/>
2.创建svn版本库目录:  <br/>
 mkdir –p /var/svn/svnrepos, <br/>
3.进入到conf目录,设置账户密码: <br/>
 vi passwd, <br/>
4.设置权限: <br/>
 vi authz, <br/>
5.修改svnserve.conf: <br/>
 vi svnserve.conf, <br/>
6.关闭防火墙权限: <br/>
 sudo systemctl stop firewalld.service, <br/>
7.启动svn版本库: <br/>
 svnserve –d –r /var/svn/svnrepos, <br/>
8.在windows上右键打开SVN Checkout,输入svn IP地址,点击OK,输入账户和密码,点击确定,就成功了。 <br/>

![image025.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image025.png)
![image026.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image026.png)
![image027.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image027.png)
![image028.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image028.png)
![image029.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image029.png)

<h3>6.redis安装</h3>
6.1 redis版本 <br/>
Redis 3.2.7 <br/>
6.2 安装步骤 <br/>
1.先通过rz将redis上传到linux上,在重命名redis: <br/>
 mv redis-3.2.7.tar.gz redis, <br/>
2.在新建一个文件夹: <br/>
 mkdir -p /usr/local/redis, <br/>
3.再解压到redius文件夹: <br/>
 tar –xzvf redis –C /usr/local/redis, <br/>
4.在进入redis: <br/>
 cd /usr/local/redis, <br/>
5.在通过make进行安装: <br/>
 make <br/>
最后会出现  Hint: It's a good idea to run 'make test' ;) make[1]: 离开目录“/usr/java/redis/src”,就说明安装成功了。 <br/>
6.接下来要启动redis: <br/>
 src/redis-server,  <br/>
7.使用redis客户端测试: <br/>
 src/redis-cli <br/>
 
![image037.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image037.png)
![image038.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image038.png)
![image039.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image039.png)
![image040.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image040.png)

<h3>7.PHP安装</h3>
7.1 php版本  <br/>
php7.0.16  <br/>
7.2 安装步骤  <br/>
 1.先通过yum安装epel-release,  <br/>
 yum install epel-release,  <br/>
2.再通过rpm进行安装:  <br/>
 rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm,  <br/>
3.在通过yum 进行安装:   <br/>
 yum install php70w,  <br/>
安装结果,  <br/>
4.检查php版本命令行:  <br/>
 php –v.  <br/>
 
![image041.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image041.png)
![image042.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image042.png)

<h3>8.Apache安装</h3>
8.1 apache版本 <br/>
Apache/2.4.6 (CentOS) <br/>
8.2 安装步骤  <br/>
1.先通过yum 安装httpd: <br/>
 yum install httpd, <br/>
2.在修改httpd.conf里的serverName: <br/>
 vi /etc/httpd/conf/httpd.conf, <br/>
3.在进入/var/www/html命令: <br/>
 cd /var/www/html, <br/>
4.在新建html页面, 添加一段html代码: <br/>
 vi index.html, <br/>
5.在通过elinks显示这个页面: <br/>
 elinks 10.0.50.19:80, <br/>
就可以看到这个页面了 <br/>

![image043.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image043.png)
![image044.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image044.png)
![image045.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image045.png)

<h3>9.nginx安装</h3> 
9.1 nginx版本 <br/>
nginx version: nginx/1.11.10 <br/>
9.2 安装步骤 <br/>
1.要先通过rz将nginx上传到linux,  <br/>
2.在解压: <br/>
 tar –xzvf nginx-1.11.10.tar.gz –C /usr/local/, <br/>
3.进入nginx文件夹,还要先装一些工具和库(如图8-1): <br/>
 yum –y install gcc-c++,  <br/>
4.基础模块(如图8-2):   <br/>
 yum –y install pcre-devel,  <br/>
5.安装插件(如图8-3):  <br/>
 yum –y install zlib-devel,  <br/>
6. 安装ssl功能需要openssl库: <br/>
 yum -y install openssl-devel, <br/>
7.在对nginx进行编译: <br/>
 ./configure –prefix=/usr/local/nginx,  <br/>
8.进行make编译, <br/>
9.进行make install安装, <br/>
10.在进入# cd /usr/etc/ngin/sbin, <br/>
11.再启动nginx命令: <br/>
 ./nginx, <br/>
12.通过elinks访问本地nginx结果: <br/>
elinks http://localhost, <br/>

![image046.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image046.png)
![image047.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image047.png)
![image048.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image048.png)
![image049.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image049.png)
![image050.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image050.png)
![image051.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image051.png)
![image052.png](https://github.com/gaokaomim/learn_linux/blob/master/image/image052.png)
