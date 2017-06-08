---
layout: post
title:  "centos编译安装ffmpeg"
date:   2017-06-08 16:16:22 +0800
categories: wymDon update
---

    node作为前后端分离的装X利器，必然要接触一下。以下为本人在linux操作系统下安装的过程和遇到的一些小坑。

node作为前后端分离的装X利器，必然要接触一下。以下为本人在linux操作系统下安装的过程和遇到的一些小坑。

- 环境：centos7（默认包含python2.7）
- nodejs安装包
- 源码编译安装


----------

1.首先下载nodejs安装包[下载地址][1]


  [1]: https://nodejs.org/en/download/

```linux
wget https://nodejs.org/dist/v6.11.0/node-v6.11.0.tar.gz #最新版
```

2.解压编译并安装

```linux
tar -zxf node-v6.11.0.tar.gz
cd node-v6.11.0.tar.gz
./configure --prefix=/usr/local/node/ #置顶安装目录
make && make install
```
3.检测安装结果

```linux

node -v //输出node版本号
npm -v  //输出npm版本号

```
**一些注意事项**
使用npm 安装一些包的时候出错
重新定义下镜像地址解决

```linux
npm config set registry http://registry.cnpmjs.org
```
后续待更