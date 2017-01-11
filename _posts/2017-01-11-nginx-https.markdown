---
layout: post
title:  "nginx服务器HTTPS简单配置（阿里ECS为例）"
date:   2017-01-11 9:51:22 +0800
categories: wymDon update
---
## 进入conf文件

```ruby
server {
        listen 443; server_name #你的域名;
        ssl on;
        root #web目录;
        index index.html index.htm index.php;
        ssl_certificate /alidata/server/nginx/sslkey/****.pem;
        ssl_certificate_key  /alidata/server/nginx/sslkey/****.key;
        ssl_session_timeout 5m;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers AESGCM:ALL:!DH:!EXPORT:!RC4:+HIGH:!MEDIUM:!LOW:!aNULL:!eNULL;
        ssl_prefer_server_ciphers on;
		#其他配置代码省略
		.
		.
		.
		.
		.
		}
server {
        listen     80;
        server_name  #你的域名;
        #return 301 https://$server_name$request_uri;#80端口重定向到443端口 也就是http访问重定向到https（有需要就加）
        index index.html index.htm index.php;
        root #web目录;
		#其他配置代码省略
		.
		.
		.
		.
		.
		}
```
> 重启nginx查看配置是否成功

1.注意https端口为443
2.pem和key可以自己按照一定算法生成（浏览器会报证书错误），阿里云提供生成渠道，也可自己去国外网站生成
