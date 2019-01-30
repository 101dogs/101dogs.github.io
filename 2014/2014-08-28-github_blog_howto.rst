blog 框架选择
===============================
#为什么是GitHub pages,而不是wordpress -
这货可以用\ `markdown <http://markdown.tw/>`__\ 写文（语法简单，排版没得说），专注于写文章
- git直接接管 -
超轻量级（应该甩开wordpress几条街吧，本人没学过太多web方面的知识，果断抛弃）

#使用GitHub pages `GitHub pages <https://pages.github.com/>`__\ 分为
User&Organization与Project两类，搭建blog的当然是选User&Organization，在仓库的\ **master**\ 分支工作（Project则要新建一个干净的\ **gh-pages**,
git checkout –orphan gh-pages）;

我的用户名是101dogs,用http协议进行的提交，检出操作（不要问我，为毛没得ssh_keygen之类的）

具体操作

::

   在github主站上创建 101dogs.github.io的仓库
   git clone https://github.com/101dogs/101dogs.github.io.git //克隆仓库到本地 
   cd 101dogs.github.io
   echo "101dogs' blog" > index.html  //创建主页
   git add .      //添加index.html到仓库索引                    
   git commit -m "101dogs' blog first commit" //提交到仓库
   git push -u origin master  //提交仓库到github服务器

抽根烟功夫，再去访问101dogs.github.io ^_^ #jekyll模板使用

有了\ `jekyll <http://jekyllrb.com/>`__\ 自然省力不少，搭建好这个模板系统（当然也可以不搭建，克隆个漂亮\ `github
blog <https://github.com/jekyll/jekyll/wiki/Sites>`__,），Jekyll其实就是一个文本的转换引擎，用
Markdown、Textile或者HTML写的文章等等，github后台会根据你模板中的layout将文档拼装起来，最终呈现到主页。之后就写blog吧。

Jekyll基本结构

::

   .
   ├── _config.yml
   ├── css
   │   └── main.scss
   ├── _includes
   │   ├── header.html
   │   └── head.html
   ├── index.html
   ├── _layouts
   │   ├── default.html
   │   ├── page.html
   │   └── post.html
   ├── _posts
   │   ├── 2014-08-26-aboutme.md
   │   └── 2014-08-28-github_blog_howto.md
   ├── README.md
   └── _sass
   ├── _base.scss
   ├── _layout.scss
   └── _syntax-highlighting.scss

这个是使用jekyll的默认模板搭建起来的仓库主目录结构(tree命令)

``jekyll new new_sites``

简单介绍一下他们的作用，参考\ http://jekyllrb.com/docs/configuration/\ ：

\_config.yml 设置一些站点属性，我的配置如下

::

   # Site settings
   title: 101dogs
   email: 101dogs@163.com 
   description: > # this means to ignore newlines until "baseurl:"
        Just a a blog to note techniqual tips erevrday 
   baseurl: "" # the subpath of your site, e.g. /blog/
   url: "http://yourdomain.com" # the base hostname & protocol for your site
   github_username: 101dogs

\_includes

\_layouts

这两个目录都是模板，暂时忽略，

\_posts

这个路径就是你扔博客文章的地方了，命名必须是\ **2012-02-22-artical-title.md**\ 这样的形式，（克隆别人的模板，直接把文章放到这就okay啦）

\_site

这个目录本地调试的时候，才会生成，最终从101dogs.github.io
看到的也就这个啦。这玩意不用提交。

#开始写博客

使用markdown写好的博客文章，前面加个类似这样的头，

layout：当然就是指定模板啦，

title: 博文题目

发布：

::

   git add .
   git commit -m "publish a new blog"
   git push -u origin master

#搭建本地jekyll环境

::

   apt-get install curl
   curl -L https://get.rvm.io | bash -s stable //安装rvm
   gem requirements   //安装ruby
   gem install jekyll   //安装jekyll

ps:ruby 可以改源，拜伟大的GFW所赐

::

   gem sources --remove http://rubygems.org/ 
   gem sources -a http://ruby.taobao.org/ 
   gem install jekyll

##启动jekyll server jekyll –server
这个时候，你就可以通过localhost:4000来访问了。嫌模板丑的可以调试了啊
