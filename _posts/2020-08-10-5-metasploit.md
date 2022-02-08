---
layout:     post                                    # 使用的布局（不需要改）
title:      metasploit                          # 标题 
subtitle:   msf木马设置时间                 #副标题
date:       2020-08-10                          # 时间
author:     cx                                          # 作者
header-img:     #这篇文章标题背景图片
header-mask:    # 博文页面上端的背景图片的亮度，数值越大越黑暗
catalog: true                                           # 开启catalog，将在博文侧边展示博文的结构
istop: false              # 设为true可把文章设置为置顶文章
tags:
    - metasploit      #标签
---

msf生成反弹会话都是要先设置监听的,不然就无法上线,我们尝试着解决这个问题,最好是一直在反弹会话,一设置监听就上线.
我们用最常见的payload 
windows/meterpreter/reverse_tcp
生成exe木马后通过wireshark抓包分析,发现在不设置监听的情况下,exe默认运行时间10秒,会请求30次,如果在此期间没有得到返回,就结束程序.
通过分析源码,找到一个关键参数."ReverseConnectRetries"

![图片](/img/2020-08-10.png)

发现可以通过这个参数设置等待时间,单位秒.可以是木马运行更长时间而不退出
86400秒 = 24小时.
![图片](/img/2020-08-10-2.png)






