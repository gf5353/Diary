# APK�հ�ǩ��

��ǩ���ո�ָ����� δ����

---

֮ǰ�ӵ�����һ�������ϼ��ѹ�Ӧ���г���Ҫ������ƽ̨�ṩ��һ��apk�ļ������������ǵ�keystore ����ǩ������Ȼ����ƽ̨���������á�
http://zhushou.sogou.com/open/news-9.html


�������ϲ����£���ʵ�ܼ򵥣�jdk�Ѿ��������ṩ�ù����ˣ�������������
```
jarsigner -verbose -keystore [keystorePath] -signedjar [apkOut] [apkIn] [alias]
```

jarsigner�����ʽ��-verbose�����ϸ��Ϣ -keystore��Կ��λ�� -signedjarҪ���ɵ��ļ� Ҫǩ�����ļ� ��Կ���ļ�
keystorePath��������keyStore�ľ���·������D:\keystore
apkOut��������ǩ�����apk·������D:\signed.apk
apkin������������ѶӦ���������ص�δǩ��apk��Ĭ������Ϊtap_unsign.apk
alias��������ǩ���õ�alias���ƣ�����keyStoreʱ����д������timdong

```
$ jarsigner -verbose -keystore debug.keystore -signedjar test2.apk tap_unsign1.apk timdong
```

[ԭ������][1]
  [1]: http://blog.csdn.net/wed110/article/details/38303637