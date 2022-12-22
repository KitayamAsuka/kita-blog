---
title: "解决部署在Github Pages上图片不显示的问题"
date: 2022-12-22T19:18:26+08:00
draft: false 
description: 又见到了奇怪的问题
tags: 
    - 疑难杂症
    - 实验
    - 网站设置
categories: 
    - Debug
---

简单来说一句话，看看自己有没有配置config.toml里的baseUrl。如果没有的话自己每次引用的图片都是自己的域名/引用的域名，这样能找的到图片就有鬼了，肯定每次都报错404。

我还因为这个问题头疼了两天，主要是搜也搜不到，估计是很蠢的问题，也没好意思提Issue去问。

现在发现根源之后果然很蠢。主要是浏览器报错的error竟然是黄色的，在我的刻板印象里黄色的都是warning不用管的。

后来想了想本地部署的可以显示，但是远程的不行，那我看看这个报的错有什么区别呗。一对比才找到问题。

于是搜了下上面的`Error with Permissions-Policy header: Origin trial controlled feature not enabled: 'interest-cohort'.`

找到了[这个博客](https://blog.csdn.net/DD_Davis/article/details/128101441)就想起来前几天配置的时候为了方便不用老改CNAME，把Url删除空了，这样确实主页什么的改或者不改域名都能进了，但是图片引用上就寄了。真是服了。

不过就算配置了baseUrl这个报错也不会消失，不过能用就行了我也不想管了。

[StackOverflow上面有说是router配置问题的](https://stackoverflow.com/questions/72948207/error-with-permissions-policy-header-origin-trial-controlled-feature-not-enable)，反正大概就还是哪个地方没写明白地址的事吧。