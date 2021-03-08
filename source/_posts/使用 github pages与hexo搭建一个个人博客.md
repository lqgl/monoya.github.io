---
title: 使用 github pages与hexo搭建个人博客
date: 2020-12-13
updated:
tags:
 - Github
 - Hexo
categories: Blog
keywords: 'Github,Hexo'
description: 使用 github pages + hexo 搭建博客
top_img: https://raw.githubusercontent.com/lqgl/repo/main/img/top_img.jpg
cover: https://raw.githubusercontent.com/lqgl/repo/main/img/cover.png
---

# 使用 github pages与hexo搭建个人博客

## 安装 git与node.js

## 安装hexo

### 全局安装 hexo
```cmd
npm install hexo-cli -g
```

![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201213171607021.png)

验证安装结果：
```
hexo -v
```

![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201213171742218.png)

## 在github上创建并设置远程库

注册登录略过，不会的请自行百度。

## 初始化 Hexo

创建一个文件夹用于存放hexo。然后右键该文件夹使用![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201213172009186.png)

```undefined
 npm install hexo --save
```

初始化hexo基础配置文件。初始化时间比较长，不用急，等完成后输入

```kotlin
hexo init
```

初始化hexo。这个命令和git 仓库命令相似。意思一样都是初始化。
 接着输入

```undefined
npm install
```

配置node。然后输入

```undefined
hexo g
```

加载hexo基础html、css、js等文件。
 在这完成后等于已经在本地创建了一个网页，想查看的话，输入

```undefined
hexo s
```

然后相当于开启了一个本地的服务器，会提示你拷贝url到浏览器。

http://localhost:4000

## 更换主题

### 这里更换的是 butterfly 主题
```bash
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```

### 应用主題

  修改站点配置文件_config.yml，把主題改为butterfly

```YAML
theme: butterfly
```
### 安装插件
如果你沒有 pug 以及 stylus 的渲染器，请下载安装：
```
npm install hexo-renderer-pug hexo-renderer-stylus --save
```
### 升级建议
把主题文件夹中的 _config.yml 复製到 Hexo 根目录里，同时重新命名为 _config.butterfly.yml。

以后只需要在 _config.butterfly.yml进行配置就行。

Hexo会自动合併主题中的_config.yml和 _config.butterfly.yml里的配置，如果存在同名配置，会使用_config.butterfly.yml的配置，其优先度较高。
### 修改内容
内容较多建议参考官方文档
https://hexo.io/zh-cn/docs/configuration.html
修改完之后，可以重新执行hexo s在浏览器查看效果。并确认无误，包括以后需要添加文章，或者更新主题等，都建议先在本地查看无误再远程部署。
根_config.yml文件中
```
# Site
title: 网站标题
subtitle: 副标题
description: 个人签名
author: 姓名
language: zh-CN
timezone:
```
### 注意：
这里有几个坑需要注意一下：
>1、所有的配置“:”符号后面都要带空格，否则执行本地测试直接失败。
2、language是设置语言。zh-CN是中文。
3、如果设置zh-CN后仍出现乱码问题。需要更改文件的字符编码集为UTF-8,方法很多具体，就不详细介绍了。

### 要在根config.yml中配置自己的远程仓库地址
```
deploy:
  type: git
  repo: https://github.com/lqgl/monoya.github.io.git
  branch: main
```
## 将博客部署到 github pages上

### 安装部署工具（方便以后更新）
```
npm install hexo-deployer-git --save
```
### 初始化本地仓库：
```
git init
```
### 连接远程仓库：
如果是第一次使用git，在使用git的时候会提示输入用户名和密码，用户名是自己的注册邮箱。
git remote add origin https://github.com/lqgl/monoya.github.io.git

### 发布hexo到github pages
```
hexo clean && hexo g && hexo d
```
### 推送到远程仓库（github）
这里建议创建一个新的分支hexo，用于管理hexo文件。提交的的时候只提交hexo网站html、css、等源文件。而默认的main分支用来部署更新项目
1) 创建并切换到新建分支：
```
git checkout -b hexo
```
2) 添加文件到本地仓库
```
git add .
```
3)提交声明
```
git commit -m '内容'
```
4) 将分支推送到远程仓库：
```
git push origin hexo
```
## 进阶-绑定域名
###  购买域名,添加解析
具体请百度，或发工单
### 登录github
找到项目，设置setting，找到GitHub Pages
![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201213200436249.png)

### 写入注册的域名
在`main`分支下的创建一个`CNAME`文件
![](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20201213200610626.png)

如果延迟的话，可能解析立马不会生效。需要等会儿才能看到。

>以前也有搭建过博客，但因为没有坚持下来，总忘记，所以整理一下，以后方便查看。所有的流程都在这里。

## 参考文档
[使用hexo+github免费搭建个人博客网站超详细教程](https://www.jianshu.com/p/a39573555039)
[Butterfly 安装文档(一) 快速开始](https://butterfly.js.org/posts/21cfbf15/)

