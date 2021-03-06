.. jerry_doc documentation master file, created by
   sphinx-quickstart on Sat Oct 19 08:51:57 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


TriAquae 使用文档 
====================


TriAquae是Python语言 + Django Web框架编写的开源的服务器运维管理软件, 您可以借助TriAquae轻松实现对上万台服务器的统一管理，如批量命令执行、文件分发、主机状态监控、资产信息自动管理、运维操作审计等功能。


.. contents:: :depth: 3  
  
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

1. 安装前准备
======================

1.1. TriAquae所依赖的环境
--------------------------

.. hint::

   TriAquae支持Centos5.x 、RedHat5.x及Ubuntu 12

.. code-block:: bash
   :linenos:
   
   Python       ==> 2.75
   python-pip   ==> 1.1
   Httpd        ==> 2.2
   MySQL        ==> 5.0
   SNMP         ==> 5.4
   Django       ==> 1.5
   Rrdtool      ==> 1.47
   Shellinabox  ==> 2.10
   Paramiko     ==> 1.10.1
   sysstat
   MySQLdb
   django_admin_bootstrapped.admin.models


1.2. 获取TriAquae
--------------------

::

	# wget http://118.244.168.45:8082/TriAquae_beta.3.1.x86_64.tar.gz	

.. note::
	
	目前 TriAquae 版本更新很快,如果想下载最新版本的程序,请直接访问 http://118.244.168.45:8082 , 复制连接,并下载.	

2. 安装TriAquae
==================


2.1. 安装依赖环境
---------------------------

.. note:: CentOS

        .. code-block:: bash 

                yum install gcc gcc-c++ make sysstat nc -y
                yum install python-devel -y
                yum install net-snmp net-snmp-utils net-snmp-devel -y
                yum install mysql mysql-server mysql-devel -y
                /etc/init.d/mysqld start
        
        安装rrdtool

        .. code-block:: bash

                yum install cairo-devel libxml2-devel pango-devel pango libpng-devel -y
                yum install freetype freetype-devel libart_lgpl libart_lgpl-devel intltool -y
                yum install rrdtool rrdtool-devel -y


.. note:: Ubuntu

        .. code-block:: bash

                sudo apt-get install gcc make sysstat nc
                sudo apt-get install python-dev
                sudo apt-get install snmpd
                sudo apt-get install mysql-client mysql-server
                sudo apt-get install python-mysqldb
                sudo /etc/init.d/mysql start

        安装rrdtool
        
        .. code-block:: bash

                sudo apt-get install rrdtool

2.2. 升级 python 到2.75以上
------------------------------

::

	python -V
	sh install/python_ins.sh
	python -V
	说明：5.x系统python默认版本是2.4。安装包中自带升级python 2.75的脚本,安装完成后在次查看python版本
	

2.3.	安装TriAquae 
---------------------------

::

	tar zxf TriAquae.tar.gz
	cd TriAquae/install
	python setup.py build --prefix=	指定TriAquae安装路径，如果不指定的话，默认安装路径为/usr/local/TriAquae。
	python setup.py install		安装TriAquae到您指定的目录中


.. image:: images/startservice_01.jpg


.. note::
	
	安装程序会检测TriAquae安装的系统环境，如果有不满足要求，TriAquae会帮您自动安装这些pythone和django所需的环境，当然这是在您允许的情况下。


2.4. 配置TriAquae
---------------------------

配置数据库信息

编辑当前目录下的tri_config.py配置文件，填写数据库连接信息。

TriAquae初始化之前会将必要的信息写入到数据库中，必须在初始化之前配置好数据库和本机IP地址。

::
	
	MySQL_Name = 'TriAquae'  # Don't change this database name
	MySQL_User = 'root'	 # Your Mysql username
	MySQL_Pass = 'coral'	 # Your Mysql password, '' means no password.

.. note::
	
   修改数据库名称目前不支持,使用默认的
	

配置IP地址

::

	Tri_IP = '10.0.0.171' # your TriAquae server’s IP address


配置报警接受邮件

::
	
	SMTP_server = 'smtp.company.com' #replace it to your company smtp server
	Mail_username = 'tri_mailuser'
	Mail_password = 'tri_mailpass'


2.5. 初始化
-----------------

::

	# python setup.py init

.. hint:: 

	初始化操作会创建tri_connector用户，导入TriAquae数据库等操作

2.6. 启动TriAquae
---------------------------

::

	# cd "Your installation directory"
	# python TriAquae/sbin/tri_service.py start


2.7. 登录TriAquae
---------------------------


::

	http://<Your ip>:7000/

.. hint::

	默认初始账户：admin	
	密码：triaquae

.. tip::
	
	注意关闭 iptables

2.8. FAQ
--------------------------------

:: 
        
        启动tri_service.py时报导入错误 
        
	ImportError: libpython2.7.so.1.0: cannot open shared object file: No such file or directory
        
.. hint::

        升级为python2.7
        
:: 
        
        登陆堡垒机连接远程服务器不显示连接信息，无任何输出

.. hint:: 

        logs目录需要777权限

:: 

        执行$ sudo python tri_service.py start
   
	django.core.exceptions.ImproperlyConfigured: 
	
	Error loading MySQLdb module: libmysqlclient_r.so.15: 

	cannot open shared object file: No such file or directory
        
.. hint:: 

        访问https://pypi.python.org/simple/MySQL-python/下载合适的MySQLdb版本进行编译安装


3. 配置
===============

.. toctree::
   :maxdepth: 2

   self
   1.	启动服务 <startservice>
   2.	添加主机 <addhost>
   3.	添加用户 <adduser>
   4.	绑定远程用户与主机 <bindremote>
   5.	配置主机 <confighost>
   6.	配置SNMP监控 <snmpmonit>
   7.	配置报警 <alert>
   8.	启动自动资产管理 <autoasset>



.. Indices and tables
	==================
	* :ref:`genindex`
	* :ref:`modindex`
	* :ref:`search`

