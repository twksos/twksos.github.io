---
title: 用Brakeman来保护你的Rails应用
author: 望终南
layout: post
permalink: /yong-Brakeman-lai-bao-hu-ni-de-Rails-ying-yong/
dsq_thread_id:
  - 1432783403
categories:
  - Tools
tags:
  - RoR
---
最近RoR这边出了一件大事：Github 因为Mass assignment没用好被攻击了。

互联网应用除了没人用最怕的估计就是被攻击了。在这次的攻击中各大rails应用都开始紧张的排查自己的安全漏洞。但是并不是每个公司都能请得起安全专家。另外，我们的很多应用也没有重要到要请安全专家这一步。

但是应用有明显的漏洞就像是开着门请别人进来，这样总是不好吧。最简单的办法就是使用一个检测工具来告诉你代码哪里哪里可能有问题，甚至告诉你rails本身需要升级或者哪里需要打补丁。

Brakeman这个Gem可以进行对代码进行静态检测。

> gem install brakeman

或者加入Gemfile里面

> gem &#8216;brakeman&#8217;

然后

> bundle install

嗯，安装好了，检测当前项目的情况

> breakman -h html -o breakman-result.html

-h 指明生成html文件

-o 指明生成文件的存放位置（当前文件夹下的breakman-result.html）

之后打开这个新生成的html文件就可以看到breakman的报告啦。

更具体的详情请走传送门

<http://brakemanscanner.org/docs/>

&nbsp;