###一、本地配置git，注册并将项目代码提交到GitHub 

>　　GitHub是代码托管平台，也是基于git的开源分布式版本控制系统。然而，当你登陆github官网时，它并没有为你准备一个很好的代码上传的系统，这是因为它是基于git的分布式版本管理系。那么，如何更快更有效的将本地代码上传到github呢？首先，我们需要在本地安装git，这样才能在本地环境中使用git命令行，其次是要连接到你的GitHub账户上，这样才能把你的代码文件上传上去，而每一次的更改都会形成一个版本记录，这样对团队协作是很有帮助的。  


**1.安装git**
[下载](https://github.com/git-for-windows/git/releases/tag/v2.8.1.windows.1)并在本地安装

**2.配置git**
设置自己的账户信息，windows下任意位置右键菜单在出现的菜单中选择git bash打开git命令行，使用如下命令设置信息，配置自己的用户名和用户邮箱：
```
git config --global user.name mwkang
git config --global user.email mwkang@foxmial.com
```

![配置用户名用户邮箱.png](http://upload-images.jianshu.io/upload_images/208018-f7c7c900dea9c17e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**3.创建本地ssh**
这是一种传输代码的方法，速度快又安全。SSH 是目前较可靠，专为远程登录会话和其他网络服务提供安全性的协议。在终端或cmd输入以下命令行，选择ssh-key生成路径和密码均默认直接回车跳过：
>ssh-keygen -t rsa -C "mwkang@foxmial.com"

![创建本地SSH.png](http://upload-images.jianshu.io/upload_images/208018-5427f954927dda12.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**4.将ssh配置到GitHub中**
windows系统C:\Users\自己电脑用户名\.ssh 路径下，用记事本打开id_rsa.pub，将里面的全部代码复制到github的新建SSH中，然后检验是否配置成功，复制如下代码:
>ssh -T git@github.com

到终端，验证时输入YES，然后出现如下信息：
>Warning: Permanently added the RSA host key for IP address '192.30.252.131' to the list of known hosts.

>Hi hawx1993! You've successfully authenticated, but GitHub does not provide shell access.

当出现以上信息时，说明配置成功，可以连接上GitHub

![配置成功连接到GitHub.png](http://upload-images.jianshu.io/upload_images/208018-0dda81d157d82c83.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![将ssh配置到GitHub中.png](http://upload-images.jianshu.io/upload_images/208018-f021f4ba3cbacdf1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**5.创建本地版本库**
在本地创建一个版本库
```
$ mkdir test
#test是你的文件夹的名字
$ cd test
#进入test所在目录
$ pwd
#pwd命令用于显示当前目录 
```


![创建一个本地仓库和名为README的文件.png](http://upload-images.jianshu.io/upload_images/208018-55d592c45c5188b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


通过git init命令把这个目录变成Git可以管理的仓库
```$ git init```

在github上创建一个你自己的new repository
```
mkdir test  
cd test  
git init    #initialize your git repository  
touch README  #create a file named README  
git add README    #add README to cache  
git commit -m 'first commit'  #commit your files to local repository
```

将本地的文件传送至github中
```
git remote add origin https://github.com/yourname/test.git  
git push -u origin master
```

![将文件上传到GitHub.png](http://upload-images.jianshu.io/upload_images/208018-34dd566b74e1b066.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![上传成功.png](http://upload-images.jianshu.io/upload_images/208018-432b1a52ff00bd74.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

</br>
###二、配置Maven并新建一个项目上传到GitHub
>　　Maven项目对象模型(POM)，可以通过一小段描述信息来管理项目的构建，报告和文档的软件项目管理工具。
　　Maven 除了以程序构建能力为特色之外，还提供高级项目管理工具。由于 Maven 的缺省构建规则有较高的可重用性，所以常常用两三行 Maven 构建脚本就可以构建简单的项目。由于 Maven 的面向项目的方法，许多 Apache Jakarta 项目发文时使用 Maven，而且公司项目采用 Maven 的比例在持续增长。

**1.配置java环境变量**
maven的运行需要java运行环境，所以需要确保已安装JDK，并将 “JAVA_HOME” 变量加入到 Windows 环境变量。

![配置java本地环境变量.png](http://upload-images.jianshu.io/upload_images/208018-407d8dabe2e860fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![配置path路径.png](http://upload-images.jianshu.io/upload_images/208018-e85e35de056ded0c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

运行如下代码查看java版本，若如图所示，则java已在本地配置好
>java -version

![java配置成功.png](http://upload-images.jianshu.io/upload_images/208018-2d6df0e046d32bde.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**2.本地配置maven**
[Maven官方网站下载](http://maven.apache.org/download.cgi)Maven 的 zip 文件，例如： apache-maven-3.3.9-bin.zip，将它解压到你要安装 Maven 的文件夹

![下载maven并解压到本地.png](http://upload-images.jianshu.io/upload_images/208018-b4059176e7cb6c44.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**3.配置maven环境变量**

![配置maven本地环境变量.png](http://upload-images.jianshu.io/upload_images/208018-c1d56a3609587020.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

运行如下代码查看maven版本，若如图所示，则maven在本地配置好
>mvn -v


![maven配置成功.png](http://upload-images.jianshu.io/upload_images/208018-88841a53b36b5140.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**4.安装并在IDEA中配置Maven**
安装IDEA，并在其中修改maven home路径，其下两个路径为maven本地仓库设置和路径，默认即可。

![配置Maven.png](http://upload-images.jianshu.io/upload_images/208018-cfa24bbdef431786.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![配置maven在idea中安装.png](http://upload-images.jianshu.io/upload_images/208018-b256d88cb23b2f0c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**5.新建Maven项目并提交到GitHub**
（新建项目过程在文档02中展开）
![新建Maven项目并上传GitHub.png](http://upload-images.jianshu.io/upload_images/208018-6c876ed715bf51a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![提交到GitHub.png](http://upload-images.jianshu.io/upload_images/208018-9149eddd3497d568.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###三、附：pull&push&git常用命令
**1.pull**
- 如需获取他人库中的代码，先 fork 别人的仓库，相当于拷贝一份
- 在自己的机器上 git clone 这个仓库，切换分支（也可以在 master 下），进行代码修改
>git clone https://github.com/beepony/bootstrap.git
cd bootstrap~ git checkout -b test-pr
git add . && git commit -m "test-pr"
git push origin test-pr

- 完成修改之后，回到 test-pr 分支，发起 pull request 给原仓库，让对方看到你修改的 bug
- 原仓库 review 这个 bug，如果是正确的话，就会 merge 到他自己的项目中

**2.push**
- 进入到要push的代码的目录文件夹，打开bash

![到目录文件夹下打开Bash.png](http://upload-images.jianshu.io/upload_images/208018-bc7a1672fd802087.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 初始化，系统会在本地代码库会自动创建一个.git隐藏文件，这个就是本地代码库
```git init```

![初始化.png](http://upload-images.jianshu.io/upload_images/208018-2f32b2ee9bbe5701.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![初始化后新建的本地代码库.png](http://upload-images.jianshu.io/upload_images/208018-81c9de787539e6c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 加载文件，"." 是把文件夹里面的所有文件都加载进来
```git add .```

也可以单个加载
```git add index.html,test.html```

- 提交文件，创建时间点，创建之后可以随时回到这个时间点，-m "这里的文件是注释"
```git commit -m "init commi```

可以随时查看git的状态
```git status```

![添加之后并查看状态.png](http://upload-images.jianshu.io/upload_images/208018-db67ac925f20dd44.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 可以看到有2个文件被修改了，9615个插入，没有文件删除

**3.git常用命令
- 新建代码库
```Bash
# 在当前目录新建一个Git代码库
$ git init
# 新建一个目录，将其初始化为Git代码库
$ git init [dir-name]
# 下载一个项目和它的整个代码历史
$ git clone [url] 
```
- Git配置
```Bash
# 显示当前的Git配置
$ git config --list
# 编辑Git配置文件
$ git config -e [--global]
# 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```

- 为Git增加/删除文件
```Bash
# 添加指定文件到暂存区
$ git add [file1] [file2] ...
# 添加指定目录到暂存区，包括子目录
$ git add [dir]
# 添加当前目录的所有文件到暂存区
$ git add .
# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
$ git add -p
# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...
# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]
# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
```

- 将代码提交到Git
```Bash
# 提交暂存区到仓库区
$ git commit -m [message]
# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]
# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a
# 提交时显示所有diff信息
$ git commit -v
# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]
# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
```

- Git的分支
```Bash
# 列出所有本地分支
$ git branch
# 列出所有远程分支
$ git branch -r
# 列出所有本地分支和远程分支
$ git branch -a
# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]
# 新建一个分支，并切换到该分支
$ git checkout -b [branch]
# 新建一个分支，指向指定commit
$ git branch [branch] [commit]
# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]
# 切换到指定分支，并更新工作区
$ git checkout [branch-name]
# 切换到上一个分支
$ git checkout -
# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]
# 合并指定分支到当前分支
$ git merge [branch]
# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]
# 删除分支
$ git branch -d [branch-name]
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```

- Git的标签
```Bash
# 列出所有tag
$ git tag
# 新建一个tag在当前commit
$ git tag [tag]
# 新建一个tag在指定commit
$ git tag [tag] [commit]
# 删除本地tag
$ git tag -d [tag]
# 删除远程tag
$ git push origin :refs/tags/[tagName]
```

- 查看信息
```Bash
# 显示有变更的文件
$ git status
# 显示当前分支的版本历史
$ git log
# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat
# 搜索提交历史，根据关键词
$ git log -S [keyword]
# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s
# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature
# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]
# 显示指定文件相关的每一次diff
$ git log -p [file]
# 显示过去5次提交
$ git log -5 --pretty --oneline
# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn
# 显示指定文件是什么人在什么时间修改过
$ git blame [file]
# 显示暂存区和工作区的差异
$ git diff
# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]
# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"
# 显示某次提交的元数据和内容变化
$ git show [commit]
# 显示某次提交发生变化的文件
$ git show --name-only [commit]
# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]
# 显示当前分支的最近几次提交
$ git reflog
```

- Git远程同步
```Bash
# 下载远程仓库的所有变动
$ git fetch [remote]
# 显示所有远程仓库
$ git remote -v
# 显示某个远程仓库的信息
$ git remote show [remote]
# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]
# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]
# 上传本地指定分支到远程仓库
$ git push [remote] [branch]
# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force
# 推送所有分支到远程仓库
$ git push [remote] --all
```

- 撤销与其他
```Bash
# 恢复暂存区的指定文件到工作区
$ git checkout [file]
# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]
# 恢复暂存区的所有文件到工作区
$ git checkout .
# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]
# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard
# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]
# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]
# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]
# 新建一个commit，用来撤销指定commit# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]
# 暂时将未提交的变化移除，稍后再移入
$ git stash$ git stash pop
# 生成一个可供发布的压缩包
$ git archive
```
