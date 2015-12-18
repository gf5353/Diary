# Android打包说明

标签（空格分隔）： 未分类

---

1. build.gradle配置说明<br>
-----------------------

**app下的build.gradle**

根据buildTypes分为debug/preview/release 打包默认路径在如上目录下<br>
**debug:**<br>
开发内部使用,无法通过QQsdk登录客户端<br>
正常签名<br>
不混淆<br>
使用友盟测试key<br>
log[LOG_DEBUG]状态打开<br>
白名单[CAMERA_DEBUG]关闭<br>

**preview:**<br>
通常为内部预览版,提交测试使用<br>
正常签名<br>
不混淆<br>
使用友盟测试key<br>
打包发往友盟升级后台,提供测试环境测试<br>
log[LOG_DEBUG]状态打开<br>
白名单[CAMERA_DEBUG]关闭<br>

**release:**<br>
正式发布版,打一个生成加固包，再打出相对数量的渠道包<br>
正常签名<br>
混淆<br>
使用友盟正式key<br>
打包发往友盟升级后台,提供生产环境测试<br>
log[LOG_DEBUG]状态关闭<br>
白名单[CAMERA_DEBUG]打开<br>

productFlavors：多渠道出一个包即可，打完后生成加固包


----------


 **全局的build.gradle**
 
```
ext {
    compileSdkVersion = 22//编译sdk版本
    buildToolsVersion = "23.0.2"//编译Tools版本
    minSdkVersion = 16//应用最低支持版本，此处为June 2012: Android 4.1
    targetSdkVersion = 22//目标版本和编译版本相同
    versionCode = 2015121611//打包主要修改，生成规则：年份|月份|日期|小时，依版本递增，注（新版本低于旧版本无法提示升级）
    versionName = "3.0.19"//版本号release按照正式来，preview低于正式发包前依次迭代，debug不打
}
```

2. 加固包
------
[腾讯应用加固](http://www.qcloud.com/product/cr.html)
操作步骤
上传应用安装包
1. 点击添加版本按钮，在弹出框中选择待上传的APK，安装包不大于100M
![yingyongjiagu_01.png][1]
2. 安装包上传完毕，然后点击确定，开始加固
![yingyongjiagu_02.png][2]
![此处输入图片的描述][3]
下载加固包并重签名
1. 状态变化为加固成功后，下载加固后的安装包
![yingyongjiagu_04.png][4]
2. 对加固包进行重签名，如果要使用不同证书签名，需要删除加固包中的META-INF文件夹,具体签名方法，请[参考加固后重签名][5]<br>
[参照连接][6]
3. 多渠道<br>
------
链接：http://pan.baidu.com/s/1pKx7srp 密码：8fzm<br>
multTool工具<br>
将加固后的母包，用鼠标拖进多渠道打包工具，并根据情况选择打包参数。<br>
![这里写图片描述](http://img.blog.csdn.net/20151218135635217)
图中这段参数是修改 AndroidManifest.xml 里的<meta-data>结点，将 android:name 属性
为 UMENG_CHANNEL 的结点的 android:value 属性分别改为 chanel_2,chanel_3,chanel_4依次类推，然后批量生成渠道包，此时的渠道包是没有签名的，后续将进行渠道包批量签名。<br>

*注（详细操作文档见压缩包）*
4. 签名<br>
-----
链接：http://pan.baidu.com/s/1pKx7srp 密码：8fzm<br>
sign工具<br>
首次打开软件，作者显示Administrator，这时是没有导入keystore的<br>
![这里写图片描述](http://img.blog.csdn.net/20151218140400392)<br>
点击导入选择自己应用的keystore文件<br>
![这里写图片描述](http://img.blog.csdn.net/20151218140537091)<br>
输入证书的密码<br>
![这里写图片描述](http://img.blog.csdn.net/20151218140649057)<br>
然后选择相应的证书<br>
![这里写图片描述](http://img.blog.csdn.net/20151218140722194)<br>
再次输入证书的密码<br>
![这里写图片描述](http://img.blog.csdn.net/20151218140649057)<br>
导入成功<br>
![这里写图片描述](http://img.blog.csdn.net/20151218140829867)<br>
此时作者这栏会变成证书的作者<br>
![这里写图片描述](http://img.blog.csdn.net/20151218140922669)<br>

导入一次即可，之后签名都不需要再次导入了，接下来是进行批量签名
![这里写图片描述](http://img.blog.csdn.net/20151218141029636)<br>
将上述加固后的渠道包拖入到位置中进行签名
![这里写图片描述](http://img.blog.csdn.net/20151218141143811)<br>
提示签名成功即可完成签名，此时可以通过安装apk进入应用后面检测渠道的正确性

*注（详细操作文档见压缩包）*
  [1]: http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/yingyongjiagu_01.png
  [2]: http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/yingyongjiagu_02.png
  [3]: http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/yingyongjiagu_03.png
  [4]: http://qzonestyle.gtimg.cn/qzone/vas/opensns/res/img/yingyongjiagu_04.png
  [5]: http://www.qcloud.com/wiki/%E5%8A%A0%E5%9B%BA%E5%90%8E%E9%87%8D%E7%AD%BE%E5%90%8D
  [6]: http://www.qcloud.com/wiki/%E5%BA%94%E7%94%A8%E5%8A%A0%E5%9B%BA