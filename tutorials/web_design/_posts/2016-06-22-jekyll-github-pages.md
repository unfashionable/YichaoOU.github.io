---
layout: post
title: Use GitHub Pages to Build Your Blog
header_keywords_abstract : true
header_keywords:
- Sublime Text, Ruby, Bundler & Jekyll
- Git, GitHub, GitHub Pages
- Markdown
keywords:
- Installation：ST & Bundler & Jekyll
- Setup： Git
- Use：Markdown
anchors:
- a1
- a2
- a3
header_image: github_jekyll.jpg
abstract : Github Pages is a free website server. Your free url will be your_user_name.github.io. It is pretty cool, isn't it?
---

> In this tutorial, you will:
>
> * install `sublime text` and `git bash` (for Windows user only) to build your IDE
>
> * install `ruby`
>
> * create a `GitHub` account to host your website
>
> * install `Bundler` and `Jekyll`; they are static site generator
>
> * `git clone` my jekyll theme
>
> * use `markdown` language to write your first post


## <kbd> 1. Download Sublime Text </kbd> {#a1}

[Sublime Text](https://www.sublimetext.com/) is the greatest text editor ever. However, when working through sftp, I prefer to use `NotePad++`. Because I can't find a good sftp plugin for sublime text. 

You can download a cracked version of sublime text (not working in my Mac) following [this link](http://sublimetext.iaixue.com/dl/): 

> http://sublimetext.iaixue.com/dl/



## <kbd> 2. Install Git </kbd>


<h3  data-target="#collapseOne" data-toggle="collapse">

	<span class="label label-primary">
    <span class=" glyphicon glyphicon-plus" style="-webkit-text-stroke: 3px;"></span> 
    &nbsp; What is Git ?</span>


</h3>

<div id="collapseOne" class="panel-collapse collapse panel panel-default">
      <div class="panel-body">
       Git is a version control command. In plain English, Git allows you to undo every editing. In other words, you can go back to every version that you have commited. 
      </div>
</div>


Windows users need to install Git Bash. You can download it following [this link](https://git-scm.com/downloads):

> https://git-scm.com/downloads

Mac users just need to type `git` in your terminal and it will come up an installation box if you haven't installed `git`.

Iterm is a good replacement terminal for Mac users. Please check out my other post about [iterm.]({% post_url 2016-06-25-iterm-setup %})

## <kbd> 3. Install Ruby </kbd>

For MAC users, first install brew. Paste the following line to your Terminal:

> /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Then, please install Ruby using the following command:

>  $ brew install ruby

For Windows users, please install Ruby using RubyInstaller following [this link](http://railsinstaller.org/en):

> http://railsinstaller.org/en


## <kbd> 4. Install Bundler and Jekyll </kbd> 

Now, type the following command in your terminal:

> $ gem install bundler

We will use bundler to install jekyll. To do this, you need to use a text editor to create a file named `Gemfile`. We will do this step later.





## <kbd> 5. Sign up for GitHub </kbd> {#a2}

Go to `https://github.com/` to get an account








## <kbd> 6. Git clone my Jekyll theme </kbd> 

Find a folder that you would like to work. This is typical to be `~/Document`. In the terminal, `cd` to your folder and `git clone` my repo using the following command:

> $ git clone https://github.com/YichaoOU/jekyll_theme_liyc.git

My repo has a Gemfile so you don't need to create it again. Now, we will install jekyll by typing:



> $ cd jekyll_theme_liyc
>
> $ bundle install
>
> $ bundle exec jekyll serve -w


Now, open your browser to `127.0.0.1:4000`. You should be able to see my theme. Try out some of the buttons. 


## <kbd> 7. Use MarkDown to write your first post </kbd> {#a3} 

Let's use markdown to create our first post. Inside the `MyPostFolder/_posts` folder, create a file named:

> YYYY-MM-DD-my-title.md

(Please change YYYY-MM-DD to the current date).

Now, add the following to your file:

<pre>
---
layout: post
title: Give a title
header_keywords_abstract : false
one_sentence: Use one sentence to summarize this post
header_image: Desert.jpg
---
</pre>

<span class="label label-danger">Note!</span> `header_keywords_abstract`, `one_sentence`, and `header_image` are not standard Jekyll variables. I added them myself for my convenience. 

The `header_image` is a file under `/image/` folder.








