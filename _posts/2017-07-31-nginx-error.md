---
date: 2017-07-31T12:20:12.000Z
layout: post
title: Nginx下配置typecho出现"Access denied"
thread: 166
categories: 日志
tags: 博客
published: true
---


如果你也尝试用在Nginx环境配置typecho的博客，当按照 [typecho文档](http://docs.typecho.org/doku.php) 在服务器上传好安装文件，按步骤安装成功后。查看网站主页点击其他链接时，出现 **"Access denied"** 提示

![access denied](http://oqnsxsykk.bkt.clouddn.com/access%20denied.jpg)

经过一番折腾后，发现是 php 中 cgi 的一个配置问题造成的，在这里我们只需要修改一下`php.ini`中的参数即可。
oneinstack中` php.ini ` 默认路径： **/usr/local/php/etc/php.ini** ，将其中  ` cgi.fix_pathinfo = 0 改为 "1" ` 
![php.ini](http://oqnsxsykk.bkt.clouddn.com/vim%20php.jpg)


关于"cgi.fix_pathinfo"的配置问题，据说是Nginx+PHP的一个安全漏洞，关闭最为保险，但某些网站（如typecho、Discuz!）的正常运行还是需要开启的。
点击[此处](http://www.laruence.com/2010/05/20/1495.html)了解这个安全漏洞的详细内容。

	注：只有Nginx下配置typecho才会出现这种情况，如果是Apache服务的话不会出现此类错误。

2017-6-9
