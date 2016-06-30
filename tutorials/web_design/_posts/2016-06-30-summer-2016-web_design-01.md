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
>
>
>
>
>
>


大家好，我叫`Jekyll`，是一个静态网页生成器(`Static site generator`)。我大哥是`Django`，一个动态网页生成器(`Dynamic website generator`)。

那我为什么是静态网页呢？因为我的内容是固定的，程序猿将我的一切都提早设定好了。而我大哥动态网页就要灵活很多，他可以根据你们不同的请求(`request`)而做出不同的响应(`response`)。

大部分动态网页都需要数据库，而这些内容，你们是看不见的，因此他们又叫网页后端开发(`back-end developer`)。相对的，网页前端开发(`front-end developer`)则是关注网页本身。如果你们在维护整个网页，不仅设计网页的样子，而且开发后端数据库，则我会把你们亲切的称为`Full-stack developer`.

1. 工欲善其事必先利其器。你们要想使用我，必须有一套非常顺手的IDE。下面我向大家介绍我的一套装备: `Sublime Text` + `Git Bash` (Win) + `Iterm` (Mac) + `Ruby` + `Bundle` + `Jekyll` + `Git`. 

	- ☐ Sublime Text可以从[这里](https://www.sublimetext.com/)下载: [https://www.sublimetext.com/](https://www.sublimetext.com/). windows用户可以下载破解版：[http://sublimetext.iaixue.com/dl/](http://sublimetext.iaixue.com/dl/)

	- Git Bash可以从这里下载：[https://git-scm.com/downloads](https://git-scm.com/downloads)

	- Iterm点击这里：[https://www.iterm2.com/](https://www.iterm2.com/)。具体如何美化Iterm，请戳[这里]({% post_url 2016-06-25-iterm-setup %})：[{% post_url 2016-06-25-iterm-setup %}]( {{site.url}} {% post_url 2016-06-25-iterm-setup %})


	- 安装Ruby。Mac用户需要从命令行开始安装，具体步骤是运行下面两行命令：(这个符号`$`表示命令行，不要输入这个符号)

	> $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	>
	> $ brew install ruby

	- 安装Ruby。Win用户需要安装RubyInstaller，可以从这里下载：[http://railsinstaller.org/en](http://railsinstaller.org/en)

	- 安装Bundle。你们需要打开命令行程序。Windows用户打开Git Bash，注意需要使用 **右键 > Run as Administrator**。Mac用户打开Iterm。

	请在命令行中运行: 

	> Windows users:
	>
	> $ gem install bundler 
	>
	> Mac users:
	>
	> $ sudo gem install bundler

	- 安装Jekyll。我们将使用bundler来安装Jekyll。

	> Windows users:
	>
	> $ cd ~/Documents
	>
	> $ notepad Gemfile

	复制如下内容到文本编辑器中，并保存，关闭。

	<pre>
	source "https://rubygems.org"

	gem "github-pages"
	</pre>

	> 然后：
	> 
	> $ bundle install


	> Mac users:
	>
	> $ cd ~/Documents
	>
	> $ nano Gemfile
	>
	> 复制相同内容，然后`ctrl + o`保存，最后`ctrl + x`关闭
	>
	> $ bundle install

	- 安装Git。Windows用户已经不用安装Git了。Mac用户只需在Iterm中运行`git`，系统便会自动提示安装过程。










