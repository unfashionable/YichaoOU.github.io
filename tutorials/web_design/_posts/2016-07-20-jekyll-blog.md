---
layout: post
title: 使用jekyll建立博客
header_keywords_abstract : false
header_image: github_jekyll.jpg
one_sentence: 2016 Summer Web Design 第四课
check: <span style="font-size:40px">☐</span>
todo: <span class="label label-danger">TO DO</span>
---


如同第一节课的讲义所述，Jekyll使用html模板来建立网站，其模板就放在了`_layouts`和`_includes`两个文件夹下。

同时，jekyll使用markdown来写博客，其博客就放到了`_posts`文件夹下。所有的配置都在`_config.yml`文件中。

{{page.check}} 要在github中使用jekyll，我们先要在github中新建一个project，将其命名为`your_account_name.github.io`.

添加一下readme和license。

{{page.check}} 将新的project复制到你的文档中

> cd ~/Documents/
>
> git clone https://github.com/pokemon-liyc/pokemon-liyc.github.io.git

{{page.check}} 现在，用ST3打开你的网站文件夹，我们来新建几个文件夹，分别是：

> _layouts
>
> _includes
>
> category1/_posts + index.html
>
> css
>
> js
>
> image
>
> .gitignore
>
> Gemfile
>
> index.html
>
> _config.yml

{{page.check}} 在.gitignore中添加：_site/

{{page.check}} 在Gemfile中添加：

<pre>
source "https://rubygems.org"

gem "github-pages"
</pre>

{{page.check}} 我们现在在layouts里添加第一个HTML模板，把它叫做`default.html`：

{% highlight html %}

<html>
	<head>
		<meta charset='utf-8'>
		<meta name='viewport' content='width=device-width,initial-scale=1.0'>
		<title>{\{ page.title }}</title>
		<link rel="stylesheet" type="text/css" href="/css/bootstrap.css">
		<link rel="stylesheet" type="text/css" href="/css/liyc.css">
		<link rel="stylesheet" href="/css/bootstrap-theme.css">	
		<script type="text/javascript" src="/js/jquery2.js"></script>
		<script type="text/javascript" src="/js/bootstrap.min.js"></script>
		<!-- 方便google搜索并定义你的网站 -->
		<meta name="description" content="{\{page.description}}">
	</head>

	<body>

		<!-- Navigation bar -->
		<div name="this is navigation bar">
			{ \% include nav_bar.html %}
		</div>  <!-- END Navigation bar -->

		<!-- Header -->
		<div name="this is header">	
			{ \% if page.header == "main" %}
				{ \%include main_header.html %}
			
			{ \%  elsif page.header == "category1" %}
				{ \%include cat1_header.html %}
			
			{ \%  else %}
				{ \%include cat2_header.html %}
			{ \% endif %}
		</div>  <!-- END Header -->

		<!-- content -->
		<div name="content" >
			{\{ content }}
		</div> <!-- END content -->

		<!-- footer -->
		<div name="footer">
			{ \%include footer.html %}
		</div>  <!-- END footer -->

	</body>
</html>


{% endhighlight %}


{{page.check}} 我们现在在includes里添加`nav_bar.html`. 内容与第三节课的navbar一样。但是，现在，每次我们写一个新的博客时，就不用总是copy这个navbar的code了。这就是HTML模板的好处。

{{page.check}} 我们现在在includes里添加`main_header.html`,`cat1_header.html`,`cat2_header.html`. 这个header也跟上次课的一样。


{{page.check}} 我们现在在includes里添加`footer.html`。不用说了，还是一样的。

{{page.check}} 回到你的主页，index.html. 为了与上节课一样，我们这里还是直接copy上次的内容：

{% highlight html %}

---
layout: default
title: Everything about me
header : main

---

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


{% endhighlight %}

好，现在运行jekyll，看看效果。

> bundle exec jekyll serve -w

部署到github上：

> git add *
>
> git commit -m "my website"
>
> git push origin master

主页有了，我们现在来做文章列表。

{{page.check}} 在layouts中新建`post_list.html`.

{% highlight html %}

---
layout: default
header: category1
---

{ \% assign cat = page.url | split:'/' | last %}

{ \% for post in site.categories.[cat] %}


<div class="container container-fluid" style="margin-top:15px;margin-bottom:20px;">
	<div class="row">
		<div class="col-xs-9 list_post_box" >
			<div class="col-xs-3 ">
				<img class="img-rounded img-responsive " src="/image/{\{post.header_image}}" style="height:180px">
			</div> <!-- END image -->
			<div class="col-xs-9 abstract ">
				<div class="row date_align_bottom" >
					<div class="col-xs-8">
						<h3 style="margin-top: 0px;"><a href="{\{ post.url }}">{\{ post.title }}</a></h3>
					</div>
					<div class="col-xs-3">
						<h4 style="text-align:right;margin-bottom: 0px;"> {\{ post.date | date_to_string }}</h4>
					</div>
				</div>
				<hr style="width: 100%; color: black; height: 1px; background-color:black;margin-top: 0px;margin-bottom: 0px;" />
				<h4>{\{post.abstract}}</h4>
			</div> <!-- END abstract -->
		</div> <!-- END list post box -->
	</div> <!-- END outter row -->
</div><!--  END container -->

{\% endfor %}    

{\{content}}


{% endhighlight %}

{{page.check}} 我们要给这个文章列表配一个header，我们来编辑cat1_header.html。直接把上节课我们文章列表所使用的header复制上去即可。

{{page.check}} 接下来打开category1/index.html，你只需要写一下front matter就行了，例如：

{% highlight ruby %}
---
layout: post_list
title: post_list
---
{% endhighlight %}

{{page.check}} 这个时候，这个页面是空的，因为我们还没有添加任何post。现在，在category1/_posts/里面，添加几个post，例如, 2016-07-22-something-here.md:

{% highlight ruby %}
---
layout: post
title: post1
abstract: sdfsdfsdfsdf
header_iamge: post1.png
---
{% endhighlight %}

{{page.check}} 我们再来在layouts下添加一个模板，叫做post.html

{% highlight html %}
---
layout: default
---
<h1>{/{ page.title }}</h1>
<hr>
<div class="post">
  <div class="container container-fluid">
  	<div class="row">
  		<div class="col-xs-9">
  			{/{ content }}
  		</div>
  		<div class="col-xs-3 hidden-xs hidden-sm" id="post_sidebar">
  			{ /% include side_bar.html %}
  		</div>
  	</div>
  </div>
</div>
{% endhighlight %}


{{page.check}} 我们在includes下添加一个side_bar.html:

{% highlight html %}

{ \% assign total =  page.keywords.size|minus:1 %}
{ \% if total > 0 %}
{ \% assign i = 0 %}
	<ul class="nav nav-stacked " data-spy="affix" data-offset-top="320" style="top: 30px;">
		{ \% unless i == total %}
		
			<li ><a href="#{{page.anchors[i]}}" style="font-size:20px">  {{page.keywords[i]}} </a></li>
			{ \% if page.subkeywords[i] == "true" %}
				<ul class="nav nav-stacked">
					{ \% assign my_array = page.subkeywords[i+1] | split: "|" %}
					{ \% for item in my_array %}
						<li><a href="{/{item}}">{/{item}}</a></li>
					{ \% endfor %}
				</ul>
			{ \% endif %}
		{ \% i = i + 1 %}
		{ \% endunless %}




	</ul>
{ \% endif %}

{% endhighlight %}
 









