---
layout: post
title: 如何使用Jekyll并在GitHub Pages上发布自己的网站
header_keywords_abstract : false
header_image: octojekyll.png
keywords:
- Installation：ST & Bundler & Jekyll
- Setup： Git
- Use：Markdown
one_sentence: 2016 Summer Web Design 第一课
check: <span style="font-size:40px">☐</span>
todo: <span class="label label-danger">TO DO</span>
---

> 在第一节课中，我们将学习：
>
> * 如何安装Jekyll
>
> * Jekyll的目录结构
>
> * Git的几个基本命令
>
> * Jekyll的变量
>
> * markdown几个常用的语法
>
> * 在github上发布自己的网站
>
>
>


大家好，我叫`Jekyll`，是一个静态网页生成器(`Static site generator`)。我大哥是`Django`，一个动态网页生成器(`Dynamic website generator`)。

那我为什么是静态网页呢？因为我的内容是固定的，程序猿将我的一切都提早设定好了。而我大哥动态网页就要灵活很多，他可以根据你们不同的请求(`request`)而做出不同的响应(`response`)。

大部分动态网页都需要数据库，而这些内容，你们是看不见的，因此他们又叫网页后端开发(`back-end developer`)。相对的，网页前端开发(`front-end developer`)则是关注网页本身。如果你们在维护整个网页，不仅设计网页的样子，而且开发后端数据库，则我会把你们亲切的称为`Full-stack developer`.

<hr>

工欲善其事必先利其器。你们要想使用我，必须有一套非常顺手的IDE。下面我向大家介绍我的一套装备: `Sublime Text` + `Git Bash` (Win) + `Iterm` (Mac) + `Ruby` + `Bundle` + `Jekyll` + `Git`. 我给大家准备了to do list，你们每安装完成一件，就请在checkbox中打钩。

{{page.check}} **安装Sublime Text**

请点击这个网址下载: [https://www.sublimetext.com/](https://www.sublimetext.com/). Windows用户可以下载破解版：[http://sublimetext.iaixue.com/dl/](http://sublimetext.iaixue.com/dl/)

{{page.check}} **安装命令行工具**

Windows用户请下载Git Bash：[https://git-scm.com/downloads](https://git-scm.com/downloads)

Mac用户请下载Iterm：[https://www.iterm2.com/](https://www.iterm2.com/)。具体如何美化Iterm，请戳[这里]({% post_url 2016-06-25-iterm-setup %})：[{% post_url 2016-06-25-iterm-setup %}]( {{site.url}} {% post_url 2016-06-25-iterm-setup %})

{{page.check}} **安装Ruby, Bundle和Jekyll**


**Mac用户**打开命令行程序（iterm），分别运行下面的命令：(这个符号`$`表示命令行，不要输入这个符号)

> $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
>
> $ brew install ruby
>
> $ sudo gem install bundler
>
> $ cd ~/Documents
>
> $ nano Gemfile

复制如下内容到文本编辑器中，并保存，关闭。
<pre>source "https://rubygems.org"
gem "github-pages"</pre>

> `ctrl + o`保存，最后`ctrl + x`关闭
>
> $ bundle install
>
> $ git <span style="color:blue">  #系统会自动提示安装过程 </span>



**Win用户**需要安装RubyInstaller，可以从这里下载：[http://railsinstaller.org/en](http://railsinstaller.org/en)

安装Bundle。你们需要打开Git Bash,注意要使用 **右键 > Run as Administrator**。

请在命令行中运行: 


> $ gem install bundler 
>	
> $ cd ~/Documents
>
> $ notepad Gemfile

复制如下内容到文本编辑器中，并保存，关闭。
<pre>source "https://rubygems.org"
gem "github-pages"</pre>


> $ bundle install

<hr>

你们安装成功了么？我是基于Ruby编程语言建立的。我主要有两个command：

> `bundle exec jekyll new Give_a_website_name`
>
> cd Give_a_website_name
>
> `bundle exec jekyll serve -w`
>

`bundler`是一个Ruby的软件管理工具。牛大哥说，要站在巨人的肩膀上。相同的，我也是基于很多软件包的，因此，有一个友好的软件管理工具，能帮我们自动解决各种软件之间的依赖性(`dependency`)。

> 所以，每次运行我时，都要用`bundle exec jekyll`

`new`和`serve`是我自身的两个命令。`new`的意思是，新建一个站点；`serve`的意思是，打开网站服务器，这样你就可以使用浏览器查看网页了。想要终止服务器运行，直接在命令行界面下，按下`ctrl + c`.

很简单，对不对？下面你们来试着建立第一个网站吧？在命令行下运行：

> bundle exec jekyll new my_first_jekyll
>
> cd my_first_jekyll
>
> bundle exec jekyll serve -w

好，使用你们的浏览器打开 `127.0.0.1:4000`，就可以查看网站了。

使用`ctrl + c`退出服务。

<hr>

下面，来熟悉一下我的目录结构：(*表示必须的结构)

<pre>

my_first_jekyll/				# 根目录，就是你的网站名字
├── _config.yml*				# 网站参数
├── _includes*					# 网页结构的分解，HTML
│   ├── footer.html
│   ├── head.html
│   ├── header.html
│   ├── icon-github.html
│   ├── icon-github.svg
│   ├── icon-twitter.html
│   └── icon-twitter.svg
├── _layouts*					# 网页的模板
│   ├── default.html
│   ├── page.html
│   └── post.html
├── _posts*						# 你的文章
│   └── 2016-07-03-welcome-to-jekyll.markdown
├── _sass						# sass，是一种CSS的升级版，我们不涉及
│   ├── _base.scss
│   ├── _layout.scss
│   └── _syntax-highlighting.scss
├── _site						# 自动生成的静态网页
│   ├── about
│   │   └── index.html
│   ├── css
│   │   └── main.css
│   ├── feed.xml
│   ├── index.html
│   └── jekyll
│       └── update
│           └── 2016
│               └── 07
│                   └── 03
│                       └── welcome-to-jekyll.html
├── about.md  					# 一个markdown文档
├── css* 						# CSS
│   └── main.scss
├── feed.xml
└── index.html*					# 主页

13 directories, 24 files

</pre>

一会儿我还会再次回顾这个目录结构。

<hr>

下面，用Sublime text打开my_first_jekyll文件夹，点击index.html，我们来看看HTML文档长什么样子。

{% highlight html %}

---
layout: default
---

<div class="home">

  <h1 class="page-heading">Posts</h1>

  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>

  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>

</div>



{% endhighlight %}

html是布局语言，这种语言的特点就是有头有尾，而布局的结构则是由一个一个标签(`tag`)的嵌套形成的。例如，`<h1>`和`</h1>`就组成了一个头尾结构。`<h1>`表示的是一级标题，如同<span style="color:blue">MS Word</span>中的一级标题一样，会展现出比较大的字体。

{{page.todo}}下面我们把line 
7的post改成: Your Name's Post，这里输入中文也可以。刷新页面，我们看看效果。

OK，我们先有一个对于HTML的大概印象。下节课再细说HTML。

<hr>

{{page.check}} **写一个Post**

在`_post`文件夹下，新建一个文件，命名为`YYYY-MM-DD-your-file-name.md`。不用起很长的名字，让自己认识就行。

在开头输入：(当你输入时，请去掉h1标签和花括号中的空格)

<pre>
---
layout: post
title: 这是写这篇文章的名字

---


< h1> 我的题目是：{ { page.title } }</h1>

</pre>


这个以`---`为标签的内容叫做front matter。任何写有front matter的文件都会被Jekyll执行并放到`_site`文件夹中。

保存，刷新你的网站，你是否看到了主页上又增加了一点内容呢？

<hr>

{{page.check}} **学习markdown**

其实，我们可以使用一个很简单的方法来代替`<h1>`标签，那就是markdown。

我们再回来编辑我们的post，删除`<h1>`标签，在这一行最前面输入`#`。再回来刷新页面，你们看到了什么？是不是没有变化？因为`<h1>`与`#`是等效的。你们可以再试试`###`？是不是字体变小了？

{{page.todo}} 请分别用一、二、三、四、五级标题，写出你今天吃的食物

例如：

> `#` 一个包子
>
> `##` 一个包子
>
> `###` 一个包子
>
> `####` 一个包子
>
> `#####` 一个包子

其实，我们的食物是同一级别的，我们也许更喜欢用列表的方式呈现出来，在markdown中，你可以这样做:

>我今天吃了：
>
>`-` 一个包子
>
>`-` 一个包子
>
>`-` 一个包子

{{page.todo}} 请用markdown list罗列出5个属于欧盟的国家

markdown中还有一种常用的格式，叫做blockquote. 这个格式的特点就是文字有了一点底色，再加上最前面的一个深灰色竖条。

> `>` 这样使用blockquote
>
> `>`
>
> `>` 这样使他们在不同的两行


{{page.todo}} 请用markdown blockquote写出你的座右铭

插入图片也是很常用的功能，在markdown中，插入图片非常简单它包括三部分:`![图片名字](图片地址)`。

下面我新建一个image文件夹，里面有一个图片叫small.png，我如何插入图片呢？ 

> `![any_name](/image/small.png)`


{{page.todo}} 请下载五个你最喜欢的电影海报，并将它们保存在image文件夹下，使用markdown插入图片，并在图片上面，用一级标题写下电影的名字

插入链接与插入图片类似，他们的语法是：`[链接名字](链接地址)`。例如：

> `[点击这里](http://google.com)`

{{page.todo}} 请将电影海报上的title改成电影IMDB的链接

现在我们学习最后一个知识点，加粗和斜体：

> `*斜体*`
>
> `**加粗**`
>
> `***加粗并斜体***`

更多markdown语法，请看这里：[
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet](
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

<hr>

{{page.check}} 建立第一个Github Project Page

下面，你们要注册一个Github账号，[https://github.com/](https://github.com/)

注册完成后，新建一个**repo**，把他命名为`2016_summer_web_design`，然后点击Create repository.

接下来，我们就要把已经创建好的网站上传到github上。

现在我们回到命令行，输入如下命令:

> git init
>
> git add *
>
> git commit -m "2016 summer, I create my first Jekyll website"
>
> git remote add origin https://github.com/YichaoOU/web_test.git # paste your own url here
>
> git checkout -b gh-pages
>
> git push origin gh-pages
>
> 输入你们的用户名和密码

现在，你们就可以在输入：your_username.github.io/2016_summer_web_design, 查看你们的网站了。

是不是发现网站的样子很诡异？这是因为没有css的原因。

用sublime text打开`_config.yml`，修改一下`baseurl`, 将其变成：

> baseurl: "/2016_summer_web_design"

然后再将我们更改的文件上传到github上：

> git add *
>
> git commit -m "fix CSS bug"
> 
> git push origin gh-pages

将网页刷新一下，你是否看到了变化？

好，第一节课就到这里，我们回顾一下。我们首先学习了网页的结构，我们知道了bootstrap是现在最流行的网页框架。我们配置了网页开发的IDE，学习了jekyll，markdown和github。并且，我们还使用了Github project pages。以后，我们还要使用github user pages。

Jekyll是我们这个课程的重点，但是第一节课并没有深入的讲解jekyll，是因为大家需要有一定的HTML和CSS基础才能够使用Jekyll。下节课，我们将边学习html和css，边学习bootstrap。




