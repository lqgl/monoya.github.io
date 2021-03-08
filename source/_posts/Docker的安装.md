---
title: Ubuntu 安装 Docker
tags:
  - Ubuntu
  - Docker
categories: Docker
keywords: 'Ubuntu,Docker'
description: Ubuntu 安装 Docker
top_img: 'https://raw.githubusercontent.com/lqgl/repo/main/img/top_img.jpg'
date: 2021-03-07 15:34:31
updated:
cover: https://raw.githubusercontent.com/lqgl/repo/main/img/20210308090455.png
---

# Ubuntu 安装 Docker

## 使用脚本自动安装

在测试或开发环境中 Docker 官方为了简化安装流程，提供了一套便捷的安装脚本，Ubuntu 系统上可以使用这套脚本安装：

```
$ curl -fsSL get.docker.com -o get-docker.sh
# 可能会出现 404 错误，请移步下面的特别说明
$ sudo sh get-docker.sh --mirror Aliyun
```

执行这个命令后，脚本就会自动的将一切准备工作做好，并且把 Docker CE 的 Edge 版本安装在系统中。

## 查看 Docker 版本

```
docker version
```

## 卸载 Docker

用了 Aliyun 脚本安装并成功的

- 卸载 Docker 的命令为：`apt-get autoremove docker-ce`
- 删除 `/etc/apt/sources.list.d` 目录下的 `docker.list` 文件

![image-20210307154353096](https://raw.githubusercontent.com/lqgl/repo/main/img/image-20210307154353096.png)

## 启动 Docker CE

```
$ sudo systemctl enable docker
$ sudo systemctl start docker
```

## 建立 docker 用户组

默认情况下，`docker` 命令会使用 [Unix socket](https://en.wikipedia.org/wiki/Unix_domain_socket) 与 Docker 引擎通讯。而只有 `root` 用户和 `docker` 组的用户才可以访问 Docker 引擎的 Unix socket。出于安全考虑，一般 Linux 系统上不会直接使用 `root` 用户。因此，更好地做法是将需要使用 `docker` 的用户加入 `docker` 用户组。

建立 `docker` 组：

```bash
$ sudo groupadd docker
```

将当前用户加入 `docker` 组：

```bash
$ sudo usermod -aG docker $USER
```

退出当前终端并重新登录，进行如下测试。

## 测试 Docker 是否安装正确

```bash
$ docker run hello-world

Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b8dfde127a29: Pull complete 
Digest: sha256:89b647c604b2a436fc3aa56ab1ec515c26b085ac0c15b0d105bc475be15738fb
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

若能正常输出以上信息，则说明安装成功。

##  参考文档

- [Docker 官方 Ubuntu 安装文档](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/)

- [Ubuntu 安装  Docker](https://www.funtl.com/zh/docker/Ubuntu-%E5%AE%89%E8%A3%85-Docker.html)
