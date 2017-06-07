---

title: 'IPv6 season 2: 在DHCPv6网络环境下的OpenWRT Chaos Calmer'
author: HeYSH
type: post
date: 2015-09-09T13:58:27+00:00
url: /2015/09/09/ipv6-season-2-在dhcpv6网络环境下的openwrt-chaos-calmer/
aliases:
  - /2015/09/09/ipv6-season-2-在dhcpv6网络环境下的openwrt-chaos-calmer/
dsq_thread_id:
  - "4112987006"
categories:
  - web
tags:
  - ipv6
  - OpenWRT
  - web

---
背景：桥接3秒断一次的渣网，以及经常在我博客中出现的5手db120；还有经常更新以后把老版本脚本删掉的OpenWRT，这里用的是Chaos Calmer 15.05-rc3。

大概上思路和[这里](http://talk.withme.me/?p=51)一样，因为学校给的地址位数只有/64，不够再去划分子网，所以要去启用邻居发现协议；但是因为`6ndp`,`ndppd`和`radvd`都已经被始乱终弃，现在它们的功能被odhcpd给代替了。具体上，`/etc/config/dhcp`的关键几行大概应该是这样：

    # /etc/config/dhcp:
    config dhcp 'lan'
            option interface 'lan'
            option start '100'
            option limit '150'
            option leasetime '12h'
    #       option dhcpv6 'server'
            option ra 'relay'
            option ndp 'relay'
    #config dhcp 'wan'
            #option interface 'wan'
            #option ignore '1'
    config dhcp 'wan6'
            option ra 'relay'
            option ndp 'relay'
            option master '1'

另外，还需要把`luci`的`interface`页面下的`IPv6 ULA-Prefix`删掉。

现在的问题是，LAN口和WAN口的IP地址是一样的，而且客户机必须先ping一下这个地址才能连接外网，有时候路由还要重启`/etc/init.d/odhcpd`；不管了，我先在这里存个盘。

有人说relay-&gt;hybrid也能成功的样子……我还没有测试过。

参考：

<http://bbs.pku.edu.cn/new/bbs/article/showthread/Networking/15501646?1>

<http://ict.jingyan.info/openwrt-%e7%94%a8odpcpd%e9%85%8d%e7%bd%aerelay-%e6%96%b9%e5%bc%8f-ipv6/>（链接不知道为什么已经失效了）

20160321更新：odhcp烂的抠脚，转用邪恶的IPV6 NAT，见[这里](https://wiki.openwrt.org/doc/howto/ipv6.nat6)

