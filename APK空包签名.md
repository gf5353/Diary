# java/adb常用命令

标签（空格分隔）： 未分类

---

1.apk空包签名

之前接到这样一个需求，上架搜狗应用市场需要给他们平台提供的一个apk文件，将其用我们的keystore 进行签名，当然其他平台都可以适用。
http://zhushou.sogou.com/open/news-9.html


我在网上查了下，其实很简单，jdk已经跟我们提供好工具了，具体命令如下
```
jarsigner -verbose -keystore [keystorePath] -signedjar [apkOut] [apkIn] [alias]
```

jarsigner命令格式：-verbose输出详细信息 -keystore密钥库位置 -signedjar要生成的文件 要签名的文件 密钥库文件
keystorePath参数代表keyStore的绝对路径，如D:\keystore
apkOut参数代表签名后的apk路径，如D:\signed.apk
apkin参数代表在腾讯应用中心下载的未签名apk，默认名称为tap_unsign.apk
alias参数代表签名用的alias名称（创建keyStore时所填写），如timdong

```
$ jarsigner -verbose -keystore debug.keystore -signedjar test2.apk tap_unsign1.apk timdong
```

2.查看手机CPU信息<br>
cmd——adb shell——cd /proc------cat cpuinfo

3.查看apk签名信息<br>
keytool -printcert -file CERT.RSA

[原文链接][1]
  [1]: http://blog.csdn.net/wed110/article/details/38303637