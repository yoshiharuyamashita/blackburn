---

title: 'phpwind论坛刷分脚本（可用于openwrt）'
author: HeYSH
type: post
date: 2012-09-11T04:56:26+00:00
url: /2012/09/11/phpwind论坛刷分脚本（可用于openwrt）/
aliases:
  - /2012/09/11/phpwind论坛刷分脚本（可用于openwrt）/
cleanretina_sidebarlayout:
  - default
duoshuo_thread_id:
  - "1239563020875595783"
dsq_thread_id:
  - "3667750831"
categories:
  - python

---
用Python2写成，为什么不用Lua？因为我不会



    '''
    Created on 2012-9-10
    @author: hh
    '''
    import cookielib
    import urllib2
    import urllib
    import time
    username="Chetter.Hummin"
    password="password"
    def login(usr, pwd):
        'login function'
        cj = cookielib.CookieJar()
        opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
        opener.addheaders = [('User-agent','Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.1 (KHTML, like Gecko) Chrome/21.0.1180.89 Safari/537.1')]
        url_login = 'http://bbs.sarabalst.com/2b/login.php'
        body={"step":"2","pwuser":usr,"cktime":"31536000","pwpwd":pwd,"lgt":"0"}
        print 'login to get cookies'
        urllib2.install_opener(opener)
        req = urllib2.Request(url_login,urllib.urlencode(body))
        resp = urllib2.urlopen(req)
        #print (resp.read())

    if __name__ == '__main__':
        login(username,password)
        print "login success"
        print (time.strftime('%Y-%m-%d %H:%M',time.localtime(time.time())))
        for i in range(0,23):
            try:
                str=urllib2.urlopen("http://bbs.sarabalst.com/2b/",timeout=100).read()
                #print "success"
            except:
                str=""
                #print "fail"
            if str!="":
                print str
                print "refresh success"
            else:
                print "refresh fail"
            print (time.strftime('%Y-%m-%d %H:%M',time.localtime(time.time())))
            time.sleep(300);


在openwrt上测试成功。理论上可以加入crontab，现在还没测试（时间不够）\
update :鉴于论坛和路由器双重不给力，给urllib2设了超时

