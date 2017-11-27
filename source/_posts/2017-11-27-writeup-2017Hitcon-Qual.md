---
title: writeup —— 2017Hitcon_Qual
categories: re
tags: [RE,writeup]
comments: true
date: 2017-11-27 14:56:46
type:
---

打国际赛才能认识到自己的弱小 :)



<!--more-->

## Sakura

唯一做出的一道题 :(

要求输入400bytes，然后经过一系列验证函数，如果正确则输出flag（输入值的SHA256值）

![](http://owhak23d7.bkt.clouddn.com/17-11-27/12995336.jpg)

验证函数太大了，导致IDA没法反汇编为C(只显示部分如下)

![](http://owhak23d7.bkt.clouddn.com/17-11-27/48078380.jpg)

每步都是用input加某个不同的值，然后再验证一下它们的sum是否match

这里想到了符号执行，试着用angr跑，结果能getflag

自己写的脚本太简陋了，此处参考LCBC的脚本

[solver_sakura.py](https://github.com/edwardchoijc/ctf-writeups/blob/master/2017-Hitcon/rev-sakura/solver_sakura.py)



## Seccomp

参考：

[https://blukat29.github.io/2017/11/hitcon-quals-2017-seccomp/](https://blukat29.github.io/2017/11/hitcon-quals-2017-seccomp/)

[https://azure.kdays.cn/2017/11/08/HITCON2017-writeup/](https://azure.kdays.cn/2017/11/08/HITCON2017-writeup/)



## 家徒四壁~Everlasting Imaginative Void~

参考：

[https://azure.kdays.cn/2017/11/08/HITCON2017-writeup/](https://azure.kdays.cn/2017/11/08/HITCON2017-writeup/)



## 天衣無縫~Fantastic Seamless Textile~

参考：

[https://gist.github.com/pzread/2ae0bb3aa5fe0dc69fcf3257c41db944](https://gist.github.com/pzread/2ae0bb3aa5fe0dc69fcf3257c41db944)

[https://github.com/radare/radare2/pull/8796](https://github.com/radare/radare2/pull/8796)

