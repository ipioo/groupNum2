# git  / git hub

## 1.创建github社区账号

### 	通过百度搜索github 进入到git社区中，创建自己的账号

## 2.创建自己的仓库

### 	点击右上角+号，选择新存储库选项，然后创建库

​	![](/home/xin/images/6.jpg)

### 3.安装本地git软件

### 		3.1.打开终端  输入命令：sudo apt-get install git

### 		3.2.验证git是否安装成功，输出命令：git version

### 		3.3.配置用户名和邮箱，输入命令：	

```
git config --global user.name "XXXX"         配置用户名，用户名为上面自己创建的github的账号
git config --global user.email  "XXXXXXXXXX"    配置邮箱，确保邮箱存在且正确
```

### 		3.4.查看是否配置成功，输入命令：git config --list

### 		3.5.配置Git的私钥和公钥.密码为空.  输入命令：

```
	ssh-keygen -t rsa  -C "用户邮箱"      注：出来需要输入的东西，直接回车
```

### 		3.6.证书已经生成成功，进入指定路径下，输入命令：

```
cd ~/.ssh/                                    ：查看是否生成成功
```

### 		3.7.打开github社区，选择头像下的设置选项中的SSH和GPC密钥被选项

​	![](/home/xin/images/7.png)

### 		3.8.看到上面的GitHub的SSH配置后,在新建一个SSH Key.

​		![](/home/xin/images/8.png)

### 		3.9.vim 打开Git的公钥证书.(在上述查看证书的文件夹下)

```
vim id_rsa.pub         
```

### 		3.10.打开证书文件，复制文件中全部的文字，到GitHub中的key中	

![](/home/xin/images/9.png)

### 		3.11.验证Git是否配置成功

```
ssh git@github.com                       ：出现下述话语，配置成功
```

![](/home/xin/images/10.png)

## 4.Git创建仓库

注：在你用户目录中创建一个文件夹，进入之后输入下面命令：

```
git init            注：初始化当前文件夹为Git本地仓库，
```

### 流程

1. 在用户目录下创建一个文件如： touch a.txt
2. 将为文件放置暂区 git add a.txt
3. 添加注释 git commit -m "注释"
4. git push origin master 将本地仓库中的暂存数据推送到远程仓库
5. 记住用户名 及密码`git config --global credential.helper store`

### 创建分支

1. git checkout -b  分支名  

2. git branch 查看分支

3. git checkout   分支名 切换分支

4. git status 查看数据状态

   ##   git常用命令

 1. ## git init -- 初始化本地版本库

 2. ## git add . -- 跟踪所有改动过的文件

 3. ## git add <file>  -- 跟踪指定的文件

 4. ## git commit -m “commit message” -- 提交所有更新过的文件

 5. ## git push origin <本地分支名>:<远程分支名>  推送本地提交数据到远程仓库指定分支

# git命令

1. ## git checkout -b 分支名    创建切换分支

2. ## git branch   查看当前所在分支

3. ## git checkout 分知名   切换分支

4. ## git merge <branch>   合并指定分支到当前分支

5. ## git fetch -a 从远程获取最新版本到本地

​      ![](/home/xin/images/11.png)

```
echo "# notebooks" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/jiaxin321/notebooks.git
git push -u origin master
```

  



xin@xin-ThinkPad-T420:~/notebooks$ ls
aaa.txt  a.txt  sss.txt  Typora.md  个人简历.md  日志

## `git push -u orgin master -f  `刷新远程分支

##  `git fetch -a  ` 是将远程主机 的最新内容拉到本地

xin@xin-ThinkPad-T420:~/notebooks$ git fetch -a
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
展开对象中: 100% (6/6), 完成.
来自 https://github.com/jiaxin321/notebooks

 * [新分支]          fpx        -> origin/fpx

##   `git merge origin/fpx  `

 * xin@xin-ThinkPad-T420:~/notebooks$   git merge origin/fpx 
Merge made by the 'recursive' strategy.
 ...244\232\347\255\226\347\256\200\345\216\206.md" | 36 ++++++++++++++++++++++
 ...244\232\347\255\226\347\256\200\345\216\206.md" | 36 ++++++++++++++++++++++
 2 files changed, 72 insertions(+)
 create mode 100644 "myFile/\351\233\267\345\244\232\347\255\226\347\256\200\345\216\206.md"
 create mode 100644 "myfile/\351\233\267\345\244\232\347\255\226\347\256\200\345\216\206.md"
xin@xin-ThinkPad-T420:~/notebooks$ ls
aaa.txt  a.txt  myfile  myFile  sss.txt  Typora.md  个人简历.md  日志
    xin@xin-ThinkPad-T420:~/notebooks$          ` git status`
位于分支 book
	未跟踪的文件:
	  （使用 "git add <文件>..." 以包含要提交的内容）
	
	aaa.txt

提交为空，但是存在尚未跟踪的文件（使用 "git add" 建立跟踪）

## 添加文件

xin@xin-ThinkPad-T420:~/notebooks$ `	git add 	`.
xin@xin-ThinkPad-T420:~/notebooks$` git commit -m '提交fpx日志文件'`
[book f90f55f] 提交fpx日志文件
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 aaa.txt

##  提交文件

xin@xin-ThinkPad-T420:~/notebooks$` git push origin book:notebooks `
对象计数中: 4, 完成.
Delta compression using up to 4 threads.
压缩对象中: 100% (4/4), 完成.
写入对象中: 100% (4/4), 517 bytes | 517.00 KiB/s, 完成.
Total 4 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/jiaxin321/notebooks.git
   078ed86..f90f55f  book -> notebooks

##  切换到`master`分支

xin@xin-ThinkPad-T420:~/notebooks$ `git checkout master `
切换到分支 'master'
您的分支领先 'origin/master' 共 1 个提交。
  （使用 "git push" 来发布您的本地提交）

## 切换到master 主分支 合并分支   `git merge book`

xin@xin-ThinkPad-T420:~/notebooks$ `git merge book `
更新 75d52b6..f90f55f
Fast-forward
 aaa.txt                                            |  0
 ...244\232\347\255\226\347\256\200\345\216\206.md" | 36 +++++++++++
 ...244\232\347\255\226\347\256\200\345\216\206.md" | 36 +++++++++++
 sss.txt                                            |  2 +
 ...270\252\344\272\272\347\256\200\345\216\206.md" | 70 ++++++++++++++++++++++
 ...270\252\344\272\272\347\256\200\345\216\206.md" | 70 ++++++++++++++++++++++
 6 files changed, 214 insertions(+)
 create mode 100644 aaa.txt
 create mode 100644 "myFile/\351\233\267\345\244\232\347\255\226\347\256\200\345\216\206.md"
 create mode 100644 "myfile/\351\233\267\345\244\232\347\255\226\347\256\200\345\216\206.md"
 create mode 100644 sss.txt
 create mode 100644 "\344\270\252\344\272\272\347\256\200\345\216\206.md"
 create mode 100644 "\346\227\245\345\277\227/\344\270\252\344\272\272\347\256\200\345\216\206.md"
xin@xin-ThinkPad-T420:~/notebooks$ git status
位于分支 master
您的分支领先 'origin/master' 共 7 个提交。
  （使用 "git push" 来发布您的本地提交）

无文件要提交，干净的工作区
xin@xin-ThinkPad-T420:~/notebooks$ git add .
xin@xin-ThinkPad-T420:~/notebooks$ git commit -m '日志合并'
位于分支 master
您的分支领先 'origin/master' 共 7 个提交。
  （使用 "git push" 来发布您的本地提交）

无文件要提交，干净的工作区

## 提交到主分支`git push origin master:master `

xin@xin-ThinkPad-T420:~/notebooks$ git push origin master:master 
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/jiaxin321/notebooks.git
   6ba04f4..f90f55f  master -> master
xin@xin-ThinkPad-T420:~/notebooks$ git staus
git：'staus' 不是一个 git 命令。参见 'git --help'。

最相似的命令是
	status
xin@xin-ThinkPad-T420:~/notebooks$ 

### 建仓库步骤

## 1. 在远程新建一个仓库

## 2. 新建文件夹 

### 3. 执行如下步骤

```
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/jiaxin321/xdh2.git
git push -u origin master
```

## 4.邀请组员并将连接发送给组员

### 5 .新建分枝  在分支内创建文件夹及文件  提交文件   从本地分支提交到远程分支

### 6. `git fetch -a  ` 是将远程主机的最新内容拉到本地

### 7.  `git merge origin/a`（把远程仓库中origin最新代码取回）依次添加

### 8 . 将本地分支内的内容提交到远程分支

### 9. 将分支内文件合并至主分支

### 10. 切换到本地主分支 将文件提交至远程主分支



## 搭建个人博客

万支 https://jiaxin321.github.io/

##  git 常用命令

https://blog.csdn.net/kunlcw/article/details/89379285

