---
layout: post
title: git 常用操作（持续更新）
date: 2017-08-10
categories: blog
tags: [git,github]
description: 
---

## 1. fork 项目与 clone 项目

把其他人的项目复制到自己的仓库里的操作叫做 fork，fork 完之后，这个项目就是你自己的了。

无论是 fork 的或是自己创建的 GitHub 项目，在网站上编辑总是太麻烦了，把整个项目拷贝到自己电脑里的操作就叫做 clone。clone的操作需要用到 git 命令，那么首先电脑上得有 git 命令工具，Windows 电脑直接在 GitHub 上下载 [git-for-windows](https://git-for-windows.github.io/) 就可以了。如果想深入了解 git 的话，可以看看这本书 [Pro Git](http://iissnan.com/progit/) 。

安装完 git 后，运行 git bash，首先创建一个你需要放置 clone 的项目的文件夹，并 clone 你的项目到这个文件夹，需要用到以下命令：

`cd 路径` --- 前往你要进行下一步操作的路径

`mkdir 文件夹名` --- 创建一文件夹

`git clone 项目地址` --- 将项目 clone 到你的电脑里。

**举个例子**

> 加入在你的 GitHub 上有一个项目叫做 myProject,你的 GitHub 用户名叫做 username,你要把 myProject 项目 clone 到你的电脑 E 盘下新建的 GitHubProject 文件夹里应该怎么操作呢？

首先在你的 GitHub 页面 myProject 项目界面上会有 `Clone or Download` 的下拉按钮，点击它，你会看到 `https://github.com/username/myProject.git` 的网址，这个就是你 clone 是要用到的地址，把它复制下来。

然后打开 git bash，依次输入以下命令：

```shell
cd e:
mkdir GitHubProject
cd GitHubProject/
git clone https://github.com/username/myProject.git
```

现在打开 E 盘，在 GitHubProject 文件里，你应该能看到 myProject 文件夹，这就是你 clone 到的项目。

## 2. 本地更新项目后提交到远程

项目 clone 到本地后，当然是为了方便更新项目，更新完之后，如何把项目提交到远程呢，使得在 GitHub 网页上看到的和电脑文件夹看到的一致呢，继续接下来的操作，需要用的以下命令。

`git status` --- 查看本地项目的状态

`git add -A` --- 把你的更新添加到缓存中去，表示已经准备好提交了，`-A` 表示把你的整个项目都放到缓存中。

`git commit -m "说明"` --- 提交你的更新，引号的里的说明是简要介绍一下你都更新了些什么内容。

`git push origin master` --- 将你的更新推送到远程项目中。

**举个例子**

> 假如你在 E:\GitHubProject\myProject\ 中添加了一个 example.md 的文件，现在要把它提交到远程项目中去，要如何操作呢。

打开 git bash ,依次输入以下命令：

```shell
cd e:
cd GitHubProject
cd myProject
git add -A
git commit -m "添加example.md文件"
git push origin master
```

如此整个提交过程完成。

## 3. 如何保持 fork 别人的项目在自己的仓库里保持更新

> 假设在 E:\GitHubProject\ 文件夹中有个 otherProject 文件夹是你 fork 自其他人的项目，如何确保创建项目的人更新了项目后，你能同步他更新后的项目呢，只需要如下几步操作就可以了。

```shell
//首先确定是否建立了主项目的远程源
git remote -v
//如果里面只有你自己的两个源( fetch 和 push )，那就需要添加主项目的源
//Url 表示主项目的地址
git remote add upstream Url
//再次确定远程源，就能看到有四个源，两个前缀是 origin ，两个前缀是 upstream,前缀是 upstream 的就是主项目的远程源
git remote -v
//切换到 master 分支
git checkout master
//与主项目合并
git fetch upstream
git merge upstream/master
//推送到远程
git push origin master
```

至此，你 fork 的项目就与 源项目保持一致了。