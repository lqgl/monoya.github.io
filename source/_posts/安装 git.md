---
title: 安装Git
date: 2020-10-21
updated:
tags:
 - Git
 - Windows
categories: Git
keywords: 'Windows,Git,安装Git'
description: 安装Git
top_img: https://raw.githubusercontent.com/lqgl/repo/main/img/top_img.jpg
cover: https://raw.githubusercontent.com/lqgl/repo/main/img/20201217230926.png
---
# 安装 Git
## 访问 git 官网，下载 git

[git官网](https://git-scm.com/)

![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201021194051425.png)

## 安装 git 
下载完成后，双击安装包进行安装，之后一直点击“下一步”就可以完成安装了。

## 配置身份
配置你的身份，这样在提交代码时，git 就知道是谁提交的了。命令如下：
![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201021195207295.png)
```bash
 git config --global user.name "Monoya"
 git config --global user.email "948735627@qq.com"
```
查看是否配置成功，使用去除名字或邮箱地址的相同命令进行验证
![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201021195312525.png)
```bash
git config --global user.name
git config --global user.email
```