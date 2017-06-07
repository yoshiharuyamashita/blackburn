---

title: '用于OPENWRT的流量监控脚本：wrtbwmon'
author: HeYSH
type: post
date: 2014-03-02T11:38:02+00:00
url: /2014/03/02/用于openwrt的流量监控脚本：wrtbwmon/
aliases:
  - /2014/03/02/用于openwrt的流量监控脚本：wrtbwmon/
cleanretina_sidebarlayout:
  - default
duoshuo_thread_id:
  - "1239563020875595816"
dsq_thread_id:
  - "3667750326"
categories:
  - 未分类

---
UPDATE at 15年平安夜：<https://wiki.openwrt.org/doc/howto/wrtbwmon>

------------------------------------------------------------------------

在某次坑爹的网费改革之后校园网的免费流量变成了20G，于是流量监控这一需求变得迫切起来。Google之后，发现了这个脚本：[wrtbwmon](http://code.google.com/p/wrtbwmon/)。不过这个是为dd-wrt设计的，而且也很久没有更新过了，要进行一些小修改才能用。


> 比如第24行，`nvram`在我这里挂掉了，于是我简单粗暴的把它改成了`eth1``br-lan`；还有那个`publish`函数，似乎是读取`/etc/dnsmasq`工作的，在OpenWRT上的对应文件似乎是`/etc/dhcp.leases`什么的，相应的167行也稍稍修改了一下……

TL;DR：请在[这里](https://gist.github.com/heyeshuang/9305089)下载修改过的版本，在本人的2成新db-120上测试通过。

把上面那东西扔到`/bin`里之后，在crontab里添上这么一段：

    * * * * * /bin/wrtbwmon setup br0
    */30 0-3 * * * /bin/wrtbwmon update /tmp/usage.db peak
    */30,59 4-8 * * * /bin/wrtbwmon update /tmp/usage.db offpeak
    */30 9-23 * * * /bin/wrtbwmon update /tmp/usage.db peak
    */30 * * * * /bin/wrtbwmon publish /tmp/usage.db /tmp/usage.htm /tmp/dhcp.leases
    30 * * * * cp /tmp/usage.db /root/usage.db
    * * * * * [ ! -f /tmp/usage.db ] && cp /root/usage.db /tmp/usage.db

[自带的教程](http://code.google.com/p/wrtbwmon/wiki/Deploying)写的crontab似乎跟OpenWRT不兼容……*这里的一定是雨林木风精简版OpenWRT！*

又及：为了凑字数，关于如何在nat后面使用isatap的方法参见[这里](http://wiki.tuna.tsinghua.edu.cn/IsatapBehindNat)

