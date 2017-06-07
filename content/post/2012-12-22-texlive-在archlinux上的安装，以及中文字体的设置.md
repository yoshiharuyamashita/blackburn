---

title: 'Texlive 在archlinux上的安装，以及中文字体的设置'
author: HeYSH
type: post
date: 2012-12-21T16:38:48+00:00
url: /2012/12/22/texlive-在archlinux上的安装，以及中文字体的设置/
aliases:
  - /2012/12/22/texlive-在archlinux上的安装，以及中文字体的设置/
duoshuo_thread_id:
  - "1239563020875595790"
dsq_thread_id:
  - "3760147852"
categories:
  - linux
tags:
  - arch
  - ctex
  - linux
  - tex

---
> texmacs已经不能满足我了！

> 其实是想着反正这个软件已经挺难用了，要不就直接去挑战大魔王吧！

> 然后发现大魔王令人绝望的实力

> 然后用S/L大法加google作弊器成功——安装了字体

> 结果我还是不会用tex

> 所以我下了lyx

> \#期末考试就要到了我还在弄这个\#

> \#挂科预感up（大）\#

> 我说这个又没人爱听

> 反正也不会有人来

> fin

> 骗你的

> 这里不是只有一个活人吗……不会有什么“你”在啦

> 好吧让我~~们~~进入正题。

> 其实我一开始以为直接pacman就好了

> 但是后来我发现自己太甜了

> 于是我就下了texlive的镜像

> 后来发现直接安可能也可以？？

按照[这里](http://www.road2stat.com/cn/tex/archtex.html)的安装方式\

~~~bash
su –
wget -c http://mirrors.ustc.edu.cn/CTAN/systems/texlive/Images/texlive2012.iso
mkdir /mnt/tex
mount -o loop texlive2012.iso /mnt/tex/
cd /mnt/tex/
./install-tl
vim /etc/profile #在这里要设置全局变量PATH，加上/usr/local/texlive/2012/bin/i386-linux，否则找不到tlmgr……
tlmgr option repository http://mirrors.ustc.edu.cn/CTAN/systems/texlive/tlnet
tlmgr update –self
tlmgr update –all
umount /mnt/tex
rm -rf /mnt/tex
~~~

然后发现没有字体……

然后在[这里](http://tug.org/texlive/doc/texlive-zh-cn/texlive-zh-cn.pdf)发现要：



> 将 texlive-fontconfig.conf 文件复制到
> /etc/fonts/conf.d/09-texlive.conf，
> 运行 fc-cache -fsv 以root的名义

接下来xetex就会提示你缺少字体了，是不是很高兴？

——才怪咧！

然后，你要用yaourt安装ttf-ms-fonts-zh_cn这个包——

然后fc-list|grep sim和fc-list|grep SIM各一次——

然后`sudo vim /usr/local/texlive/2012/texmf-dist/tex/latex/ctex/fontset/ctex-xecjk-winfonts.def`

把里面奇怪的\[SIMKAI.TTF\]和\[SIMFANG.TTF\]都换成刚才写着“楷体”和“仿宋”行中的英文名，我的是KaiTi\_GB2312和FangSong\_GB2312

编译用例：

~~~tex
\documentclass{ctexart}
\begin{document}
为什么大家都在这里写“你好”啊……我一点也不好……而且也没有什么“你”……
\end{document}
~~~

用的编译命令是xelatex……

然后……要是提示缺少`Adobe Song Std`什么的，应该`yaourt acroread-font-chinese-simplified`就行了吧……



啊啊，从这个过程里，我好像看到了我短暂的人生……越是精于算计，就越可能出现意想不到的状况……

> 老子不做人了！TeTe！

> 然后就想起这里还有一篇论文要写……

> 世界末日没有来真是令人沮丧啊……我好想变成橙汁啊……

> 最后祝你身体健康，再见

