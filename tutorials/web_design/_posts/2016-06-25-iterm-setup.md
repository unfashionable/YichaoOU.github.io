---
layout: post
header: just_img_header
title: The best appearance setting for iterm

header_image: iterm.jpg
keywords:
- 1. Download iterm
- 2. Download solarized theme
- 3. Adjust Preference
- 4. install Oh My Zsh
anchors:
- a1
- a2
- a3
- a4
abstract: iterm is an outstanding terminal for Mac OS
---

> In this tutorial, you will:
>
> * install `iterm`
>
> * install `solarized theme`
>
> * adjust iterm `preference`
>
> * install `Oh My Zsh`


#  ![liyc image](/image/my_iterm_theme.png) {#my_first_image}

## <kbd> 1. Download iterm </kbd> {#a1}

To download iterm, click [this link](https://www.iterm2.com/):

> https://www.iterm2.com/

You will get a zip file when you finish downloading. Unzip the file and copy `iterm.app` to your `Application` folder.

## <kbd> 2. Download solarized theme </kbd> {#a2}

Go to [this website](http://ethanschoonover.com/solarized) to download the theme:

> http://ethanschoonover.com/solarized

![theme](/image/solarized.png)

You will again get a zip file. Upzip it. 

## <kbd> 3. Adjust Preference </kbd> {#a3}

Use this hotkey to open perference <span class="label label-primary"> command + , </span>

Now, let's create a new profile. Click on the `profile` tab and follow the steps below:

![steps123](/image/iterm_create_profile.png)

Then, import the solarized theme. Go to `Colors` tab and click on `Load Presets ---> import`.

![color](/image/iterm_color.png)

Select the file `Solarized Dark.itermcolors`.

![theme](/image/iterm_solarized.png)

Then, load the solarized theme by selecting `Load Presets ---> Solarized Dark`

![theme2](/image/iterm_load_theme.png)

Finally, let's change the transparency and window size. Go to the `window` tab.

![window](/image/iterm_window.png)

## <kbd> 4. install Oh My Zsh </kbd> {#a4}

Restart your `iterm` and copy and paste the following line to your iterm and hit `return`.

> sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

Here you go. You should get a similar appearance like my [first image](#my_first_image).  

Added, iterm2 cheetsheet [https://gist.github.com/helger/3070258](https://gist.github.com/helger/3070258) 
