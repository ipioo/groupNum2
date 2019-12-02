#  jekyll

![](/home/xin/images/12.png)

在Ubuntu 18.04系统上安装Jekyll的方法网址`https://ywnz.com/linuxyffq/4335.html`

![](/home/xin/images/11.png)



**简介**

Jekyll是最受欢迎的静态站点生成器之一，具有内容管理系统（CMS）中所需的所有功能，与其它数据库驱动的CMS系统不同，它主要关注性能和安全性，使用Jekyll，你可以在几秒钟内将纯文本文件转换为静态网站和博客。

![在Ubuntu 18.04系统上安装Jekyll的方法](https://ywnz.com/uploads/allimg/19/1-1Z222214429504.JPG)

Jekyll特色如下：

Jekyll很简单：你不需要了解数据库管理，评论审核或讨厌的更新安装。

适合静态内容：你可以使用Markdown，Liquid，HTML和CSS，静态站点可以在你选择的Web服务器上进行部署。

Jekyll具有博客感知功能：它可以很好地处理永久链接，类别，页面，帖子和自定义布局。

 

**一、在Ubuntu 18.04上安装Jekyll**

我们将首先将所有系统软件包更新到最新版本，然后继续安装Jekyll：

$ sudo apt-get update

### $ sudo apt-get upgrade

Jekyll需要一个包含库的Ruby开发环境，使用以下命令安装Jekyll和必需的构建工具：

$ sudo apt-get install make build-essential    `可不操作`

安装Ruby包和开发工具：

### $ sudo apt-get install ruby ruby-dev

参考：[在Ubuntu 18.04 LTS系统上安装Ruby的方法](https://ywnz.com/linuxjc/3817.html)。

### 我们现在需要指示Ruby的gem包管理器将gem放在登录用户的主目录中，在~/.bashrc或~/.zshrc下添加以下行，具体取决于你的shell：

export GEM_HOME=$HOME/gems

export PATH=$HOME/gems/bin:$PATH

现在来源.bashrc|.zshrc文件以使更改生效：

### $ source ~/.bashrc

### $ source ~/.zshrc

完成此操作后，将使用gem安装Jekyll和Bundler，这是一个用于管理Gem依赖项的工具：

### $ gem install bundler

Fetching: bundler-1.16.2.gem (100%)

Successfully installed bundler-1.16.2

Parsing documentation for bundler-1.16.2

Installing ri documentation for bundler-1.16.2

Done installing documentation for bundler after 3 seconds

1 gem installed

安装Jekyll：

### $ gem install jekyll

## 安装 jekyll

##  sudo apt-get install jekyll

**二、使用Jekyll创建一个新网站**

现在已经设置了所有必需的东西，让我们继续为Jekyll添加一个站点，为此，我们将使用命令jekyll new site，这将使用默认的Jekyll主题启动所需依赖项的bundle安装，安装成功后，你应该看到如下输出（请把xxx.com换成你的域名，比如ywnz.com）：

### $ jekyll new blog.xxx.com

http://127.0.0.1:4000/

### 测试 模板是否可用   jekyll s

Running bundle install in /home/jmutai/blog.xxx.com... 

Bundler: Don't run Bundler as root. Bundler can ask for sudo if it is needed, and installing your bundle as root will break this application for all non-root users on this

Bundler: machine.

Bundler: The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java`.

Bundler: Fetching gem metadata from https://rubygems.org/...........

Bundler: Fetching gem metadata from https://rubygems.org/.

Bundler: Resolving dependencies...

Bundler: Using public_suffix 3.0.2

Bundler: Using addressable 2.5.2

Bundler: Using bundler 1.16.2

Bundler: Using colorator 1.1.0

Bundler: Using concurrent-ruby 1.0.5

Bundler: Using eventmachine 1.2.7

Bundler: Using http_parser.rb 0.6.0

Bundler: Using em-websocket 0.5.1

Bundler: Using ffi 1.9.25

Bundler: Using forwardable-extended 2.6.0

Bundler: Using i18n 0.9.5

Bundler: Using rb-fsevent 0.10.3

Bundler: Using rb-inotify 0.9.10

Bundler: Using sass-listen 4.0.0

Bundler: Using sass 3.5.6

Bundler: Using jekyll-sass-converter 1.5.2

Bundler: Using ruby_dep 1.5.0

Bundler: Using listen 3.1.5

Bundler: Using jekyll-watch 2.0.0

Bundler: Using kramdown 1.17.0

Bundler: Using liquid 4.0.0

Bundler: Using mercenary 0.3.6

Bundler: Using pathutil 0.16.1

Bundler: Using rouge 3.1.1

Bundler: Using safe_yaml 1.0.4

Bundler: Using jekyll 3.8.3

Bundler: Fetching jekyll-feed 0.10.0

Bundler: Installing jekyll-feed 0.10.0

Bundler: Fetching jekyll-seo-tag 2.5.0

Bundler: Installing jekyll-seo-tag 2.5.0

Bundler: Fetching minima 2.5.0

Bundler: Installing minima 2.5.0

Bundler: Bundle complete! 4 Gemfile dependencies, 29 gems now installed.

Bundler: Use `bundle info [gemname]` to see where a bundled gem is installed.

New jekyll site installed in /home/jmutai/blog.xxx.com.

将使用用于创建静态站点的Jekyll源文件创建目录：

$ tree blog.xxx.com/

blog.xxx.com/

├── 404.html

├── Gemfile

├── Gemfile.lock

├── _config.yml

├── _posts

│　　└── 2019-02-22-welcome-to-jekyll.markdown

├── about.md

└── index.md

1 directory, 7 files

请注意，你必须先cd到此目录才能开始使用它：

$ cd blog.xxx.com/

Jekyll的内置轻量级Web服务器将在端口4000上提供内容，如果启用了防火墙服务，则允许访问此端口：

$ sudo ufw allow 4000

Jekyll旨在通过自动检测文件的更改来支持实时开发，并在保存更改时自动重新生成静态站点。

 

**三、启动Jekyll Web Server**

要启动Jekyll内置Web服务，请选择到站点目录并使用jekyll serve命令启动Jekyll Web服务器，然后使用要绑定的主机IP地址：

$ cd ~/blog.xxx.com

$ jekyll serve --host=178.128.164.211

执行jekyll serve命令时，Jekyll将解析配置并将内容文件推送到名为_site的目录中，然后它提供此_site目录中的内容：

$ ls -1 _site/

404.html

about

assets

feed.xml

index.html

jekyll

应该得到如下输出：

Configuration file: /home/jmutai/blog.xxx.com/_config.yml

Source: /home/jmutai/blog.xxx.com

Destination:/home/jmutai/blog.xxx.com/_site

Incremental build: disabled. Enable with --incremental

Generating... 

done in 0.372 seconds.

Auto-regeneration: enabled for '/home/jmutai/blog.xxx.com'

Server address: http://178.128.164.211:4000/

Server running... press ctrl-c to stop.

当保存对帖子或页面的更改时，Jekyll还会在~/blog.xxx.com目录中监视新的更改，它将自动重建静态站点，将所有站点帖子放在_posts目录下。

## http://jekyllthemes.org/page3/ 



修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
xin@xin-ThinkPad-T420:~/1234$ git checkout -- a.txt...
error: pathspec 'a.txt...' did not match any file(s) known to git.
xin@xin-ThinkPad-T420:~/1234$ git add/rm a.txt...
git：'add/rm' 不是一个 git 命令。参见 'git --help'。
xin@xin-ThinkPad-T420:~/1234$ git rm a.txt...
fatal: 路径规格 'a.txt...' 未匹配任何文件
xin@xin-ThinkPad-T420:~/1234$ cd
xin@xin-ThinkPad-T420:~$ cd 1234
xin@xin-ThinkPad-T420:~/1234$ jekyll s
Configuration file: /home/xin/1234/_config.yml
            Source: /home/xin/1234
       Destination: /home/xin/1234/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 0.44 seconds.
 Auto-regeneration: enabled for '/home/xin/1234'
Configuration file: /home/xin/1234/_config.yml
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
^Cxin@xin-ThinkPad-T420:~/1234$ git init
已初始化空的 Git 仓库于 /home/xin/1234/.git/
xin@xin-ThinkPad-T420:~/1234$ git add .
xin@xin-ThinkPad-T420:~/1234$ git status
位于分支 master

尚无提交

要提交的变更：
  （使用 "git rm --cached <文件>..." 以取消暂存）

	新文件：   .DS_Store
	新文件：   .gitignore
	新文件：   404.html
	新文件：   ChinaREADME.md
	新文件：   Gemfile
	新文件：   Gemfile.lock
	新文件：   LICENSE
	新文件：   README.md
	新文件：   _config.yml
	新文件：   _includes/foot.html
	新文件：   _includes/head.html
	新文件：   _includes/pagination.html
	新文件：   _includes/signoff.html
	新文件：   _layouts/blog.html
	新文件：   _layouts/default.html
	新文件：   _posts/git/2017-03-07-githubyaunchengjiami.md
	新文件：   _posts/git/2017-07-16-gitignore.md
	新文件：   "_posts/\344\271\246\347\261\215/1970-01-01-bookindex.md"
	新文件：   "_posts/\344\271\246\347\261\215/2017-06-20-santibook.md"
	新文件：   "_posts/\344\271\246\347\261\215/2017-07-03-waerdenghu.md"
	新文件：   "_posts/\344\271\246\347\261\215/2017-07-09-meilideshijie.md"
	新文件：   "_posts/\344\271\246\347\261\215/2017-6-27-sikaobook.md"
	新文件：   "_posts/\344\271\246\347\261\215/2017-6-27-xuanhuanzuole.md"
	新文件：   "_posts/\350\264\237\350\275\275\345\235\207\350\241\241/2017-07-30-memcacheandredis.md"
	新文件：   about.md
	新文件：   archives/index.html
	新文件：   book/index.html
	新文件：   feed.xml
	新文件：   index.html
	新文件：   road/index.html
	新文件：   search/.DS_Store
	新文件：   search/cb-search.json
	新文件：   search/js/cb-search.js
	新文件：   style/favicons/favicon.ico
	新文件：   style/images/bg-ico.png
	新文件：   style/images/logo-liberxue.png
	新文件：   style/style-liberxue.css
	新文件：   tags/index.html
	新文件：   thumbnails/.DS_Store
	新文件：   thumbnails/01.gif
	新文件：   thumbnails/02.gif
	新文件：   thumbnails/03.gif
	新文件：   thumbnails/04.gif
	新文件：   thumbnails/404.png
	新文件：   thumbnails/archives.png
	新文件：   thumbnails/blog.png
	新文件：   thumbnails/tags.png
	新文件：   thumbnails/ui.jpg

xin@xin-ThinkPad-T420:~/1234$ git commit -m "个人博客"
[master （根提交） f37e0f3] 个人博客
 48 files changed, 4460 insertions(+)
 create mode 100644 .DS_Store
 create mode 100644 .gitignore
 create mode 100755 404.html
 create mode 100644 ChinaREADME.md
 create mode 100755 Gemfile
 create mode 100755 Gemfile.lock
 create mode 100755 LICENSE
 create mode 100644 README.md
 create mode 100755 _config.yml
 create mode 100644 _includes/foot.html
 create mode 100755 _includes/head.html
 create mode 100755 _includes/pagination.html
 create mode 100755 _includes/signoff.html
 create mode 100644 _layouts/blog.html
 create mode 100755 _layouts/default.html
 create mode 100644 _posts/git/2017-03-07-githubyaunchengjiami.md
 create mode 100644 _posts/git/2017-07-16-gitignore.md
 create mode 100644 "_posts/\344\271\246\347\261\215/1970-01-01-bookindex.md"
 create mode 100644 "_posts/\344\271\246\347\261\215/2017-06-20-santibook.md"
 create mode 100644 "_posts/\344\271\246\347\261\215/2017-07-03-waerdenghu.md"
 create mode 100644 "_posts/\344\271\246\347\261\215/2017-07-09-meilideshijie.md"
 create mode 100644 "_posts/\344\271\246\347\261\215/2017-6-27-sikaobook.md"
 create mode 100644 "_posts/\344\271\246\347\261\215/2017-6-27-xuanhuanzuole.md"
 create mode 100644 "_posts/\350\264\237\350\275\275\345\235\207\350\241\241/2017-07-30-memcacheandredis.md"
 create mode 100755 about.md
 create mode 100755 archives/index.html
 create mode 100755 book/index.html
 create mode 100755 feed.xml
 create mode 100755 index.html
 create mode 100755 road/index.html
 create mode 100644 search/.DS_Store
 create mode 100755 search/cb-search.json
 create mode 100755 search/js/cb-search.js
 create mode 100644 style/favicons/favicon.ico
 create mode 100644 style/images/bg-ico.png
 create mode 100644 style/images/logo-liberxue.png
 create mode 100644 style/style-liberxue.css
 create mode 100644 tags/index.html
 create mode 100644 thumbnails/.DS_Store
 create mode 100644 thumbnails/01.gif
 create mode 100644 thumbnails/02.gif
 create mode 100644 thumbnails/03.gif
 create mode 100644 thumbnails/04.gif
 create mode 100644 thumbnails/404.png
 create mode 100644 thumbnails/archives.png
 create mode 100644 thumbnails/blog.png
 create mode 100644 thumbnails/tags.png
 create mode 100644 thumbnails/ui.jpg
xin@xin-ThinkPad-T420:~/1234$ git remote add origin https://github.com/jiaxin321/jiaxin321.github.io.git
xin@xin-ThinkPad-T420:~/1234$ git push origin master
对象计数中: 66, 完成.
Delta compression using up to 4 threads.
压缩对象中: 100% (59/59), 完成.
写入对象中: 100% (66/66), 2.42 MiB | 1.24 MiB/s, 完成.
Total 66 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), done.
To https://github.com/jiaxin321/jiaxin321.github.io.git

 * [new branch]      master -> master
xin@xin-ThinkPad-T420:~/1234$ 