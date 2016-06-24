---
layout: post
title: Use GitHub Pages to Build Your Blog
header_keywords_abstract : true
keywords:
- Git
- GitHub Pages
- Bundle & Gem
- Jekyll
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
> * git clone my jekyll theme
>
> * use `markdown` language to write your first post


## <kbd> 1. Download Sublime Text </kbd> 

You can download a cracked version of sublime text following [this link](http://sublimetext.iaixue.com/dl/): 

> http://sublimetext.iaixue.com/dl/

## <kbd> 2. Download Git Bash </kbd> 

Windows users need to install Git Bash. You can download it following [this link](https://git-scm.com/downloads):

> https://git-scm.com/downloads

## <kbd> 3. Install Ruby </kbd>

For MAC users, please install Ruby using the following command:

>  $ brew install ruby

For Windows users, please install Ruby using RubyInstaller following [this link](http://railsinstaller.org/en):

> http://railsinstaller.org/en


## <kbd> 4. Install Bundler and Jekyll </kbd> 

Now, type the following command in your terminal:

> $ gem install bundler

We will use bundler to install jekyll. To do this, you need to use a text editor to create a file named `Gemfile`. We will do this step later.







## <kbd> 5. Sign up for GitHub </kbd> 

Go to `https://github.com/` to register an account








## <kbd> 6. Git clone my Jekyll theme </kbd> 

Find a folder that you would like to work. This is typical to be `~/Document`. In the terminal, `cd` to your folder and `git clone` my repo following:

> $ git clone https://github.com/YichaoOU/jekyll_theme_liyc.git

My repo has a Gemfile so you don't need to create it again. Now, we will install jekyll by typing:



> $ cd jekyll_theme_liyc
>
> $ bundle install
>
> $ bundle exec jekyll serve -w


Now, open your browser to `127.0.0.1:4000`. You should be able to see my theme.


## <kbd> 7. Use MarkDown to write your first post </kbd> 

