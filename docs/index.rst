.. jerry_doc documentation master file, created by
   sphinx-quickstart on Sat Oct 19 08:51:57 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to TriAquae's documentation!
=====================================

TriAquae 使用文档 
TriAquae是Python语言 + Django Web框架编写的开源的服务器运维管理软件, 您可以借助TriAquae轻松实现对上万台服务器的统一管理，如批量命令执行、文件分发、主机状态监控、资产信息自动管理、运维操作审计等功能。
功能介绍
主机管理
批量命令执行
批量文件传送
主机监控
主机状态监控
资产管理
主机资产自动管理
快速安装
TriAquae安装

TriAquae所依赖的环境
1. TriAquae支持Centos5.x 、RedHat5.x及Ubuntu 12
2. Python     	==> 2.6
3. python-pip  ==> 1.1
4. Httpd       ==> 2.2
5. MySQL     ==> 5.0
6. SNMP       ==> 5.4
7. Django     ==> 1.5
8. Rrdtool     ==> 1.47
9. Shellinabox ==> 2.10
10. paramiko   ==> 1.10.1
11. sysstat
12. MySQLdb
13. django_admin_bootstrapped.admin.models

不用担心，TriAquae已经帮您解决了，您可以通过一键安装配置以上环境,Oh yeah!

获取TriAquae
# wget http://118.244.168.45:8082/TriAquae.tar.gz	
安装TriAquae

2.3.1. 只需三步安装TriAquae
# python setup.py -h
TriAquae安装步骤非常简单，只需要三步就能使用TriAquae轻松管理数千台服务器
.build --prefix=	指定TriAquae安装路径，如果不指定的话，默认安装路径为/usr/local/TriAquae。检测TriAquae安装的系统环境，如果有不满足要求，TriAquae会帮您自动安装这些pythone和django所需的环境，当然这是在你允许的情况下。
.install		安装TriAquae到您指定的目录中
.init		初始化TriAquae相关操作

2.3.2. 检测系统环境
*因为TriAquae 会自行为你安装httpd, 所以安装前请务必卸载机器上已有的httpd 
yum remove httpd –y && rm –rf /etc/httpd

# tar zxf TriAquae.tar.gz
# cd TriAquae/install
# python setup.py build --prefix=/usr/local/TriAquae
自动检测系统环境，并显示出环境不符合要求的信息。这是一台新的服务器系统，。选择"y"一键解决以上问题（我们建议您所有的TriAquae依赖包都通过一键安装方式部署，尽量不要自行手动安装）。一键安装时，保证服务器能够正常上网及YUM正常使用,并使用root用户安装此软件。经过漫长的安装等待，直到所有环境都OK，提示运行'python setup.py install'


2.3.3. 安装
# python setup.py install

2.3.4. 配置TriAquae
创建数据库
mysql> create database TriAquae;
mysql> quit;
配置数据库信息
	编辑当前目录下的tri_config.py配置文件，填写数据库连接信息。TriAquae初始化之前会将必要的信息写入到数据库中，必须在初始化之前配置好数据库和本机IP地址。
#TriAquae database info
MySQL_Name = 'TriAquae'   # don’t change this one
MySQL_User = 'root'    #input your own database username
MySQL_Pass = 'triaquae' #input your own database password
配置IP地址
Tri_IP = '10.0.0.171' # your TriAquae server’s IP address
注意：修改数据库名称目前不支持,使用默认的

2.3.5. 初始化
# python setup.py init
初始化操作会创建tri_connector用户，导入TriAquae数据库等操作

2.3.6. 启动TriAquae
# cd "Your installation directory"
# python TriAquae/sbin/tri_service.py start
# /etc/init.d/httpd restart 

2.3.7. 登录TriAquae
http://localhost/
默认初始账户：admin	;密码：triaquae


配置
1.	启动服务
2.	添加主机
3.	添加用户
4.	绑定远程用户与主机
5.	配置主机
6.	配置SNMP监控
7.	配置报警
8.	启动自动资管理





Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

