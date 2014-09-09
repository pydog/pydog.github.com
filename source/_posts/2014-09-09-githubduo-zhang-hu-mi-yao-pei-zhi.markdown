---
layout: post
title: "github多账户密钥配置"
date: 2014-09-09 21:54
comments: true
categories: github
---

- 使用下面的命令生成密钥
`ssh-keygen -t -rsa -C 'second@mail.com'`
默认SSH只会读取id_rsa，所以为了让SSH识别新的私钥，需要将其添加到SSH agent
`ssh-add ～/.ssh/id_rsa_second`

  
<!--more-->

- 完成以上步骤后在~/.ssh目录创建config文件，该文件用于配置私钥对应的服务器。内容如下：
```
    # Default github user(first@mail.com)
        Host github.com
        HostName github.com
        User git
        IdentityFile $HOME/.ssh/id_rsa

    #second user(second@mail.com)
        Host github-second
        HostName github.com
        User git
        IdentityFile $HOME/.ssh/id_rsa_second
```

- 配置完成后，在连接非默认帐号的github仓库时，远程库的地址要对应地做一些修改， 比如现在添加second帐号下的一个仓库test，则需要这样添加：    
`
    git remote add test git@github-second:second/test.git 
    #并非原来的git@github.com:second/test.git
`

- 注意： github根据配置文件的user.email来获取github帐号显示author信息， 所以对于多帐号用户一定要记得将user.email改为相应的email(second@mail.com)。

**本文参考自**: [多个github帐号的SSH key切换](http://justjavac.com/git/2012/04/13/multiple-ssh-keys.html)
