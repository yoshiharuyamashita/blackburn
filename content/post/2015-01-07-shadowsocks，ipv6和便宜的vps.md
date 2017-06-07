---

title: 'shadowsocks，ipv6和便宜的VPS，还有OpenVPN'
author: HeYSH
type: post
date: 2015-01-07T15:05:56+00:00
url: /2015/01/07/shadowsocks，ipv6和便宜的vps/
aliases:
  - /2015/01/07/shadowsocks，ipv6和便宜的vps/
cleanretina_sidebarlayout:
  - default
dsq_thread_id:
  - "3667750278"
duoshuo_thread_id:
  - "1239563020875595818"
categories:
  - linux
  - web
tags:
  - GFW
  - ipv6
  - shadowsocks
  - VPS

---
那个……我还活着呢。

前几天睡不着的时候翻了一下这个博客，最后发布时间是去年的5月份。七个月的话应该是很多草本植物的一生了吧？幸好这里种的是树。

……算了过几天写一页年终总结来写这些充满腐烂气息的东西吧。今天是正经的技术环节，当然是剪切链接形式的技术。

那么首先是VPS，用的是便宜的[Bandwagon](https://bandwagonhost.com/aff.php?aff=1656)（搬瓦工），因为穷，只买了64M内存的版本；因为没有信用卡（穷），用不了paypal，于是去淘宝找了一家代购，入手价格29￥/年。

然后是shadowsocks，按照[这里](https://github.com/shadowsocks/shadowsocks/wiki/Shadowsocks-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)的办法安装。根据[这里](http://blog.robotshell.org/2014/about-shadowsocks/)的说法，就用python版的服务端就好。

为了看起来像是技术文档的样子，下面是`/etc/shadowsocks.json`:

    {
        "server":["[::0]","0.0.0.0"],
        "server_port":443,
        "local_address": "127.0.0.1",
        "local_port":1080,
        "password":"******",
        "timeout":300,
        "method":"aes-256-cfb",
        "fast_open": false
    }

> update150208: “server” 行只写::0的话就是纯v6连接了……

最后是ipv6，在he.net申请tunnel breaker，因为便宜的VPS动不了内核，于是用[TB-TUN](https://github.com/heyeshuang/tb-tun/)弄一个用户态隧道，见~~[这里](http://www.yangyaping.cn/2014/08/21/ipv6tunnel/)~~[这里](http://daili.ml/centos_shadowsocks_ipv6.html)和[这里](http://ichon.me/post/659.html)，还有init.d的[自启动脚本](http://www.cybermilitia.net/2013/07/22/ipv6-tunnel-on-openvz/)。

> update150409:
> 增加一个[UStun](https://github.com/rejsmont/ustun)的链接；更换了Googlecode的链接
>
> ~~Google带着小姨子code跑了！你王八蛋！你还我血汗码！~~

另外，chrome的[SSH](https://chrome.google.com/webstore/detail/secure-shell/pnhechapfaindjhompbnflcldabbghjo/related?utm_source=chrome-app-launcher-info-dialog)很好用，可以算是*刚换电脑还没有买SSD装arch的人*的福音。

update：听说libev版本的可以节省内存，安装方法在[这里](https://github.com/shadowsocks/shadowsocks-libev#debian--ubuntu)。

update2：从[这里](https://github.com/shadowsocks/shadowsocks/wiki/Connect-to-OpenVPN-over-Shadowsocks)看到可以在shadowsocks上飞OPENVPN，于是：

在服务器运行这个：

    wget git.io/vpn --no-check-certificate -O openvpn-install.sh; bash openvpn-install.sh

然后设中转：

    iptables -A INPUT -s 10.8.0.0/24 -j ACCEPT
    iptables -I FORWARD 1 -s 10.8.0.0/24 -j ACCEPT
    iptables -I FORWARD 2 -d 10.8.0.0/24 -j ACCEPT
    iptables -I FORWARD 3 -j LOG --log-prefix "FORWARD-LOG "
    iptables -I FORWARD 4 -j DROP

把在`/root/`生成的`.ovpn`文件复制到本机，这时我发现chrome并没有自带SCP……

在得到的`.ovpn`文件里加两行：

    socks-proxy 127.0.0.1 1080
    route [SHADOWSOCKS服务器地址] 255.255.255.255 net_gateway

然后去下[客户端](https://openvpn.net/index.php/open-source/downloads.html)，不要手贱点xp版本，否则今天下午就没空写作业了\~

如果windows的shadowsocks客户端支持UDP转发的话，这里就是终点了，否则，请将本机和服务端的`.ovpn`文件（`etcopenvpnserver.ovpn`）修改为tcp模式。

8.23：谨以此博文对领路人致敬。身处寒夜，你们为我们带来了微光。

