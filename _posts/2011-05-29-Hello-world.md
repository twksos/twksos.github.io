---
title: Hello world!
author: 望终南
layout: post
permalink: /Hello-world/
dsq_thread_id:
  - 1639981779
categories:
  - CentOS
  - Server
tags:
  - CentOS
  - mysql
  - php
  - phpMyAdmin
format: aside
---
今天捣鼓了一晚上，又架起来了一个望终南阁。

遇到的问题有：

phpMyAdmin需要5.2+的php，而centOS5.6的自带源最高版本是5.1。

> 使用[RPMForge][1]解决。  
> rpm -Uvh
> 
> http://download.fedora.redhat.com/pub/epel/5/i386/epel-release-5-4.noarch.rpm
> 
> http://rpms.famillecollet.com/el5.i386/remi-release-5-8.el5.remi.noarch.rpm
> 
> 之后yum –enablerepo=remi 就可以使用RPMforge的源

二是mysql从5.1升级5.5，无法启动。

> mv /etc/my.cnf /etc/my.cnf.bak  
> mv /etc/my.cnf.rpmnew /etc/my.cnf  
> 之后就可以启动了，接着运行升级和自动修复  
> mysql_upgrade -p  
> mysqlcheck &#8211;all-databases &#8211;check-upgrade &#8211;auto-repair -p

下一步架代理和VPN吧。

夜晚是适合思考的时间。

 [1]: http://wiki.centos.org/AdditionalResources/Repositories/RPMForge