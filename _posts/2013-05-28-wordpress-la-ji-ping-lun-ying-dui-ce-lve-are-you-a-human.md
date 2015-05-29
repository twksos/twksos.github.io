---
title: WordPress垃圾评论应对策略：Are you a human
author: 望终南
layout: post
permalink: /wordpress-la-ji-ping-lun-ying-dui-ce-lve-are-you-a-human/
dsq_thread_id:
  - 1409196098
categories:
  - 未分类
tags:
  - 工具
  - 验证
---
不得不说，现在的网络营销非常厉害啊非常厉害：博客里头122条评论，乍一看还算有点人气。结果里面有122条都是垃圾评论，100%的垃圾评论率！人干事？！  
当然，如果有人真的每天能够来这里垃圾评论一下的话，如果真的有人这么无聊的话，我也是愿意的。。。毕竟真的没什么内容。  
不过，如果是恶意脚本的话怎么办呢？最简单的策略就是验证码。在插件里面搜了一下，居然没有Verification code相关的，而且，也没有中文的。不过很凑巧的看到了一个Are you a human的插件。  
这个插件当初也听说过，旨在对抗人都看不清的 CAPTCHA 。他们使用了一些小游戏来替代 CAPTCHA 中扭曲到难以识别的文字。具体介绍请走传送门http://areyouahuman.com/  
那么，利用Are you a human需要什么呢？账号是必须的，针对一个网站，账号中会给出一个Publisher Key和一个Scoring Key。  
作为WordPress，只需要安装插件，填入这两个Key就好了。  
之后，在插件中有三个选项，分别是针对注册、忘记密码、发表回复进行验证。  
同时，还可以不针对已经注册登录的用户验证。

小游戏也很有趣，只是不知道有没有中文版