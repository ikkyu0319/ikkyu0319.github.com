---
layout: post
title: "How To:升级Mac OS X上的GIT"
date: 2014-08-13 21:49
comments: true
keywords: octopress,github,blog
description: 通过网络几篇文章整理的mac平台上基于github的安装octopress大致全面的教程。
categories: git
---
[Github][]
[Github]: http://github.com
<br>

   
   在MacOSX下使用Homebrew或其它方式安装最新版本的GIT后，往往并不能使用，系统默认调用的依旧还是比较旧的版本，原因是已经通过XCode等方式安装过git，且它们的路径优先级较高。

　 下面假设你已经通过Homebrew的brew install git成功安装了GIT，但系统默认使用的还是旧版本。

##1. 检查系统默认调用的是否是通过Homebrew安装的最新版本

   Homebrew安装的GIT会被软链接到/usr/local/bin目录下，所以如果你使用which git看到的结果不是/usr/local/bin/git，那么你就需要通过后面的方法修改以便能够默认使用你所安装版本的GIT。
   
    安装brew:
    curl -L http://github.com/mxcl/homebrew/tarball/master | tar xz –strip 1 -C /usr/local
    
    export PATH=/usr/local/bin:$PATH

安装成功后通过`brew install`查看brew版本
    


##2. 移除系统自带的版本
   如果which git返回的结果是/usr/bin/git，说明你可能通过XCode安装了其自带的GIT，其版本一般都比较低，需要移除。

    cd /usr/bin
    sudo mkdir backup-git-apple
    sudo mv git* backup-git-apple



##3. 移除可能存在的其它版本
   如果which git返回的结果是/usr/local/git/bin/git，则表示可能是你曾经使用git-osx-installer或其它方式安装过GIT，检查系统环境变量PATH可能还包含形如/usr/local/git/bin的路径。
   
    sudo rm -rf /usr/local/git
    sudo rm /etc/paths.d/git
    sudo rm /etc/manpaths.d/git
   
   
   
   最后，重启终端，再次检查which git及git version。  
   
   
   
  