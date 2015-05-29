---
title: Git之Rollback
author: 望终南
layout: post
permalink: /Git-zhi-Rollback/
dsq_thread_id:
  - 1411299994
dsq_needs_sync:
  - 1
categories:
  - Tools
tags:
  - git
---
<p style="color: #ff0000;">
  注：回滚什么的就是个杯具，你可能不需要这么做。可以参照checkout branch（还没写&#8230;请google之）<br /> 另：本文还没写完。估计还得等下周。半成品请将就看&#8230;.<br /> 之后的工作有：
</p>

  * 1.配图
  * 2.配Github repo
  * 3.配些链接

最近在项目中使用git对已经push的更改进行回滚操作。  
当时的状况如下图：  
<!--图等等再加-->

  
需要回滚的是commit 2, commit 4.  
<!--图等等再加-->

  
于是有两种策略。  
**1.否认历史**

<p style="padding-left: 30px;">
  当时直接考虑最简单的情况，如果没有commit 2和commit 4会怎么样？<br /> 神不知鬼不觉的回滚到commit 1有木有，这个主意太好了，我们就这么搞吧。<br /> <!--图等等再加-->
  
  <br /> <code>&lt;br />
git reset --hard HASH_OF_COMMIT_1&lt;br />
git cherry pick HASH_OF_COMMIT_2&lt;br />
</code><br /> 然后，repo的状态应该是这样的。<br /> <!--图等等再加-->
  
  <br /> 对于我这种懒人，就可以直接把它扔到origin/master上面了。<br /> <code>&lt;br />
git push --force&lt;br />
</code><br /> <!--图等等再加-->
  
  <br /> Oh YEAH!<br /> origin/master的历史已经改变了。<br /> 到此，任务完成。<br /> 于是同事A、B分别pull了一下代码。<br /> A表示非常满意。<br /> B表示一点都不满意，repo乱作一团啊。<br /> <!--图等等再加-->
  
  <br /> 额，原来B在回滚之前刚好pull过一次代码（A你pull的不够啊）。<br /> 于是B的master认为的情况是这样的。<br /> <!--图等等再加-->
  
  <br /> 这里就是Git的分布式奥义了。除非大家都否认历史，否则历史总是存在的。
</p>

**2.修补**

<p style="padding-left: 30px;">
  好吧，我承认我有失误我的提交不好所以我要回滚代码。这个也没什么好藏着掖着的。<br /> 于是进行<br /> <code>&lt;br />
git revert HASH_OF_COMMIT_4&lt;br />
</code><br /> <!--图等等再加-->
  
  <br /> <code>&lt;br />
git revert HASH_OF_COMMIT_2&lt;br />
</code><br /> <!--图等等再加-->
  
  <br /> <code>&lt;br />
git push&lt;br />
</code><br /> <!--图等等再加-->
  
  <br /> 嗯，由于我的revert中没有出现冲突，所以不需要什么merge。<br /> 但是如果需要的话，比如commit 3, commit 2对同一个文件做出了修改。<br /> 那么revert的时候就需要手工merge。<br /> 然后commit 加注释<br /> 大功告成。
</p>

总结：  
两种方式各有利弊：  
一个是正着cherry-pick，但是对历史有破坏，对于revert一大堆的情况小团队可以使用。  
一个是正统revert，留着历史，随时还可以再回去。就是很可能要一个一个merge。  
当然。这个杯具都是因为发布权不在我们自己手里。不然的话直接checkout一个branch，再进行打包等活动就好了。