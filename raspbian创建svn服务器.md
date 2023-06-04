### SVN服务器创建

参考：

[Ubuntu环境搭建svn服务器 - 呆萌小二哥 - 博客园 (cnblogs.com)](https://www.cnblogs.com/daimengxiaoerge/p/10238503.html#:~:text=%E8%AE%B0%E5%BD%95%E4%B8%80%E6%AC%A1%E4%BD%BF%E7%94%A8Ubuntu%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BAsvn%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%9A%84%E8%AF%A6%E7%BB%86%E6%AD%A5%E9%AA%A4%20%E4%B8%80%E3%80%81%E6%9F%A5%E7%9C%8B%E6%98%AF%E5%90%A6%E5%B7%B2%E7%BB%8F%E5%AE%89%E8%A3%85svn%20%E5%91%BD%E4%BB%A4%EF%BC%9Asvn%20%E5%A6%82%E6%9E%9C%E6%98%BE%E7%A4%BA%E4%BB%A5%E4%B8%8B%E4%BF%A1%E6%81%AF%EF%BC%8C%E8%AF%B4%E6%98%8E%E5%B7%B2%E5%AE%89%E8%A3%85%20%E4%BA%8C%E3%80%81%E5%8D%B8%E8%BD%BD%E5%B7%B2%E5%AE%89%E8%A3%85%E7%9A%84svn,%E5%91%BD%E4%BB%A4%EF%BC%9Asudo%20apt-get%20remove%20--purge%20subversion%20%E4%B8%89%E3%80%81%E5%AE%89%E8%A3%85svn)

##### 一、查看是否已经安装svn

命令：svn



##### 二、卸载已安装的svn

命令：sudo apt-get remove --purge subversion



##### 三、安装svn

更新命令：sudo apt-get update

安装svn：sudo apt-get install subversion



###### 2.创建svn版本库

在home目录下创建svn目录，然后在svn中创建repository目录

命令：sudo mkdir -p /home/svn/repository



###### 3.修改repository文件中权限

命令：sudo chmod -R 777 /home/svn/repository



###### 4.创建版本库

命令：sudo svnadmin create /home/svn/repository



###### 5.切换当前目录到repository

命令：cd /home/svn/repository



###### 6.设置db文件的权限

命令：sudo chmod -R 777 db



###### 7.切换当前目录打破conf

命令：cd conf



###### 8.修改配置文件svnserve.conf

命令：sudo vi svnserve.conf

anon-access = none 匿名用户不可读
auth-access = write 权限用户可写

password-db = passwd 密码文件为passwd
authz-db = authz 权限文件为authz

###### 8.修改password文件，添加访问用户

命令：sudo vi passwd
新增用户格式：名字 = 密码



###### 9.给用户test增加目录权限

命令：sudo vi authz





##### 四、启动服务，并且监听81端口

切换到root权限

命令：sudo su

启动svn： sudo  svnserve -d -r /home/svn --listen-port 81

查看svn是否启动

命令：ps -ef | grep svnserve



##### 五、停止服务

命令：killall svnserve