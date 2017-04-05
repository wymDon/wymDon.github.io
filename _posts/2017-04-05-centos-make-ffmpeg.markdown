---
layout: post
title:  "centos编译安装ffmpeg"
date:   2017-04-5 16:29:22 +0800
categories: wymDon update
---
## 下载并安装如下代码
```linux
wget http://ffmpeg.org/releases/ffmpeg-3.2.4.tar.bz2 //获取安装包
tar jxvf ffmpeg-3.2.4.tar.bz2 //解压
cd ffmpeg-3.2.4/ //切换到文件目录
./configure --enable-shared --prefix=/usr/local/ffmpeg
make && make install
```
> 安装过程中可能会出现若干警告，只要没有error出现也会安装完成

下面是一些坑

##不能启动
```linux
ffmpeg // /usr/local/ffmpeg/bin/ffmpeg
```
以上命令可能会出现错误如下
```linux
Ffmpeg: error while loading shared libraries: libavdevice.so.52: cannot open shared object file
//或者 Ffmpeg: error while loading shared libraries: libavdevice.so.57: cannot open shared object file
```
> 解决方法如下

* find -name XXX 找到你确实的文件 例如：/usr/local/ffmpeg/lib // 在这个文件夹下
* 将以上目录添加到配置文件  例如： vi /etc/ld.so.conf
* 执行代码 ldconfig //动态链接库管理命令具体用法自行百度

## 最后执行
```linux
ffmpeg // /usr/local/ffmpeg/bin/ffmpeg
```
得到结果
```linux
$ /usr/local/ffmpeg/bin/ffmpeg
ffmpeg version 3.2.4 Copyright (c) 2000-2017 the FFmpeg developers
  built with gcc 4.8.3 (GCC) 20140911 (Red Hat 4.8.3-9)
  configuration: --enable-shared --prefix=/usr/local/ffmpeg
  libavutil      55. 34.101 / 55. 34.101
  libavcodec     57. 64.101 / 57. 64.101
  libavformat    57. 56.101 / 57. 56.101
  libavdevice    57.  1.100 / 57.  1.100
  libavfilter     6. 65.100 /  6. 65.100
  libswscale      4.  2.100 /  4.  2.100
  libswresample   2.  3.100 /  2.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'

```
成功！