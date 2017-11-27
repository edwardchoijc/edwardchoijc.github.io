---
title: writeup —— 第四届世安杯RE
categories: re
comments: true
date: 2017-10-14 16:51:56
type:
tags: [RE,writeup]
---

带新人参加了一下第四届的世安杯，题都挺水的.....主办方一点诚意都没有....办得太烂了.....

以下是我做了的题的WP。



<!--more-->

## 6.Console

看了一下发现是c#写的程序，于是直接用dnSpy动态调试一下即可得答案

![](http://owhak23d7.bkt.clouddn.com/17-10-16/48207954.jpg)



## 8.re

![](http://owhak23d7.bkt.clouddn.com/17-10-17/87157322.jpg)

这里创建了一个链表，结构大致如下：

![](http://owhak23d7.bkt.clouddn.com/17-10-17/61131982.jpg)

需要输入匹配的index为：

![](http://owhak23d7.bkt.clouddn.com/17-10-17/11100035.jpg)

所以输入为rotors

![](http://owhak23d7.bkt.clouddn.com/17-10-17/52355834.jpg)



## 9.动态暴力破解

[pwn2win-2016-sleeper-cell](https://github.com/xil-se/xil.se/blob/master/content/post/pwn2win-2016-sleeper-cell-kbeckmann.md)



## 10.Android

[CSDN —— 逆向BSides SF CTF之flagstore.apk](http://blog.csdn.net/caiqiiqi/article/details/77460651)



## 11.简单算法

对于每个输入的值，它对应的下标加一的数用来算v11，为了以后和自己做异或，要和存储的相等。

![](http://owhak23d7.bkt.clouddn.com/17-10-17/45903572.jpg)

则脚本如下：

[hackme.py](https://github.com/edwardchoijc/ctf-writeups/blob/master/2017-Shianbei/rev-hackme/solver_hackme.py)

结果:

![](http://owhak23d7.bkt.clouddn.com/17-10-17/28790942.jpg)



## 16.reverseMe

`file`命令查一下发现是data的时候感到奇怪

![](http://owhak23d7.bkt.clouddn.com/17-10-17/83396251.jpg)

输出它也是一串奇怪的数字，于是想到用010editor看看是什么玩意

![](http://owhak23d7.bkt.clouddn.com/17-10-17/72936574.jpg)

???  原来真的是reverse.....于是脚本一下逆出来正常文件

[reverseMe.py](https://github.com/edwardchoijc/ctf-writeups/blob/master/2017-Shianbei/rev-reverseMe/solver_reverseMe.py)

python逆一下出来一个jpeg，自己改一下后缀

![](http://owhak23d7.bkt.clouddn.com/17-10-17/92864906.jpg)

![](http://owhak23d7.bkt.clouddn.com/17-10-17/67828445.jpg)

到此处真想给出题人一个大拇指，手动打flag吧: )

> 这是一道misc



## 17.珍妮的qq号

简单数学题。

[zhenni.py](https://github.com/edwardchoijc/ctf-writeups/blob/master/2017-Shianbei/misc-zhenni/solver_zhenni.py)

结果：

![](http://owhak23d7.bkt.clouddn.com/17-10-17/357165.jpg)