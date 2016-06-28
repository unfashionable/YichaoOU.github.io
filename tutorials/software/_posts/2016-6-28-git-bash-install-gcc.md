---
layout: post
header: just_img_header
title: How to install gcc in Git Bash (Windows)

header_image: git_bash_windows.jpg
abstract: iterm is an outstanding terminal for Mac OS
source: https://docs.docker.com/opensource/project/software-req-win/
---

<span class="label label-danger"> Note: </span> `Git Bash in Windows cannot behave exactly the same as a linux bash. If you need to do the same in Windows, you may try CygWin.`

To install GCC, the trick is to install MinGW installation manager. 

1. Go to MinGW [SourceForge](http://sourceforge.net/projects/mingw/) and download the file.

2. Follow the instruction to install it.

3. When you see `MinGW Installation Manager Dialog`, click on **MSYS** in the left sidebar, you will see `mingw-developer-toolkit` in the right side panel. Now just right click on it and select `mark for installation`. 


	![dialog](/image/tutorials/minGW_manager.png)


4. In the navigation bar, select **Installation > Apply Changes**. A new dialog will appear, you want to click on **Apply**.


	![dialog2](/image/tutorials/apply_changes.png)

5. The last step is to go to Windows environment variable settings: **Control Panel > System and Security > System**. 


	![dialog3](/image/tutorials/windows_var.png) 



6. Click on **Advanced system settings**.

	![dialog3](/image/tutorials/windows_PATH.png)



7. Click on **Environment Variables**. 

	![dialog3](/image/tutorials/windows_env_var.png)

8. Double Click on **System variables > Path**. Put `;C:\MinGW\bin\` into the **Variable value**. `;` is the seperator. 


	![dialog3](/image/tutorials/windows_edit_var.png)

