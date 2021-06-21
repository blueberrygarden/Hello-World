GitHub桌面版
======

## 安装Git bash

进入GitHub官网git-scm.com，下载适合自己电脑的版本并安装  
*本文中使用的是Windows64版本*

## 对git bash进行配置  
  
**1. 在本地创建一个ssh key**

    $ ssh-keygen-t rsa -C "your_email@youremail.com"
引号内需要改成你在注册GitHub的时候绑定的邮箱账号。之后会有一些简单的让你确认的操作，之后让你会提示操作路径、密码等等，一般情况下就直接按回车一路过就可以  
**2. 复制密钥**  
到他刚刚显示的默认存储位置或是自己选择的储存位置，打开该文件，找到id_rsa.pub，用记事本打开并复制密钥，密钥以ssh-rsa开头，结尾是用户邮箱  
**3. 登录到你的GitHub添加这个密匙**  
打开GitHub设置界面，找到SSH and GPG keys这个选项，在网页右上角点击添加新的SSH keys  
在title给你的密匙起一个名字，然后将复制的密匙填入框中保存即可  
之后回到你的Git bash上，然后输入下边的代码

    $ ssh -T git@github.com
    
第一次绑定的时候输入上边的代码之后会提示是否continue，在输入yes后如果出现了：You've successfully authenticated, but GitHub does not provide shell access 那就说明，已经成功连上了GitHub  
gitlab的ssh key绑定方式类似  
**4. 接下来进行一些简单的设置**  

    github
    $ git config --global user.name "blueberrygarden"
    $ git config --global user.email "jiaojiaoyutianan@gmail.com"
输入上边的代码，name和email对应账户名称和注册邮箱

git config user.name “你的用户名”：修改你本地一个仓库的用户名
git config user.email"你的邮箱"：修改你本地一个仓库的邮箱

git config --global user.name"你的用户名"：修改全局仓库的用户名
git config --global user.email"你的邮箱"：修改全局仓库的邮箱

## 使用git bash进行代码下载和上传  

**1. 将GitHub上的的Repository克隆到本地电脑中**  
根据个人习惯，可以将自己的文件储存在d盘中，所以需要将git bash定位在d盘  

    github
    $ cd /d/git/
    $ git clone https://github.com/blueberrygarden/yourrepo.git   
git clone后边的网址就是你创建的Repository的网址，此时打开D盘会出现一个同名文件夹  
打开文件，可以打开其中的文档，也可以创建一个任意格式任意名称的新文档

    $ cd /D/git/yourrepo
此时再将git bash定位到本地仓库的文件夹

    & ls
ls的作用是查看你目前所定位的文件夹中的文件，此时里面将出现README.md等内容  
**2. 创建新文档并上传到GitHub的库中**  
打开本地库的文件夹youtrepo，在其中创建一个新文档test.txt  
在git bash中输入以下代码, 并给需要上传的文档进行备注

    $ git add test.txt
    $ git commit -m "your commits" 
然后将文档push到GitHub的库中，输入以下代码后需要先登路github，*之后就上传成功啦！*

    $ git push origin main
"main" 要与你git bash输入指令前的一串路径标识最后（）中的内容相同, 在gitlab中是master  

    ****@PC*********** MINGW64 /D/How-to-use-Git-on-windows (main) 
之后回到网页版GitHub中打开自己的库How-to-use-Git-on-windows，新的文档已经出现了

**gitlab使用说明**  
You can also upload existing files from your computer using the instructions below.  
Git global setup  

    $ git config --global user.name "Lou"
    $ git config --global user.email "9242-ujjjh@users.noreply.git.scc.kit.edu"
Create a new repository  
    
    $ git clone git@git.scc.kit.edu:ujjjh/test.git
    $ cd test
    $ touch README.md
    $ git add README.md
    $ git commit -m "add README"
    $git push -u origin master
Push an existing folder  
    
    $ cd existing_folder
    $ git init
    $ git remote add origin git@git.scc.kit.edu:ujjjh/test.git
    $ git add .
    $ git commit -m "Initial commit"
    $ git push -u origin master
Push an existing Git repository  
    
    $ cd existing_repo
    $ git remote rename origin old-origin
    $ git remote add origin git@git.scc.kit.edu:ujjjh/test.git
    $ git push -u origin --all
    $ git push -u origin --tags
  
可能遇到的问题  
1.在我们在提交git时有时候会出现错误[rejected] master -> master (fetch first)  
出现这个原因是仓库中的代码和本地中的代码不一致，需要先将仓库里的代码pull下来再push     
    
    $ git pull --rebase origin master
    $ git add . 
    $ git commit -m "your commits"
    $ git push origin master  
注意，pull前防止本地文件消失可以先将主要文件复制出去   
还可以尝试下面这种强制push的方法  
    
    $ git push -f
注意，这是强制将本地仓库上传，会覆盖原来仓库更新的内容，慎用  
2.warning: LF will be replaced by CRLF in xxx  
原因是存在符号转义问题  
windows中的换行符为 CRLF， 而在linux下的换行符为LF，所以在执行add . 时出现提示，解决办法：  

    $ git config --global core.autocrlf false
