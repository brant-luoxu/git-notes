### ubuntu搭建git服务器

参考：

[(51条消息) 在ubuntu里搭建自己的git服务器_ubuntu上搭建git服务器_景韦的博客-CSDN博客](https://blog.csdn.net/jewely/article/details/104743806)

#### 1、git服务器搭建

- 安装git：`apt install git`

- 建立git用户：`useradd git`

- 设置git用户密码：`passwd git`

- 进入`/home`目录，递归创建用户目录、仓库目录、项目目录：

  `mkdir -p` git/repository/gittest.git

- 进入仓库目录repository，初始化项目目录：`git init --bare ./gittest.git`

- 修改仓库目录repository的所有者：`chown -R git:git /home/git/repository`



#### 2、ssh密钥的生成和配置

**客户端**

在客户端命令行生成密钥对：ssh-keygen -C '输入描述文字'

会提示Enter file in which to save the key，需要确定密钥文件保存位置和名称（注：这里有坑，建议直接回车使用默认名称id_rsa，若已经存在同名文件，先备份）

接下来要求输入密码，可以不输入，如果输入了密码，那么以后每次连接都需要输入密码

在/users/[username]/.ssh/目录里生成了两个密钥文件id_rsa和id_rsa.pub

**git服务器端**

在git用户目录/home/git/下建立.ssh目录

在.ssh目录里新建一个authorized_keys文件，将在客户端生成的id_rsa.pub文件内容复制进该文件
设置全部完成，下面两条是安全措施，建议也设置

使用chown git:git[文件名或目录名]命令，修改.ssh目录和authorized_keys文件所有者

使用chmod 600/700 [文件名或目录名]命令，修改.ssh目录权限为700，authorized_keys文件权限为600

客户端连接git服务器

新建客户端一个目录，在此目录打开git客户端，连接服务器测试

git clone ssh://git@[服务器地址]:/home/git/repository/gittest.git
