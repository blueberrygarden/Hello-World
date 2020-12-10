GitHub桌面版
======

## 安装Git bash

进入GitHub官网git-scm.com，下载适合自己电脑的版本并安装  
*本文中使用的是Windows64版本*

## 对git bash进行配置  
  
**1. 在本地创建一个ssh key<br/>**

    $ ssh-keygen-t rsa -C "your_email@youremail.com"
引号内需要改成你在注册GitHub的时候绑定的邮箱账号。之后会有一些简单的让你确认的操作，之后让你会提示操作路径、密码等等，一般情况下就直接按回车一路过就可以  
**2. 复制密钥**  
到他刚刚显示的默认存储位置或是自己选择的储存位置，打开该文件  
找到id_rsa.pub，用记事本打开并复制密钥，密钥以ssh-rsa开头，结尾是用户邮箱  
**3.登录到你的GitHub添加这个密匙**
打开GitHub设置界面，找到SSH and GPG keys这个选项，在网页右上角有一个添加新的SSH keys  
在title给你的密匙起一个名字，然后将复制的密匙填入框中保存即可  
之后回到你的Git bash上，然后输入下边的代码边

    $ ssh -T git@github.com
第一次绑定的时候输入上边的代码之后会提示是否continue，在输入yes后如果出现了：You've successfully authenticated, but GitHub does not provide shell access 那就说明，已经成功连上了GitHub  

**4. 接下来进行一些简单的设置**

    $ git config --global user.name "your name"
    $ git config --global user.email "your.email@gmail.com"
输入上边的代码，name最好和GitHub上边的一样，email是一定要是注册GitHub的那个邮箱地址  

## 使用git bash进行代码下载和上传  

**1. 将GitHub上的的Repository克隆到本地电脑中**  
根据个人习惯，例如将自己的文件储存在d盘之中，所以需要将git bash定位在d盘中  

    $ cd /D
    $ git clone https://github.com/blueberrygarden/How-to-use-Git-on-windows
git clone后边的网址就是你创建的Repository的网址，此时打开D盘会出现一个同名文件夹  
打开文件，可以打开其中的文档，也可以创建一个任意格式任意名称的新文档

    $ cd /D/How-to-use-Git-on-windows
此时再将git bash定位到库的文件How-to-use-Git-on-windows

    & ls
ls的作用是查看你目前所定位的文件夹中的文件，此时里面将出现README.md等内容  
**2. 创建新文档并上传到GitHub的库中**  
打开本地库的文件夹How-to-use-Git-on-windows，在其中创建一个新文档test.txt  
在git bash中输入以下代码, 并给需要上传的文档进行备注  

    $ git add test.txt
    $ git commit -m "your commits" 
然后将文档push到GitHub的库中，输入以下代码后需要先登路github，*之后就上传成功啦！*

    $ git push origin main
"main" 要与你git bash输入指令前的一串路径标识最后（）中的内容相同<br>

    ****@PC*********** MINGW64 /D/How-to-use-Git-on-windows (main)
    $ 
之后回到网页版GitHub中打开自己的库How-to-use-Git-on-windows，新的文档已经出现了
