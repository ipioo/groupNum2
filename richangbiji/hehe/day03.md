# git  / git hub

## 1. 创建github社区账号

### 	通过百度搜索github 进入到git社区中，创建自己的账号

## 2. 创建自己的仓库

### 	点击右上角+号，选择新存储库选项，然后创建库

​	![](/home/diane/桌面/Git/创建git仓库.png)

## 3.安装本地git软件

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

​	![](/home/diane/桌面/Git/上传密钥.png)

### 		3.8.看到上面的GitHub的SSH配置后,在新建一个SSH Key.

​		![](/home/diane/桌面/Git/密钥名字及密钥.png)

### 		3.9.vim 打开Git的公钥证书.(在上述查看证书的文件夹下)

```
vim id_rsa.pub         
```

### 		3.10.打开证书文件，复制文件中全部的文字，到GitHub中的key中	

​		注：无需换行![](/home/diane/桌面/Git/复制证书密钥.png)

### 		3.11.验证Git是否配置成功

```
ssh git@github.com                       ：出现下述话语，配置成功
```

![](/home/diane/桌面/Git/验证是否配置成功.png)

## 4.Git创建仓库

注：在你用户目录中创建一个文件夹，进入之后输入下面命令：

```
git init            注：初始化当前文件夹为Git本地仓库，
```

## 5. 提交流程

1. 你用户目录中创建的文件夹下创建一个txt文件 ；   

     如：touch a.txt

2. 将你创建的txt文件放入到暂区暂存；                         

      如：get add a.txt

3. 给上传的文件加一个注释；                                               

   如：get commit -m "第一次提交"

4. 将本地暂存的文件推送至远程仓库；                           

     如：git push origin master

5. 如： git config --global credential.helper store

# git常用命令

 1. ## git init -- 初始化本地版本库

 2. ## git add . -- 跟踪所有改动过的文件

 3. ## git add <file>  -- 跟踪指定的文件

 4. ## git commit -m “commit message” -- 提交所有更新过的文件

 5. ## git push origin <本地分支名>:<远程分支名>  推送本地提交数据到远程仓库指定分支



# git命令

1. ## git checkout -b 分支名    创建切换分支

2. ## git branch   查看当前所在分支

3. ## git checkout 分支名   切换分支

4. ## git merge <branch>   合并指定分支到当前分支

5. git push -u origin master -f 刷新远程分支

6. ## git fetch -a 从远程获取最新版本到本地

   

   

7. git push -u origin master -f         更新master 

![img](https://img-blog.csdnimg.cn/20190418150458890.jpg)

