---
title: 思考代码（一）-代码在哪里
author: 望终南
layout: post
permalink: /si-kao-dai-ma-yi-dai-ma-zai-na-li/
dsq_thread_id:
  - 
dsq_needs_sync:
  - 1
categories:
  - 不停止思考
---
从事软件工作一段时间了，前些日子忽然病倒了。卧床在家的时候远离代码，杂七杂八的乱想。病愈回到公司，又顶了一周的QA测试工作。忽然觉得对商业软件开发中代码的有些理解了。

**代码在哪里？**

由于我所在的公司实行敏捷开发，那就先从敏捷宣言讲起吧。

> <p style="text-align: center;">
>   Our highest priority is to satisfy the customer<br /> through early and continuous delivery<br /> of valuable software.
> </p>

持续交付有价值的软件和尽早满足客户的需求是敏捷宣言中的最优先事项。我认为这非常适合商业软件开发的情况，尤其适合当前的互联网创业。《黑客与画家》中提到过

> 互联网软件带来的最大变化之一，就是软件发布方式的改变。

当你能够尽快的满足客户需求的功能，客户就更可能向你而非你的竞争对手倾斜。能够满足客户需求的软件，就是有价值的软件。有价值的软件，由有意义的代码构成。

对于《黑客与画家》中Viaweb这个例子，网站一直由一批（三个）程序员来进行开发，并且使用了Lisp以增进开发效率、建立技术壁垒，代码方面并没有出什么问题，而且他们还可以使用诸如宏之类的特性。

但是，让我们来考虑一个普通的创业公司的时候，当他们只有N个普通的程序员JP[N]（以后以JP[1],JP[2]等来表示）和一个稍有经验的SP，同时还要考虑[Bus Factor][1]，使用Lisp的宏就看起来不那么美好了。因为投资人还指望着有人离职之后（这年头跳槽很常见啊亲），迅速找来能接手工作的孩子呢。如果用了Lisp，先不说能不能招到懂行的人。招到之后交接的代价也够喝一壶了。

团队的代码库和团队硬盘里的代码库是有区别的。正如SP有一次对JP说的那样：

<p style="padding-left: 30px;">
  SP和JP在码一段代码。<br /> JP发现需要调用的一个函数写的太复杂了，就问SP：这函数谁写的啊？<br /> SP：git blame bad_code | grep function <a href="http://wbnbd.com/#q=what that for">WTF</a><br /> <code>HASHVALUE (JP 20XX-XX-XX XX:XX:XX +0800 N) function WTF</code><br /> JP看了半天：哦~，貌似我某天写的，里面有从网上拷来的代码，我没搞太清楚。<br /> SP说，既然你也不清楚，那我们就好好看看，顺便重构一下吧。<br /> JP：时间要紧，我们先继续开发吧。<br /> SP：没有个功能，我们的功能实现不了啊。<br /> JP：可是我们有这个函数啊。<br /> SP：它在那里，也不在那里。重点是，它不在你心里，也就不在团队里。
</p>

团队的代码库就是每个人对代码理解的集合，暂时称其为*逻辑代码库*，硬盘里的代码暂时叫做*实体代码库*  
*实体代码库*比较好理解，它属于<del datetime="2012-08-19T12:19:47+00:00">不堕轮回，不入地狱</del><ins datetime="2012-08-19T12:19:47+00:00">好着就好，丢了就囧</ins>型的。  
对于*逻辑代码库*而言，就有些好玩的地方了。由于逻辑代码库是每个人对代码理解的集合，其中难免有一些冲突。  
例如：SP设计了controller A仅用作简单的连接model和view的桥梁，很多处理都扔到model里了，而JP[1]却觉得为这里应该放一些处理model中数据的功能。  
对于这些冲突，就必须merge了，不然功能分部奇怪的话，只会让后面来的人不知道代码改写在哪里。  
对于*逻辑代码库*的merge，重点在于所有人认识一致。笔者知道的比较成功的实践有：每天换Pair的结对编程、每天早上或晚上的Code Review、项目组人员不超过3人<del datetime="2012-08-19T12:19:47+00:00">、每天晚上回家加班看代码</del>等。  
愿大家在坚持敏捷实践中的两种代码库都多merge，少冲突。

 [1]: http://wbnbd.com/#q=bus factor