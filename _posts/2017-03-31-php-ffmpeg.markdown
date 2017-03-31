---
layout: post
title:  "windows下php7如何安装redis扩展"
date:   2017-03-31 16:29:22 +0800
categories: wymDon update
---
##win7 安装ffmpeg
1.ffmpeg 安装包下载https://ffmpeg.zeranoe.com/builds/ 
解压后得到的文件目录为
//bin
//doc
//licenses
//presets
//README.txt
>重点：（是bin目录下的三个.exe的执行文件）将bin路径添加到系统环境变量（之后php代码中引入会用到）之后命令行可以使用ffmpeg来确认是否正确安装

2.通过composer来帮助项目引入php-ffmpeg扩展包
部分程序代码：
```ruby
$ffmpeg = FFMpeg\FFMpeg::create(array(
	'ffmpeg.binaries'  => 'F:\ffmpegwin64-static\bin\ffmpeg.exe',
	'ffprobe.binaries' => 'F:\ffmpegwin64-static\bin\ffprobe.exe',
	'timeout'          => 3600, // The timeout for the underlying process
	'ffmpeg.threads'   => 12,   // The number of threads that FFMpeg should use
));
var_dump($ffmpeg);exit;
```
至此结束；

##坑坑介绍
1.php-ffmepg 包是不需要安装传统php扩展的，所以php.ini也不需要更改（除非ffmepg所需要加载一些扩展）
2.'ffmpeg.binaries'  => 'F:\ffmpegwin64-static\bin\ffmpeg.exe' windows系统是要加.exe的