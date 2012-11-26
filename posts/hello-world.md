---
title: Hello, World!
date: '2012-11-26'
description: Getting started with ruhoh
categories: Life
tagline: The world of ruhoh
tags: ruhoh
---
	rp_t installB (std::function<rp_t()> sth, rp_t& rp) {
		rp_t tmp = sth();
		rp += tmp;
		return tmp;
	}
	
	std::cout << installB([](){ return use_wordpress(); }, rp) << std::endl;
	std::cout << installB([](){ return use_jykell(); }, rp) << std::endl;
	std::cout << installB([](){ return use_ruhoh(); }, rp) << std::endl;
	std::cout << installB([](){ return use_octopress(); }, rp) << std::endl;
	std::cout << installB([](){ return use_ruhoh(); }, rp) << std::endl;
	
在我决定靠写Blog来install B赚RP后，我便开始蛋疼于Blog System的选择。撸了几把Static Blog Generator之后，我果断的决定使用以前的好伙伴——WordPress。

	>Arch Linux成功被毁，WordPress安装失败，Retry...
	>使用某Linode Stackscript，PPTP Server搭建失败， Stop...
	
好了，看着Brain Console的两行输出，老夫蛋疼了，一怒之下删了WordPress，撸个Debian装完PPTP Server就不管了，现在貌似连SSH的密码都忘了。

怎么办呢？听说Jykell不错，看起来也的确不错，只是用着各种蛋疼而已。某个GitHub上的Page至今还没删。再试一试吧。

	>无目的搜索Jykell资料，在Stackoverflow上发现了一个叫做ruhoh的东西，Stop...
	
本着尝鲜的优良传统，老夫对着这个听起来很美的小Loli撸了一个晚上。

	>Ruby无法更新至ruhoh需要的版本，Stop...
	
算了，很久以前就听人家说Octopress不错，玩玩那个吧！

	>这玩意跟Jykell有什么区别？Stop...
	
在无数次蛋疼之后，我终于在伟大的 _the Force_ 的引导下，很成功的撸上了小Loli。但是，这个默认的界面，怎么跟Jykell Bootstrap一模一样！！！不愧是同一个人写的！！！

算了，看看官网上的 _Who's Using Ruhoh._ 

这几个不错哦：[Dave Long](http://davejlong.ruhoh.com)、[Blynt](http://blog.blynt.com)，尤其是[这位](http://jacobmgreer.ruhoh.com)。

行了，既然这位的如此小清新，那就撸他的小Loli吧。代码在哪里呢？这个是关键。一看到是托管在ruhoh.com上我就笑了，把网址拉到GitHub里一搜，果然找到了。下载完毕，准备干活！！！

然后，然后，然后我去楼下玩了一会，然后回来的时候， _the Force_ 指引我打开Google，搜了一下 _ruhoh Theme_ 。随手打开第一个，就是现在用的这个，老夫笑了，这个好啊！

<img src="{{urls.media}}/hello-world/screenshot.png">

不过用过之后就发现还有很多地方不咋地。比如Post，它是按Bootstrap的8-4，左边是文章+底部的Disqus，右边那么一大坨就只放发布日期和Tags。再比如Tags和Categories，默认显示都像上图的那样，一个不太漂亮的外框，里面还有一个丑陋的计数，我要那些东西干啥？于是乎，辛苦删减一个下午+晚上，才搞成现在这个样子。

代码放在了[这里](https://github.com/liums/liums.ruhoh.com)，有兴趣的同学可以[对比](https://github.com/ruhoh/hooligan)一下。

顺手表示一下，其实老夫最得意的作品就是右上角带hover&foucs效果的新浪微博图标了。为什么得意？同志您自己慢慢从原版修改就知道了。

再顺手表示一下，修改代码的时候没有注意维护，目测要是有升级什么的…你懂的。