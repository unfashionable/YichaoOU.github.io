---
layout: post
title: 使用bootstrap建立博客
header_keywords_abstract : false
header_image: bs.png
one_sentence: 2016 Summer Web Design 第三课
check: <span style="font-size:40px">☐</span>
todo: <span class="label label-danger">TO DO</span>
---

我们将学习的是如下这种网页布局。

![layout](/image/simple_layout.gif)

这种网页布局是由几个部分组成的，包括`导航栏`，`header`，`内容`，`边栏`，和`footer`。

<hr>

# 创建工作目录

我们先下载bootstrap和jQuery2.0，如同第一节课一样。解压缩bootstrap，将解压后的文件夹重新命名为 --- `first_blog`，或者任何你喜欢的名字。

再将jquery2.0放到`first_blog/js`文件夹下。

再新建`image`文件夹和`index.html`。

最后文件结构如下：


<pre>
	--- first_blog:
	css/  fonts/  image/  index.html  js/ 
</pre>

用sublime text打开`first blog`文件夹，开始编辑`index.html`。

# 创建导航栏

首先写下html文档的基本样子。可以直接用快捷键：**先输入`!`，再按下`TAB`键。**

{{page.todo}} 在`<head>`中引入css和js

{% highlight html %}

<head>
	#### 快捷键 link ####
	<link rel="stylesheet" href="./css/bootstrap.css">
	<link rel="stylesheet" href="./css/bootstrap-theme.css">
	#### 快捷键 script:src ####
	<script src="./js/jquery-2.0.0.js"></script>
	#### 注意jQuery一定要在bootstrap.js的前面 ####
	<script src="./js/bootstrap.js"></script>

</head>

{% endhighlight %}

{{page.todo}} 在`<body>`中，用`<div>`建立博客的框架。html网页里，div是使用最多的tag，因为`<div>`如果不定义大小的话，它不会改变网页的样子。因此，使用div可以帮助程序猿写出更易懂的code。

我们将用div把网页分成4大部分，分别是nav，header，content，和footer。

我们给div添加name属性，来描述这个div是做什么用的。并且，在结尾的div处，标明这个是什么div的结尾。例如：


{% highlight html %}

<body>

	#### 建立导航栏 ####
	<!-- Navigation bar -->
	<div name="this is navigation bar">
		
	</div>  <!-- END Navigation bar -->
	#### 注意，一定要标明这个div是什么的结尾，不然太多的结尾符很容易混 ####

	#### 下面是网站header ####
	<!-- Header -->
	<div name="this is header">	

	</div>  <!-- END Header -->

	#### 网站的主要内容 ####
	<!-- content -->
	<div name="content" >
		
	</div> <!-- END content -->

	#### 网站的底栏 ####
	<!-- footer -->
	<div name="footer">
		
	</div>  <!-- END footer -->

</body>


{% endhighlight %}

现在，我们开始创建导航栏。导航栏的语法是`<nav>`

{% highlight html %}

#### navbar navbar-default 定义了一些位置和颜色属性，没有也是可以的 ####
<nav class="navbar navbar-default">
	#### container定义了div的宽度 ####
	#### container-fluid实现了响应式的布局 ####
	<div class="containter containter-fluid">
		

		#### 此处加入Navbar的内容 ####


	</div>

</nav>

{% endhighlight %}

可以加入的内容有很多，我们只学习其中的三个：

第一个，是brand-image。这里你可以放一个博客的logo。用法是：


{% highlight html %}


<a href="#" class="navbar-brand"><img src="some_image" alt="text" style="height:50px;"></a>


{% endhighlight %}

第二个是导航按键。他们都是`<ul class="nav navbar-nav"><li><a>`的格式，如：

{% highlight html %}

#### 快捷键 ul.nav.navbar-nav.navbar-left>li*2>a[#]{link$} ####
<ul class="nav navbar-nav navbar-left">
	<li><a href="#">link1</a></li>
	<li><a href="#">link2</a></li>
</ul>


{% endhighlight %}


最后一个是导航下拉菜单。他们是`<ul class="nav navbar-nav"><li class="dropdown"><a>`的格式，如：

{% highlight html %}

#### 快捷键 ul.nav.navbar-nav.navbar-right>li.dropdown>a[#]{my links}>span.caret^+ul.dropdown-menu>li*3>a[#]{link$} ####

#### 快捷键用的是emmet插件：.表示class的名字; >表示下一级； ^表示返回上一级；*表示要多少个相同的标签；$表示自动增加数字
<ul class="nav navbar-nav navbar-right">
	<li class="dropdown">

		#### data-toggle定义了数据展现的方式 ####
		#### aria-haspopup定义了是否出现下拉菜单 ####
		#### span class="caret"是一个向下的箭头 ####

		<a href="#" data-toggle="dropdown"  aria-haspopup="true">my links <span class="caret"></span></a>
		#### 下拉菜单里的具体内容 ####
		<ul class="dropdown-menu">
			<li><a href="#">link1</a></li>
			<li><a href="#">link2</a></li>
			<li><a href="#">link3</a></li>
		</ul>
	</li>
</ul>


{% endhighlight %}

### 响应式的导航栏


在屏幕宽度较小时，我们想收起(`collapse`)导航栏。怎么实现这样的效果？我们要用到触发器(`trigger`)。导航栏收起的触发器叫`navbar-toggle`。我们还需要设定：1. 哪些是要被收起的条目；2. 哪些是收起后的样子。

- 要被收起的条目要被一个`<div>`标签所包含，具体为：


	{% highlight html %}

	<div class="navbar-collapse collapse" id="give_a_id">
	#### 被收起的条目 ####
	</div>

	{% endhighlight %}


- 收起后的样子也要被一个`<div>`标签所包含，具体为：


	{% highlight html %}

	<div class="navbar-header">
		#### 下面这个div是收起后的样子，三个icon-bar，就是三条横线 ####
		<div class="navbar-toggle collapsed" data-toggle="collapse" data-target="#mybar">
			<span class="icon-bar"></span>
			<span class="icon-bar"></span>
			<span class="icon-bar"></span>
		</div>		
		#### 这里加入不被屏幕宽度所影响的条目 ####
		#### 比如brand-image ####
		<a href="#" class="navbar-brand"><img src="some_image" alt="text" style="height:50px;"></a>
	</div>

	{% endhighlight %}



{{page.todo}} upload这个网站到github上。

使用你上节课注册的github账户，新建一个project，可以命名为`first_blog` --- 任何你喜欢的名字。

然后回到命令行，Mac是iterm，windows是git bash。使用git命令，upload：

> git init
>
> git add *
>
> git commit -m "navbar"
>
> git remote add origin https://github.com/YichaoOU/first_blog.git # paste your own url here
>
> git checkout -b gh-pages
>
> git push origin gh-pages


# 创建Header

首页的Header一般都是一张大图，再加上一些文字，比如apple.com。

{{page.todo}} 给header加图片。

首先，我们给header的div一个class名字，`<div class="myHeader">`。

然后，我们在css中给这个class加图片。在css文件夹下，新建`liyc.css`，并在header中引入你的css。

在这个css文件中输入：


{% highlight css %}

.myHeader{
	height: 650px;
	width: 100%;	
	/* background-image: linear-gradient(0deg,#023D09,#0E3312); */
	#### 一个.表示本级目录，两个.表示上一级的目录 ####
	#### 此时我们的liyc.css是在CSS文件夹下，因此要找到header.jpg必须使用.. ####
	background-image: url(../image/header.jpg);
	background-size: 100% 100%;
	color:white;  #### 与font-color一样，就是前景色的颜色 ####
}

{% endhighlight %}


{{page.todo}} 加入一些文字，设计一个好看的header。

比如：

{% highlight html %}

<div name="this is header" class="myHeader">

	<div class="container container-fluid">

		<div class="row" style="margin-top:100px;">
			<div class="col-md-2"></div>
			<div class="col-md-8" style="text-align:center;">
				<p style="margin:0px;font-size:35px;">Welcome to my site!</p>
			</div>
			<div class="col-md-2"></div>
		</div>

		<div class="row" style="margin-top:20px;">
			<div class="col-md-2"></div>
			<div class="col-md-8" style="text-align:center;">
				<p style="margin:0px;font-size:35px;">Yichao</p>
			</div>
			<div class="col-md-2"></div>
		</div>	

		<div class="row" style="margin-top:50px;">
			<div class="col-md-2"></div>
			<div class="col-md-8" style="text-align:center;">
				<img src="./image/pikachu.png" alt="" class="header-pikachu">
			</div>
			<div class="col-md-2"></div>
		</div>	

	</div>
	
</div>

{% endhighlight %}

再给我们的图片加一点特效：

{% highlight css %}

.header-pikachu{
	height:250px;
	border-width: 2px;
	border-radius: 20px;
	border-color: yellow;
	border-style: dotted;

}

{% endhighlight %}


# 创建footer

footer里放的一般都是copyright神马的，再加上一些链接。写起来很简单，比如：

{% highlight html %}

<div name="footer" style="margin-top:30px;" class="container">

	<hr> #### 加一条线，以示分割 ####
	<div class="row"> #### 用bootstrap网格系统，4-8分屏幕，左边是copyright，右边是一些链接 ####
		<div class="col-md-4">
			Copyright © 2016 Yichao. All rights reserved.
		</div>
		<div class="col-md-8 footer-nav">
			<ul>
				<li><a href="#">About me</a></li>
				<li><a href="#">Contact</a></li>
				<li><a href="#">Follow me</a></li>
				<li><a href="#">Back Top</a></li>
			</ul>
		</div>
	</div>

</div>


{% endhighlight %}

{% highlight css %}

.footer-nav{

	text-align: right;
	list-style: none;

}
.footer-nav li{
	display:inline;
	
}
.footer-nav li:not(:first-child):before{
	content: "|";
	padding:0px 10px;
}

{% endhighlight %}


# 创建内容

主页的内容模块一般都是给出几个highlight，我们可以使用ihover.css这个library。

google搜索ihover，进入他的github页面，点击src文件夹里的ihover.css，查看`RAW`文件，全选然后复制。在你的css文件夹下，新建ihover.css，将其粘贴进来。

在`<head>`中引入ihover.css。

在ihover的demo page上查看其用法，例如：


{% highlight html %}

<!-- content -->
<div name="content" class="container">
	
<div class="row" style="margin-top:30px;">
  <div class="col-xs-3">
 
    <!-- normal -->
    <div class="ih-item circle effect1"><a href="#">
        <div class="spinner"></div>
        <div class="img"><img src="./image/2.jpg" alt="img"></div>
        <div class="info">
          <div class="info-back">
            <h3>Heading here</h3>
            <p>Description goes here</p>
          </div>
        </div></a></div>
    <!-- end normal -->
 
  </div>
 
  <div class="col-xs-3">
 
    <!-- colored -->
    <div class="ih-item circle colored effect2 left_to_right"><a href="#">
        
        <div class="img"><img src="./image/5.jpg" alt="img"></div>
        <div class="info">
          <div class="info-back">
            <h3>Heading here</h3>
            <p>Description goes here</p>
          </div>
        </div></a></div>
    <!-- end colored -->
 
  </div>

  <div class="col-xs-3">
	<div class="ih-item circle effect5"><a href="#">
	        <div class="img"><img src="./image/5.jpg" alt="img"></div>
	        <div class="info">
	          <div class="info-back">
	            <h3>Heading here</h3>
	            <p>Description goes here</p>
	          </div>
	        </div></a>
	</div>
  </div>

  <div class="col-xs-3">
  	    <div class="ih-item circle effect6 scale_up"><a href="#">
        <div class="img"><img src="./image/2.jpg" alt="img"></div>
        <div class="info">
          <h3>Heading here</h3>
          <p>Description goes here</p>
        </div></a></div>


  </div>
</div>

</div>


{% endhighlight %}


到这里，我们网站的主页就完成了。


接下来我们开始写博客了。


首先，新建一个文件夹，我把它取名为`study`，你可以把你navbar中的其中一个做为文件夹的名字。

我在study下又新建了几个网页：

<pre>
	
	--- study: 
	index.html  post1.html  post2.html  post3.html

</pre>

study所对应的主页是/study/index.html，在这里我要罗列出所有的post。我可以用到`<ul><li>`的结构，比如：


{% highlight html %}

<div name="content" class="container" style="margin-top:30px;">
	<ul>
		<li><a href="./post1.html">我这是第一个post</a></li>
		<li><a href="./post2.html">我这是第二个post</a></li>
		<li><a href="./post3.html">我这是第三个post</a></li>
	</ul>
</div>

{% endhighlight %}


## 文章列表

那我们的博客的风格得一致吧，所以我们得复制粘贴相同的code到新的index.html中。

但是我们之前的主页的header太大了，所以我们需要稍微改一下header，比如：


{% highlight html %}

<!-- Header -->
<div name="this is header" class="study_header">

	<div class="container container-fluid">
		<div class="row" >
			<div class=" col-xs-8 header_box" >
				<p class="intro_text">我曾以为这就是结束</p>
			</div>
			<div class=" col-xs-4 header_box">
				<img src="../image/pikachu.png" alt="" style="height:200px">
			</div>

		</div>

	</div>
	
</div>
{% endhighlight %}


{% highlight css %}

.study_header{
    height: 250px;
    width: 100%;	
	background: linear-gradient(0deg,#023D09,#0E3312);
	color:white;	
}

.intro_text{
	font-size:30px;
}

.header_box img:hover{
	transform: scale(1.1);
	-webkit-filter: blur(4px);
}

.header_box img{
	transition: all 0.3s ease 0s;
	#### ease是一个timming function，你可以自己定义一个，见http://cubic-bezier.com/ ####
}

{% endhighlight %}

另外，由于我们在study这个category下，我们可以给navbar study这个条目加一个active class来告诉读者我们现在所在的位置。


## 写post1.html

同样，保持风格一致，你需要复制粘贴/study/index.html到post1.html中。

接下来我们创建一个跟bootstrap页面类似的边栏效果。

首先，我们把内容部分9-3分。这个大家都应该会了吧。

我们再随便加点dummy内容，例如：

{% highlight html %}

div.group#groupA>div#subgroupA$.subgroup*2>h4{Group A sub $}

<div class="group" id="groupA">
	<div id="subgroupA1" class="subgroup">
		<h4>Group A sub 1</h4>
	</div>
	<div id="subgroupA2" class="subgroup">
		<h4>Group A sub 2</h4>
	</div>
</div>

<div class="group" id="groupB">
	<div id="subgroupB1" class="subgroup">
		<h4>Group B sub 1</h4>
	</div>
	<div id="subgroupB2" class="subgroup">
		<h4>Group B sub 2</h4>
	</div>
</div>

{% endhighlight %}

{% highlight css %}

.group{
	
	height:600px;
	width:300px;
	background-color: yellow;

}

.subgroup{
    background: orange;
    width: 150px;
    height: 300px;
}


{% endhighlight %}


下面开始做边栏：

{% highlight html %}
	
	#### 加上hidden-xs hidden-sm，让我们的边栏在屏幕过小时隐藏 ####
	<div class="col-xs-3 hidden-xs hidden-sm " id="liyc_bar">


		#### 加上data-spy="affix"，让我们的边栏固定住 ####
		<ul class="nav nav-stacked"  data-spy="affix" data-offset-top="320" style="top: 30px;">

			<li><a href="#GroupA">Group A</a>

				#### nav-stacked让ul的item没有bullet ####
				<ul class="nav nav-stacked">
					<li><a href="#GroupASub1">Group A Sub 1</a></li>
					<li><a href="#GroupASub2">Group A Sub 2</a></li>
				</ul>
			</li>
			<li><a href="#GroupB">Group B</a>
			<ul class="nav nav-stacked">
				<li><a href="#GroupBSub1">Group B Sub 1</a></li>
				<li><a href="#GroupBSub2">Group B Sub 2</a></li>
			</ul>
			</li>
			<li><a href="#GroupC">Group C</a>
			<ul class="nav nav-stacked">
				<li><a href="#GroupCSub1">Group C Sub 1</a></li>
				<li><a href="#GroupCSub2">Group C Sub 2</a></li>
			</ul>			
			</li>

		</ul>

	</div>

	<script>
	$('body').scrollspy({
	    target: '#liyc_bar',

	    #### 锚定离browser最高点多少时，开始计算 ####
	    offset: 40
	});
	</script>

{% endhighlight %}


{% highlight css %}
	
#liyc_bar{
	margin-top: 20px;
}

#liyc_bar a{
	padding:2px;
}

#liyc_bar > .nav > li > a{
	font-size:20px;
}

#liyc_bar .nav  .nav>li>a{
	padding-left: 20px;
}

#liyc_bar .active > a
{

	color: #563d7c;
    text-decoration: none;          
    background-color: transparent;  
    border-left: 2px solid #563d7c;
	font-weight: bold;
}

#liyc_bar a{
	border-left: 2px solid transparent;
	font-weight: normal;
}

#liyc_bar .nav .nav>li>a{
	display:none;
}

#liyc_bar .active .nav>li>a{
	display: block;
}


{% endhighlight %}



{{page.todo}} 写post2.html。参照http://getbootstrap.com/css/，用html写出此页面。






























