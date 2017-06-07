---

title: '总结：简单的vCal/iCalendar/.ics格式说明'
author: HeYSH
type: post
date: 2012-06-25T08:12:57+00:00
url: /2012/06/25/总结：简单的vcalicalendar-ics格式说明/
aliases:
  - /2012/06/25/总结：简单的vcalicalendar-ics格式说明/
duoshuo_thread_id:
  - "1239563020875595779"
dsq_thread_id:
  - "3667750938"
categories:
  - 奇奇怪怪
tags:
  - iCalendar
  - vCal
  - 格式解析

---
E文好的话建议去看直接去看IETF的[RFC5545](http://tools.ietf.org/html/rfc5545)定义;\
中文版：


> [政府文件：中华人民共和国通信行业标准移动互联网可移动终端数据同步业务技…（下略）](http://www.ccsa.org.cn/publish/download_bp.php?stdtype=yd1&sno=92 "总而言之就是标准")
>
> [某人翻译的标准文档（百度文库）](http://wenku.baidu.com/view/c52d284c2e3f5727a5e9621e.html)

ical格式大概是这样的：



    BEGIN:VCALENDAR

    PRODID:-//HeYSH//HeYSH Calendar 70.9054//CN

    VERSION:2.0

    CALSCALE:GREGORIAN

    METHOD:PUBLISH

    X-WR-CALNAME:课程表

    X-WR-TIMEZONE:Asia/Shanghai

    X-WR-CALDESC:

    BEGIN:VTIMEZONE

    TZID:Asia/Shanghai

    X-LIC-LOCATION:Asia/Shanghai

    BEGIN:STANDARD

    TZOFFSETFROM:+0800

    TZOFFSETTO:+0800

    TZNAME:CST

    DTSTART:19700101T000000

    END:STANDARD

    END:VTIMEZONE

    BEGIN:VEVENT

    DTSTART;TZID=Asia/Shanghai:20120901T092000

    DTEND;TZID=Asia/Shanghai:20120901T105000

    DTSTAMP:20120622T160054Z

    UID:%u4F20%u70ED%u5B66%20%u5BF9%u6D41%u5B9E%u9A8C35@第 1 次

    CREATED:20120622T154824Z

    DESCRIPTION:教师：王五n

    LAST-MODIFIED:20120622T160041Z

    LOCATION:大礼堂

    STATUS:CONFIRMED

    SUMMARY:实验2

    END:VEVENT

    END:VCALENDAR



基本上只要修改中文部分的内容就好了



#### tips：



-   PRODID按照格式随意改就好
-   UID是一件事情的绝对标识，对格式没有要求，只要不重复即可
-   重复事件可用RRLUE字段，具体见所附文档。但是好像不支持“1,2,5-9,13,16周”这样猎奇的重复，所以对本人并没有什么用处

> 还是老老实实一个一个添加吧……不过删除起来也相应的麻烦了许多。

-   我~~们~~尚不知道那天所看到的~~花的名字~~DTSTAMP的用处



最后补一些相关代码段（javascript）：

~~~javascript
$vCalArea.append('BEGIN:VCALENDARnPRODID:-//HeYSH//THU Calendar 0.0002//CNnVERSION:2.0nCALSCALE:GREGORIANnMETHOD:PUBLISHnX-WR-CALNAME:课程表nX-WR-TIMEZONE:Asia/ShanghainX-WR-CALDESC:nBEGIN:VTIMEZONEnTZID:Asia/ShanghainX-LIC-LOCATION:Asia/ShanghainBEGIN:STANDARDnTZOFFSETFROM:+0800nTZOFFSETTO:+0800nTZNAME:CSTnDTSTART:19700101T000000nEND:STANDARDnEND:VTIMEZONEn');
/***************生成文件头****************/
$vCalArea.append("BEGIN:VEVENTnDTSTART;TZID=Asia/Shanghai:" + strBT + "nDTEND;TZID=Asia/Shanghai:" + strET + "nDTSTAMP:20120622T160054ZnUID:" + uid + "nCREATED:20120622T154824ZnDESCRIPTION:" + Data.courseInfo + "nLAST-MODIFIED:20120622T160041ZnLOCATION:" + Data.place + "nSTATUS:CONFIRMEDnSUMMARY:" + Data.courseName + "nEND:VEVENTn")
/****************VEVENT部分***************/
$vCalArea.append('END:VCALENDAR');
/****************文件尾****************/
~~~

全部脚本见<http://code.google.com/p/js-thu-cal-outputer/>

