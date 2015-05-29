---
title: Ubuntu Replace evolution with Thunderbird
author: 望终南
layout: post
permalink: /Ubuntu-Replace-evolution-with-Thunderbird/
dsq_thread_id:
  - 1536952150
dsq_needs_sync:
  - 1
categories:
  - Ubuntu
tags:
  - mail
  - thunderbird
  - Ubuntu
  - 邮件
---
昨晚弄毕设的时候，顺便把Ubuntu的邮件替换成了Thunderbird，一下子方便了不少。

步骤其实很简单，参考http://ubuntuforums.org/showthread.php?t=1764611

> sudo add-apt-repository ppa:ruben-verweij/thunderbird-indicator  
> sudo apt-get update  
> sudo apt-get install xul-ext-indicator libnotify-bin

卸载evolution的步骤也很简单

> sudo apt-get purge evolution evolution-common evolution-data-server evolution-documentation-en evolution-webcal evolution-plugins evolution-exchange evolution-indicator

卸载完毕

接下来配置Thunderbird开机启动，并且下载附加组建Minimize on start and close。重启，配置Minimize on start and close，选中启动Minimize on start。

完工。