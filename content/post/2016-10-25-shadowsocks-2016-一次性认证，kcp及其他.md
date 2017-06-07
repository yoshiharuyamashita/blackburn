---

title: 'shadowsocks 2016: 一次性认证，KCP及其他'
author: HeYSH
type: post
date: 2016-10-25T13:03:46+00:00
url: /2016/10/25/shadowsocks-2016-一次性认证，kcp及其他/
aliases:
  - /2016/10/25/shadowsocks-2016-一次性认证，kcp及其他/
dsq_thread_id:
  - "5264513038"
categories:
  - linux
  - web

---
今天下午我的Bandwagon服务器被人爆掉了，让人发了一大堆垃圾邮件，于是有了一个重装的理由。终于可以用服务器原生IPv6了\~

距我上次配置shadowsocks服务端（2015.1）已经有一年半了，这次安装可以把上次没有加入的特性通通带上：

-   一次性认证，好像是当时和SSR打的时候加入的特性
-   chacha20，上次没加好像是因为懒
-   KCPtun，既然现在android客户端带上了这个功能，那就也装上吧

大概会稍微快一些吧……

对了，顺便配个iptables，象征性地防守下。

------------------------------------------------------------------------

update 161122:

象征性的防守被漫不经心的进攻给破掉了，于是增加了一些稍微认真一点的防守：

-   禁用root登录和密码登录，顺便配置了sudo；
-   用ufw代替直接配置iptables；
-   fail2ban（后来发现debian 8带的0.8版本并不支持debian 8的journalctl……interesting）

最主要的，换了一个ip地址

