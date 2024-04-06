# [如何在GitHub上面上传自己的项目/使用Github上传本地项目代码/怎样在GitHub上传自己的项目/github怎么上传一整个工程_github上传项目-CSDN博客](https://blog.csdn.net/weixin_50592077/article/details/129852095)

2 第一次上传自己的项目
2.1 下载git
官网链接，安装不要选择带中文和空格的路径，直接next就行

2.2 新建仓库
右上角+，选择New repository，给项目取名，完成得到一个地址



 复制这个地址

2.3 上传项目
选择合适的路径，在这个路径处，右键，git bash here

输入指令

git clone '你刚刚复制的网址'


出现这个界面，说明成功了，并且 你的本地文件中也会自动新建一个你项目的文件夹



 进入这个文件夹中，会发现

出现一个.git的隐藏文件夹



 这个时候不要关闭你的终端，输入：

git ls
git cd '项目名'
进入这个文件夹，在本地把你的项目文件复制到这里，比如这样



输入这个指令

git add -A


 完成后在输入这个指令

git commit -m "first commit"  
这个'first commit'是第一次提交的意思，表示这是你第一次上传你的项目，出现这个页面就表示你的项目应该上传成功了



 最后需要把你的项目传到远程库，输入下面的指令

git push -u origin main
会显示你的项目正在上传



 上传结束，就可以去github上刷新了，然后会显示你的项目上传记录

3、更新自己的项目
首先还是一样，新建一个你专门用来download-upload的文件夹，建议像我这样



 然后还是一样git bash here



然后输入以下代码

git clone '你的项目链接
'

 现在cd到这个项目的目录



 输入以下代码查看当前分支是否正确

git status


 输入以下代码将项目加入缓存中

git add * --
在输入以下代码，给自己写一个更新说明的描述'

git commit -m '


输入下面代码查看当前分支是否是main，后面的这个-l是字母L的小写，不是数字1 

git branch -l
最后输入下面代码，但是可能会弹窗，需要你输入账号密码验证

git push origin main



 当然也可以直接输入以下代码不过可能会出错，我的就出错了

git push origin master


4、建立分支，修改分支
4.1建立分支

可以直接在github网站上新建，不需要git 命令

打开你的项目，点击分支



点击新建



命名，不要空格，中文，尽量取出易于理解的名字，单词之间用下划线隔开_

类似于这种process_pems08_wx

 

 然后还是和前面一样，建立一个github文件夹，然后git bash here

然后输入以下代码

git clone '你的项目链接'
然后就会下载你的项目，下载完成后，在你的本地目录生成了一个文件夹

在git中cd到这个目录中

输入以下代码切换到你的另外一个分支中

git checkout 分支名
因为你建立一个新的分支的时候，github会自动把main分支的文件全部复制到这个分支中。而你建立新分支的目的是为了开发一个新的功能块，所以你需要把这些文件全部删除

输入以下代码，删除这个分支的所有文件

git rm ml_*
输入以下代码，记录你的操作

git commit -m "删除所有与main相关的文件，准备添加某某功能模块文件"
去复制你的文件，到当前文件夹中

复制完成后输入以下代码，将文件加入github的缓存中

git add * --
输入以下代码，记录你的操作

git commit -m "添加某某功能模块文件"
输入以下代码，提交文件上传操作

git push origin '你的分支名'
如果出错,比如

Error: src refspec master does not match any

可能会出现很多种错误，执行这个命令，确认一下分支，再次输入以下代码提交

git branch -l

git push origin '你的分支名'
这次应该提交成功了，如果再出问题，就多试几次，有时候会因为网络原因，因为github有时候被墙，有时候又没有墙，梯子有时候需要退出，总之多试几次

5、bug1
出现这个问题提示

*** Please tell me who you are. Run git config --global user.email "you@exam

很简单

git config --global user.email "邮箱"
git config --global user.name "名称
分别执行这两个代码，写上你的邮箱和你的名字，也就是nickname，执行后，这个提示就不会再出现

6、bug2
出现这个提示

git@github.com: Permission denied (publickey). Could not read from remote repository

生成ssh key

ssh-keygen -t rsa -C "邮箱"
一路回车，然后执行

ssh -v git@github.com
出现下面就没有问题

　　No more authentication methods to try.  
　　Permission denied (publickey).
执行

ssh-agent -s 
然后执行

ssh-add ~/.ssh/id_rsa
接着分别执行

ssh-agent bash
ssh-add ~/.ssh/id_rsa_name
最后运行这个，会出现一大串字符，一定要复制这串字符

cat ~/.ssh/id_rsa.pub
去你的github账户，设置，SSH and GPG keys，然后new ssh key

随便取个名，然后把你复制的这串字符粘贴进去，然后完成

再去运行

 ssh -T git@github.com
输入yes，如果看到

Hi ‘你的名字’! You've successfully authenticated, but GitHub does not provide shell access.

就说明你解决这个问题了