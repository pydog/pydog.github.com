---
layout: post
title: "利用octopress和github page搭建个人博客"
date: 2013-03-26 10:38
comments: true
categories: octopress 

---
###基础建设###
>安装RVM和Ruby
>

	安装RVM
	curl -L https://get.rvm.io | bash -s stable --ruby

	安装Ruby
	rvm install 1.9.3
	rvm use 1.9.3
	rvm rubygems latest

运行`ruby --version`确定输出是1.9.3

<!--more-->

>配置octopress
>


	$ git clone git://github.com/imathis/octopress.git octopress
	$ cd octopress
	$ bundle install
	$ rake install

###部署到github page上###
***
	$ rake setup_github_pages

	$ rake generate

	$ rake deploy

	$ git add .

	$ git commit -m ‘your message’

	$ git push origin source

###自定义域名###
	echo ‘your-domain.com’ >> source/CNAME

###写博文###
>下面摘自geekontheway的博客
>		如果你是和别人合作博客，或者自己同时在好几个电脑上写博客，每次开始之前要做以下步骤

>		*新电脑的话要先克隆:*
			克隆博客源代码：
				`git clone -b source git@github.com:username/username.github.com.git octopress
				`
			克隆_deploy:
				`cd octopress`
				`git clone git@github.com:username/username.github.com.git _deploy `


>		*部署博客：*
			`gem install bundler`
			`bundle install`
			`rake setup_github_pages`

>		*和远程同步：*
			`cd octopress`
			`git pull origin source`
			`cd ./_deploy`
			`git pull origin master`

>		*发表博文：*
>		运行`rake new_post["you_post_tittle"]`并编辑source/_post/下对应的markdown文件

		*推送到远程服务器：*
			`git add .`
			`git commit -am "sth update"`
			`git push origin source`
			`cd _deploy`
			`git push origin master`
>		*部署：*
			运行`rake gen_deploy`部署到github page


