---

title: '邪恶的Archlinux'
author: HeYSH
type: post
date: 2013-05-17T07:47:31+00:00
url: /2013/05/17/混乱邪恶的archlinux/
aliases:
  - /2013/05/17/混乱邪恶的archlinux/
cleanretina_sidebarlayout:
  - default
duoshuo_thread_id:
  - "1239563020875595802"
dsq_thread_id:
  - "3667750590"
categories:
  - linux
tags:
  - arch
  - linux
  - 吐槽

---
前几天archlinux更新后无法启动，提示”/bin/systemd not exist”，于是乖乖等官网说明，顺理成章的没等到。于是开始google，在g+发现一条线索：那群变态好像把`/bin/systemd`移到`/usr/lib/systemd/systemd`里了……\

于是解决方案是：在grub按e，把`/bin/systemd`换成`/usr/lib/systemd/systemd`就行了；进来之后，还要改`/etc/default/grub`，以及`grub-mkconfig`……\

所以说你们折腾这个到底是为什么呀？觉得系统太稳定还是想玩弄可怜的系统管理员？？\

用一张图表达我的感想：

![evil](/evil.png)