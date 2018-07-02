# learn_git
## 1.git简介
git是什么？  

git是目前世界上最先进的分布式版本控制系统（没有之一）。
### (1) 集中式VS分布式
集中式和分布式版本控制系统有什么区别呢？
  
先说集中式版本控制系统，版本库是集中存放在中央服务器的，而干活的时候，用的都是自己的电脑，所以要先从中央服务器上取得最新的版本，然后开始干活，干完活了，再把自己的活推送给中央服务器。 
 
集中式版本控制系统最大的毛病就是必须联网才能工作。 
 
分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库，这样，你工作的是后，就不需要联网，因为版本库就在你自己的电脑上。既然每个人的电脑都有一个完整的版本库，那多个人协作呢？比方说你在自己的电脑上改了文件A，你的同事也在他的电脑上改了文件A，这试，你们俩之间只需要把各自的修改推送给对方，就可以互相看到各自的修改了。
### (2) 安装git
在Windows上使用Git，可以从Git官网直接下载安装程序，（网速慢的同学请移步国内镜像），然后按默认选项安装即可。

安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

安装完成后，还需要最后一步设置，在命令行输入：  
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。你也许会担心，如果有人故意冒充别人怎么办？这个不必担心，首先我们相信大家都是善良无知的群众，其次，真的有冒充的也是有办法可查的。
### (3) 创建版本库
什么是版本库呢？版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。  

所以，创建一个版本库非常简单，首先，选择一个合适的地方，创建一个空目录：  
```
$ mkdir learngit
$ cd learngit
```  
第二步，通过git init命令把这个目录变成Git可以管理的仓库：  
```
$ git init
```  
现在我们编写一个readme.txt文件，内容如下：  
```
Git is a version control system.
Git is free software.
```  
第一步，用命令git add告诉Git，把文件添加到仓库：  
```
$ git add readme.txt
```  
第二步，用命令git commit告诉Git，把文件提交到仓库：  
```
$ git commit -m "wrote a readme file"
```  
简单解释一下git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

## 2.版本管理
### (1) 修改文件
我们已经成功地添加并提交了一个readme.txt文件，现在，是时候继续工作了，于是，我们继续修改readme.txt文件，改成如下内容：  
```
Git is a distributed version control system.
Git is free software.
```
现在，运行git status命令看看结果：  
```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   readme.txt
no changes added to commit (use "git add" and/or "git commit -a")
```  
git status命令可以让我们时刻掌握仓库当前的状态，上面的命令输出告诉我们，readme.txt被修改过了，但还没有准备提交的修改。  
虽然Git告诉我们readme.txt被修改了，但如果能看看具体修改了什么内容，自然是很好的。比如你休假两周从国外回来，第一天上班时，已经记不清上次怎么修改的readme.txt，所以，需要用git diff这个命令看看：  
```
$ git diff readme.txt
diff --git a/readme.txt b/readme.txt
index d8036c1..013b5bc 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
\ No newline at end of file
```
### (2) 版本回退
在Git中，git log命令显示从最近到最远的提交日志：  
```
$ git log
commit f1be8eaa85d05a7aff6c76a998494578ffe8b690 (HEAD -> master)
Author: leicj <448439793@qq.com>
Date:   Mon Jul 2 15:26:40 2018 +0800
    add distributed
commit 08830415c6036a27e3f785e7de9ac4e206e4f487
Author: leicj <448439793@qq.com>
Date:   Mon Jul 2 15:21:54 2018 +0800
    wrote a readme file
```  
如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数：  
```
leich@lile-pc MINGW64 ~/learngit (master)
$ git log --pretty=oneline
f1be8eaa85d05a7aff6c76a998494578ffe8b690 (HEAD -> master) add distributed
08830415c6036a27e3f785e7de9ac4e206e4f487 wrote a readme file
```




