---
layout: post
title: 讲解 | 为什么我电脑课上不了网络了？！
date: 2017/12/01
categories: blog
tags: [红蜘蛛,IPv4,网卡]
description: wtf
---

Hi,Every boby!这次我拖更了一周，不过为大家带来一个新鲜事。

想必大家上电脑课，都盼望着一件事情

#### 自由活动！！！！！！！！！！

是的，想必大家都很想在电脑课上自由活动吧~但是呢，该死的电脑老师就是会这样的：

```
你的电脑显示了这样一个东西：

屏幕锁定了，请耐心听讲
```

这个时候，我觉得大家是这样的

![](https://raw.githubusercontent.com/sctop/WebSideFile/master/sctop.github.io/20171201/%E7%BA%A2%E8%9C%98%E8%9B%9B.png?raw=true)

每次控制的时候，我们可能都会这样：

![](https://github.com/sctop/WebSideFile/raw/master/sctop.github.io/20171201/%E9%9F%A9%E5%9B%BDboy.gif)

这个时候，总会有人（没错就是我）弄出来一个解禁程序：

```
@echo off
taskkill /f /t /im rscheck.exe
taskkill /f /t /im checkrs.exe
taskkill /f /t /im redagent.exe
taskkill /f /t /im epointer.exe
```

![](https://i0.hdslb.com/bfs/article/c9c9449335f0ce757b72688c74e50e8a2a986494.jpg@1194w_436h.webp)

感觉拥有了全世界啊233333

然后，我们兴冲冲打开网页时，发现...

![](https://github.com/sctop/WebSideFile/blob/master/sctop.github.io/20171201/%E6%80%80%E7%96%91%E4%BA%BA%E7%94%9F%E7%9A%84%E7%BD%91%E7%AB%99%E8%BF%9E%E6%8E%A5.png?raw=true)

**感觉天都要塌了下来、、、**

啊啊啊脱离了老师的控制却没法上网，脱离有屁用啊！

（于是我分析了网络连接详细信息）

然后我得到了一个奇怪的IPv4地址

```
169.xxx.xxx.xxx
```

emmm，很明显是老师用了某种玩意将我们全部重定向到这IPv4上了。于是我手动指定：

```
IP地址：192.1682.2.254
子网掩码：255.255.255.0
网关地址：192.168.2.1

首选DNS地址：192.168.2.1
备选DNS地址：
```

emmm手动完毕，然后上网冲浪，开始上steam玩吃鸡！

你本以为是这样的：

![](https://imgsrc.baidu.com/baike/pic/item/023b5bb5c9ea15ce63ba2d9ebd003af33b87b2d5.jpg)

实际上是这样子的：

![](https://github.com/sctop/WebSideFile/blob/master/sctop.github.io/20171201/%E6%80%80%E7%96%91%E4%BA%BA%E7%94%9F%E7%9A%84%E7%BD%91%E7%AB%99%E8%BF%9E%E6%8E%A5.png?raw=true)

emmm，究竟哪里出问题了呢？

改变第一次：

![](https://github.com/sctop/WebSideFile/blob/master/sctop.github.io/20171201/%E6%80%80%E7%96%91%E4%BA%BA%E7%94%9F%E7%9A%84%E7%BD%91%E7%AB%99%E8%BF%9E%E6%8E%A5.png?raw=true)

第二次：

![](https://github.com/sctop/WebSideFile/blob/master/sctop.github.io/20171201/%E6%80%80%E7%96%91%E4%BA%BA%E7%94%9F%E7%9A%84%E7%BD%91%E7%AB%99%E8%BF%9E%E6%8E%A5.png?raw=true)

...第N次：

![](https://github.com/sctop/WebSideFile/blob/master/sctop.github.io/20171201/%E6%80%80%E7%96%91%E4%BA%BA%E7%94%9F%E7%9A%84%E7%BD%91%E7%AB%99%E8%BF%9E%E6%8E%A5.png?raw=true)

或者如果你有钱，你其实不用这么麻烦，弄个VPN直接连到你的vps上就可以了

![](https://i0.hdslb.com/bfs/article/b91c5a5682f8a183096c783647e723c5d5ad308e.gif)

（但首先你要知道，这不可能）

于是我开始了**漫长**的ping过程。。。。。。。

我首先想的是，老师的电脑IP是多少呢？于是我决定ping一下教师机TC

```
Microsoft Windows [版本 6.1.7601]
版权所有 (c) 2009 Microsoft Corporation。保留所有权利。

C:\Users\Administrator>ping TC

正在 Ping TC [fe80::f8da:96d0:e61d:d7b7%12] 具有 32 字节的数据:
来自 fe80::f8da:96d0:e61d:d7b7%12 的回复: 时间<1ms
来自 fe80::f8da:96d0:e61d:d7b7%12 的回复: 时间<1ms
来自 fe80::f8da:96d0:e61d:d7b7%12 的回复: 时间<1ms
来自 fe80::f8da:96d0:e61d:d7b7%12 的回复: 时间<1ms

fe80::f8da:96d0:e61d:d7b7%12 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 0ms，最长 = 0ms，平均 = 0ms
```

emmm，本以为返回过来的应该是个IP，但是返回过来的是个地址！奇奇怪怪，我接连ping了一下几台内网的：

```
C:\Users\Administrator>ping YX010

正在 Ping YX010 [fe80::39a1:460a:e28d:b3ca%12] 具有 32 字节的数据:
来自 fe80::39a1:460a:e28d:b3ca%12 的回复: 时间<1ms
来自 fe80::39a1:460a:e28d:b3ca%12 的回复: 时间<1ms
来自 fe80::39a1:460a:e28d:b3ca%12 的回复: 时间<1ms
来自 fe80::39a1:460a:e28d:b3ca%12 的回复: 时间<1ms

fe80::39a1:460a:e28d:b3ca%12 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 0ms，最长 = 0ms，平均 = 0ms

C:\Users\Administrator>ping YX18

正在 Ping YX18 [fe80::a8b2:feef:784:4053%12] 具有 32 字节的数据:
来自 fe80::a8b2:feef:784:4053%12 的回复: 时间<1ms
来自 fe80::a8b2:feef:784:4053%12 的回复: 时间<1ms
来自 fe80::a8b2:feef:784:4053%12 的回复: 时间<1ms
来自 fe80::a8b2:feef:784:4053%12 的回复: 时间<1ms

fe80::a8b2:feef:784:4053%12 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 0ms，最长 = 0ms，平均 = 0ms

C:\Users\Administrator>ping YX42
Ping 请求找不到主机 YX42。请检查该名称，然后重试。

C:\Users\Administrator>ping YX042

正在 Ping YX042 [fe80::646f:6f36:b515:87f2%12] 具有 32 字节的数据:
来自 fe80::646f:6f36:b515:87f2%12 的回复: 时间<1ms
来自 fe80::646f:6f36:b515:87f2%12 的回复: 时间<1ms
来自 fe80::646f:6f36:b515:87f2%12 的回复: 时间<1ms
来自 fe80::646f:6f36:b515:87f2%12 的回复: 时间<1ms

fe80::646f:6f36:b515:87f2%12 的 Ping 统计信息:
    数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，
往返行程的估计时间(以毫秒为单位):
    最短 = 0ms，最长 = 0ms，平均 = 0ms

C:\Users\Administrator>
```

全部的电脑都指向一个地址——`fe80::646f:6f36:b515:87f2%12`，很显然的了，既然这个地址老师的电脑ping出来了，那么也肯定是老师搞的鬼了。

但是我后来回忆了一下，发现这个地址是IPv6地址——我这台的IPv6地址也跟这个差不多格式。。。这是怎么回事呢？

还好我家里有另外一台老电脑，于是我调出来了信息。作为对比，我写出来两台电脑之间的IPv6地址：

```
（以下地址均为本地IPv6地址内容）
新电脑：
fe80::a819:cdd2:92ce:9002%6

旧电脑：
fe80::9578:cd30:edb9:83e9%12
```

**每台电脑获取的IPv6地址都是不同的！**

目前我们已知的最快ping回来的速度为`<1ms`的只有本地环回地址`127.0.0.1`或者路由器（交换机）的默认网关地址`192.168.2.1 / 192.168.1.1`才可以得到这个速度。

在结论之前，我们先来看看IPv6是什么：

> TCP/IPv6。最新版本的Internet协议，可以跨多个相互连接的网络进行通信。
>
> IPv6是Internet Protocol Version 6的缩写，其中Internet Protocol译为“互联网协议”。IPv6是IETF（互联网工程任务组，Internet Engineering Task Force）设计的用于替代现行版本IP协议（IPv4）的下一代IP协议，号称可以为全世界的每一粒沙子编上一个网址。

由此，我们得出了这些结论：
1. 老师用了某种手段，使我们的电脑的IPv6全部指向了一个本地虚拟出来的IPv6地址。为什么不是“指向默认网关”呢？如果指向了默认网关，那么学校机房内的服务器默认网关地址`192.168.2.1`应该能够访问或者ping通。但是实际上，我没有办法ping通192.168.2.1这个地址。
2. IPv6从介绍内也可以看出来，是“跨多个相互连接的网络通信”的一个协议。下面我用了“路由跟踪”命令进行了跟踪www.baidu.com：

```
Microsoft Windows [版本 10.0.15063]
(c) 2017 Microsoft Corporation。保留所有权利。

C:\Users\2094880085>tracert www.baidu.com

通过最多 30 个跃点跟踪
到 www.a.shifen.com [183.232.231.173] 的路由:

  1    <1 毫秒   <1 毫秒   <1 毫秒 192.168.1.1
  2     2 ms     2 ms     2 ms  172.16.0.1
  3    26 ms     3 ms     3 ms  120.196.22.153
  4    11 ms    10 ms    11 ms  120.196.244.221
  5    12 ms    11 ms    13 ms  211.136.244.194
  6    16 ms    15 ms    15 ms  120.241.49.30
  7     *        *        *     请求超时。
  8    14 ms    13 ms    13 ms  183.232.231.173

跟踪完成。

C:\Users\2094880085>
```

所以，“跨多个相互连接的网络通信”IPv6就是这样的作用了。
3. `fe80::646f:6f36:b515:87f2%12`是一个IPv6地址，这个地址极有可能是路由表分配的，我从百度百科上找到了这些文字：

```
IPv6使用两种地址自动配置协议，分别为无状态地址自动配置协议（SLAAC）和IPv6动态主机配置协议（DHCPv6）。SLAAC不需要服务器对地址进行管理，主机直接根据网络中的路由器通告信息与本机MAC地址结合计算出本机IPv6地址，实现地址自动配置；DHCPv6由DHCPv6服务器管理地址池，用户主机从服务器请求并获取IPv6地址及其他信息，达到地址自动配置的目的。
一、无状态地址自动配置
　　无状态地址自动配置的核心是不需要额外的服务器管理地址状态，主机可自行计算地址进行地址自动配置，包括4个基本步骤：
　　1. 链路本地地址配置。主机计算本地地址。
　　2. 重复地址检测，确定当前地址唯一。
　　3. 全局前缀获取，主机计算全局地址。
　　4. 前缀重新编址，主机改变全局地址。
二、IPv6动态主机配置协议
　　IPv6动态主机配置协议DHCPv6是由IPv4场景下的DHCP发展而来。客户端通过向DHCP服务器发出申请来获取本机IP地址并进行自动配置，DHCP服务器负责管理并维护地址池以及地址与客户端的映射信息。
　　DHCPv6在DHCP的基础上，进行了一定的改进与扩充。其中包含3种角色：DHCPv6客户端，用于动态获取IPv6地址、IPv6前缀或其他网络配置参数；DHCPv6服务器，负责为DHCPv6客户端分配IPv6地址、IPv6前缀和其他配置参数；DHCPv6中继，它是一个转发设备。通常情况下。DHCPv6客户端可以通过本地链路范围内组播地址与DHCPv6服务器进行通信。若服务器和客户端不在同一链路范围内，则需要DHCPv6中继进行转发。DHCPv6中继的存在使得在每一个链路范围内都部署DHCPv6服务器不是必要的，节省成本，并便于集中管理。
```

所以现在最好的方法是，记下正常网络下的IPv6地址，然后在封禁网络时手动指定，这样才可能会获得一点希望。