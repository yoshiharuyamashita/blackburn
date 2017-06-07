---

title: 'pentadactyl 和 Firefox 43'
author: HeYSH
type: post
date: 2015-12-17T13:03:26+00:00
url: /2015/12/17/pentadactyl_n_firefox_43/
aliases:
  - /2015/12/17/pentadactyl_n_firefox_43/
dsq_thread_id:
  - "4411610995"
categories:
  - 未分类

---
UPDATE:
<https://addons.mozilla.org/en-US/firefox/addon/pentadactyl-nightly-unofficial/>别人的第三方编译版本

------------------------------------------------------------------------

TL;DW: [百度盘](http://pan.baidu.com/s/1jH0zrhG)，[GOOGLE DRIVE](https://drive.google.com/file/d/0B5jbrghmIinDU1gtdGdHVG40WFk/view?usp=sharing)，编译好，签过名的版本，MaxVersion改到44；当然，不负任何责任。

众所周知，pentadacytl的[nightly build](http://5digits.org/nightlies)已经坏掉好久了，现在的build在[GitHub](https://github.com/ffledgling/dactyl-build/releases)上，通过Travis CI编译，不明真相的我看得一愣一愣的。

另外，Firefox 43要求强制签名，幸好步骤还是挺简单的，先在install.rdf里把`em:id="pentadactyl@mod"`随便改一下，然后去[这里](https://addons.mozilla.org/zh-CN/developers/addon/submit/2)上传就行了。别忘了把“不要在此网站上展示我的附加组件”勾上。

另外，firefox也发布了签名工具[jpm](https://developer.mozilla.org/en-US/Add-ons/SDK/Tools/jpm#jpm_sign)，好像也可以放到Travis CI里面……
