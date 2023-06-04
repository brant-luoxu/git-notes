### linux 快速创建FTP服务器

参考：

https://blog.csdn.net/qq_51212018/article/details/110350950



## 一、安装

sudo apt-get install vsftpd

## 二、配置VSFTPD服务器

vim /etc/vsftpd.conf

sudo service vsftpd restart



## 三、创建FTP用户

sudo useradd -m ftpuser

sudo passwd ftpuser

New password: 

Retype new password: 

passwd: password updated successfully





