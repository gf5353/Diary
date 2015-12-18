我的安卓学习过程

http://www.bubuko.com/infodetail-1118953.html

http://www.csdn.net/article/2015-12-09/2826427

去除AndroidStudio中libpng关于iCCP的警告
http://blog.sinzy.net/ifyr/entry/23230



Warning: debug info can be unavailable. Please close other application using<br>
解决办法:<br>
```
adb kill-server
adb kill-start


* daemon not running. starting it now on port 5037 *
* daemon started successfully 

5037端口被占用
查看端口占用<br>
netstat   -ano|findstr  5037
 

```