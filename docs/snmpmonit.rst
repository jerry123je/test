配置 SNMP 监控
=====================

测试客户机 SNMP 认证
---------------------

  .. note::

	推荐在配置 SNMP 时先在命令行测试通过. 执行监控的程序在 /安装目录/TriAquae/sbin/
	
	使用 -h 查看使用方法

	.. image:: images/snmp_02.png
		   :scale: 80 %

	这里,如果您的客户机操作系统为CentOS, 推荐使用 SNMP V3, Ubuntu 可以使用 V2

  .. hint::

	如何创建 SNMP v3 用户:

	service snmpd stop

	chmod 777 net-snmp-config
	
	net-snmp-config --create-snmpv3-user -ro -a mypass -A MD5 myname

	#注意上面一句，-a是密码，而用户名跟在最后面，-A是密码加密方式，

配置SNMP 监控
----------------------

  我们可以在没台主机的配置界面下添加 SNMP 监控

  使用我们在测试时通过的配置信息

  .. image:: images/snmp_01.jpg
	     :scale: 80 %

	  
