---
layout: post
title: "Something about Git"
date: 2013-11-03 16:54
comments: true
categories: Git 
---
- 每次推送到github服务器要输入用户名密码的解决办法是修改.git/config 文件中的url为ssh的方式：
- git submodule
<!--more-->
    + 添加submodule: 在git仓库的根目录执行`git submodule add git@url ./dir_of_submodule`
    + 更新submodule：在git仓库的根目录执行`git submodule update`
    + 克隆带子模块的项目:
        + 克隆`git clone git@url dir_to_project`，(克隆下来的项目是空的)
        + 执行初始化子模块：`git submodule init`
        + 更新子模块：`git submodule update`


  
