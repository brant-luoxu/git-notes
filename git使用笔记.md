## Git 操作笔记

### 一、简单分支管理

- #### 1、查看本地分支

  - ##### git branch

- #### 2、查看远程分支

  - ##### git branch -r

- #### 3、查看所有分支

  - ##### git branch -a

- #### 4、创建本地新分支

  - ##### git branch [branch name]

- #### 5、切换新分支

  - ##### git checkout [branch name]

- #### 6、创建分支同时也切换分支

  - ##### git checkout -b [branch name]

- #### 7、本地分支与远程分支关联

  - ##### git branch --set-upstream-to=origin/branchName

- #### 8、推送本地新分支到远程仓库

  - ##### git push origin HEAD:refs/for/[branch name]

- #### 9、在远程开好分支，本地直接拉下来

  - ##### git checkout -b feature-branch origin/feature-branch

- #### 10、本地开好分支，推送到远程

  - ##### git checkout -b branchName

  - ##### git push --set-upstream origin HEAD:refs/for/reomote-branchName

- #### 11、取消刚才的合并

  - ##### 彻底删除commitID之后所做的改动，代码也一起回退回来了。

    - ##### git reset --hard HEAD~

  - ##### 删除commitID之后的提交记录log，代码的改动还在

    - ##### git reset --soft HEAD~

- #### 12、查询提交历史

  - ##### git log --pretty=oneline

  

### 二、 常用Git 操作

- #### 1、创建+切换分支

  - ##### git checkout -b [local branch name] 

- #### 2、推送分支到Git远程仓库

  - ##### git push origin HEAD:[branch name]

- #### 3、删除本地分支

  - ##### git branch -d [branch name]

- #### 4、删除远程分支

  - ##### git push origin --delete [branch name]

  

### 三、Git切换并提交本地代码到新分支

- #### 1、checkout -切换到新分支

  - ##### git checkout [branch name]

- #### 2、add -添加要地需要提交的代码

  - ##### git add .

- #### 3、commit -提交代码到本地仓库

  - ##### git commit -m "提交代码的注释内容"

- #### 4、pull -拉取最新代码

  - ##### git pull 

- #### 5、push -推送本地代码到远程仓库

  - ##### git push origin HEAD:refs/for/[branch name]

### 四、Git 删除远程分支及tag

- #### 1、删除远程分支

  - ##### git push origin --delete branchName

- #### 2、删除tag

  - ##### git push origin --delete tag tagName

- #### 3、重命名远程分支

  - ##### 删除远程分支：

    - ##### git push --delete origin branchName

  - ##### 重命名本地分支：

    - ##### git branch -m oldName newName

  - ##### 推送本地分支：

    - ##### git push origin HEAD:branchName(newName)

### 五、添加删除Tag

- #### 1、打印所有标签

  - ##### git tag

- #### 2、打印符合检索条件的标签

  - ##### git tag -l <版本号>

  - ###### 如 git tag -l 1.*.* 为搜索一级版本为1的版本

- #### 3、查看对应标签状态

  - ##### git checkout <版本号>

- #### 4、创建带附注标签

  - ##### git tag -a <版本号> -m "<备注信息>"

- #### 5、添加特定commit标签，使用该commit对应的SHA值即可

  - ##### git tag -a <版本号> <SHA值> -m "<备注信息>"

- #### 6、推送本地标签到远程库

  - ##### git push origin --tags

  - ##### git push origin <版本号>

- #### 7、删除远和仓库的标签

  - ##### git push origin --delete <版本号>


### 五、本地分支与远程分支关联与解除关联

- #### 1、查看本地分支与远程分支的映射关系

  - ##### git branch -vv

- #### 2、建立当前分支与远程分支的映射关系:

  - ##### 如果本地新建了一个分支 branch_name，但是在远程没有

    - ##### git push --set-upstream origin HEAD:feature

    - ##### 将本地分支与远程分支关联 ，远程也会新建一个分支 feature

  - ##### 如果远程有一个分支feature，需要将本地分支feature与远程分支feature/add_order关联起来

    - ##### git branch -u origin/feature

- #### 3、撤销本地分支与远程分支的映射关系

  - ##### git branch --unset-upstream






git cherry pick

gitignore

git clone ssh://git@192.168.50.129:/home/git/repository/gittest.git

git clone ssh://git@192.168.50.129:/home/git/gitrepo/remote.git

