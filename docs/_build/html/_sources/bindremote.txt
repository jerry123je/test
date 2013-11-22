绑定远程用户
==================

添加远程用户
---------------

在TriAquae administration中,点击"Remote Users".

.. image:: images/add_remoteuser_01.png
	   :scale: 80 %
 
.. note::

 在添加 remote user 时可以选择管理端哪些用户可以使用此用户执行任务.
 此功能基于用户的权限考虑,管理员可以根据需求进行设置.

.. hint::

 * 远程用户,指在远程主机既被管理主机上执行命令使用的用户.
 * 在使用时,要注意此用户需要在远程主机中存在,否则执行任务是会报错


批量添加远程用户
-----------------

在一个成熟的系统环境中,在系统中我们会针对不同的服务或功能添加多个user. 

TriAquae 可以让你方面的把这些用户添加到系统中进行使用.

在 TriAquae Administration 界面的上方我们可以找到 "Batch Add RemoteUsers"

点击按钮填出添加界面,使用很方面,只需要按照样例在空行输入要添加的用户信息,每条记录占用一行

.. image:: images/batchadd_auth_01.png


设置远程用户的认证方式
-----------------------

根据用户的安全认证设置不同,我们把它分为ssh-password 和ssh-key 两种,即密码认证和密钥认证

TriAquae 在管理或执行命令时,需要通过远程用户连接到对端客户机. 

在TriAquae Administration 界面中点击"Auth by IP and Remote Users"

.. image:: images/auth_remote_01.png
	   :scale: 80 %

.. note::

	在此添加设置前,推荐您先在服务端和客户端测试通过,注意SELinux 等服务的影响


批量添加远程用户认证
---------------------

TriAquae 允许用户批量添加远程用户的认证信息. 操作如下

在 TriAquae Administration 界面的上方我们可以找到 "Batch Add Auth_IP_User Binding"

点击按钮填出添加界面,使用很方面,只需要按照样例在空行输入要添加的用户信息,每条记录占用一行

.. image:: images/batchadd_remoteuser_01.png
	   :scale: 80 %



