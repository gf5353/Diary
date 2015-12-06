#�������Android Gradle 

��ǩ���ո�ָ����� δ����

ԭ���� ���д�ĺܰ���������
http://www.jayfeng.com/2015/11/07/Android%E6%89%93%E5%8C%85%E7%9A%84%E9%82%A3%E4%BA%9B%E4%BA%8B/#comments

---

�µ�android��������������Gradle�������ߣ������˿����߽��й�����ͬ��Ӧ�ð汾����ɲ�ͬ�����󡣣��Ӵ˶�汾����ʹ�ࣩ

1. gradle�����﷨
-------------


----------


�½���Ŀ��Ĭ�ϵ������ļ�ճ����

```
apply plugin: 'com.android.application'
android {
    compileSdkVersion 22
    buildToolsVersion "19.1.0"
    defaultConfig {
        applicationId "org.guf.mediagesturedetector"
        minSdkVersion 22
        targetSdkVersion 22
        versionCode 1
        versionName "1.0"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    testCompile 'junit:junit:4.12'
    compile 'com.android.support:appcompat-v7:22.2.1'
    compile 'com.android.support:design:22.2.1'
}
```

**apply plugin**��
�ҵ����Ϊ�����汾��������Ϊһ����ͨ�İ�׿Ӧ�ó����ʱ��Ϊ
apply plugin: 'com.android.application'
������Ϊ��׿modle��ʽΪapply plugin: 'com.android.library'
��Ȼ��򵥵�ֻ��java��Ŀ��Ϊ apply plugin: 'java'

**android**
�����ǩ����Ҫ������Ӧ�ó�������sdkapi�汾��sdkbuildTools�İ汾
defaultConfig �������manifests��ı�������
buildTypes �����������汾������
��Ȼ��Щ�ǿ�����ģ���������˵��

**dependencies**
android studio������������
�������߸������ṩ�����ַ�ʽ����������������gradle�����ĺô�
![��Ŀ�Ҽ�](http://img.blog.csdn.net/20151205010619779)
��һ����ͨ��maven�ֿ��������ߵ������⣬�Ƚ��������磬���Ǹ��±༭������ֻ��Ҫ�޸İ汾�ż���

�ڶ��������ļ��ķ�ʽ����jar�ļ����������eclipseת�����Ļ����õ������ַ�ʽ����Ȼ������Ѿ�������
compile fileTree(dir: 'libs', include: ['*.jar'])
��ô�������ֶ�����ӣ����Զ�����libs���jar��

�����־���������Ŀ�е�modle��Ŀ���������ི����eclipse�����library����

2. ͨ��gradle�滻AndroidManifest�е�ռλ��
-------------

----------

```
  <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="${APP_NAME}"
        android:theme="@style/AppTheme">
        
```   
��������Ҫ��AndroidManifest�����ռλ��'APP_NAME',ͨ��gradle����Ĺ����У�ͨ��bulid.gradle�޸�����
manifestPlaceholders=[ռλ������Ҫ�޸ĵ�ֵ]
```
buildTypes {
        release {
            manifestPlaceholders = [APP_NAME: 'test']
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
```   
3. ��������ǩ����Ϣ
-------------

----------  
����ǩ����ص���Ϣ,ֱ��д��gradle��Ȼ����,�ر���һЩ��Դ��Ŀ��������ӵ�gradle.properties:

    RELEASE_KEY_PASSWORD=xxxx
    RELEASE_KEY_ALIAS=xxx
    RELEASE_STORE_PASSWORD=xxx
    RELEASE_STORE_FILE=../.keystore/xxx.jks
Ȼ����build.gradle�����ü��ɣ�
```
android {
    signingConfigs {
        release {
            storeFile file(RELEASE_STORE_FILE)
            storePassword RELEASE_STORE_PASSWORD
            keyAlias RELEASE_KEY_ALIAS
            keyPassword RELEASE_KEY_PASSWORD
        }
    }
}
```   
4. ��汾��������
-------------

---------- 
�汾���������̷�Ϊ��
```flow
st=>start: ����
op=>operation: �ع����
cond=>condition: ������������?
e=>end: ����

st->op->cond
cond(yes)->e
cond(no)->op
```
���ԣ����ǵİ汾���Է�Ϊ���ְ汾
debug-�������԰�
preview-����Ԥ����
release-��ʽ��

ÿ���汾�����в�ͬ��Ҫ�󣬲��԰治��Ӱ����������������ͨ���Ĵ������л����Ի������������������������Զ���Build Type��ɴ���汾����

![����дͼƬ����](http://img.blog.csdn.net/20151205015447245)
�����Ŀ¼�»��и�BuildConfig�����ǿ����������������ֵ���л�ȫ��log�Ŀ��أ���֤������������й©log��־
```
    buildTypes {
        debug {
            buildConfigField "boolean", "DEBUG", "true"
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        release {
            buildConfigField "boolean", "DEBUG", "false"
            minifyEnabled true
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
```
5. build type�еĶ��Ʋ���
-------------

---------- 
�������м������ڹ������õ��ģ�
```
android {
        debug {
            manifestPlaceholders = [app_label:"@string/app_name_debug"]
            applicationIdSuffix ".debug"
            minifyEnabled false
            signingConfig signingConfigs.debug
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        release {
            manifestPlaceholders = [app_label:"@string/app_name"]
            minifyEnabled true
            shrinkResources true
            signingConfig signingConfigs.release
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        preview{
            manifestPlaceholders = [app_label:"@string/app_name_preview"]
            applicationIdSuffix ".preview"
            debuggable true // ����debug��Ϣ
            minifyEnabled true
            shrinkResources true
            signingConfig signingConfigs.preview
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}
```
��Щ���õ�̫���ˣ���΢����һ�£�

    // minifyEnabled ��������
    // shrinkResources ȥ��������Դ
    // signingConfig ǩ��
    // proguardFiles ��������
    // applicationIdSuffix ����APP ID�ĺ�׺
    // debuggable �Ƿ���������Ϣ
    // ... ...
    
6. �๤��ȫ������
-------------

---------- 
���Ų�Ʒ�������̿�������һ�״�����Ҫ֧�ֶ����Ʒ��̬�������Ҫ�������Ҫ���뵽һ��Library��Ȼ�����Library��չ����App Module��
����ÿ��module��build.gradle������������룺
```
android {
    compileSdkVersion 22
    buildToolsVersion "23.0.1"

    defaultConfig {
        minSdkVersion 10
        targetSdkVersion 22
        versionCode 34
        versionName "v2.6.1"
    }
}
```
������sdk��build tool��target sdk�ȣ�����module��Ҫ���ģ��ǳ����鷳������Ҫ���ǣ����������ǣ����յ���app module֮��Ĳ��첻ͳһ��Ҳ���ɿء�
ǿ���gradle�����1.1.0֧��ȫ�ֱ����趨��һ�ٽ����������⡣
����project�ĸ�Ŀ¼�µ�build.gradle����extȫ�ֱ���:
```
ext {
    compileSdkVersion = 22
    buildToolsVersion = "23.0.1"
    minSdkVersion = 10
    targetSdkVersion = 22
    versionCode = 34
    versionName = "v2.6.1"
}
```
Ȼ���ڸ�module��build.gradle���������£�
```
android {
    compileSdkVersion rootProject.ext.compileSdkVersion
    buildToolsVersion rootProject.ext.buildToolsVersion

    defaultConfig {
        applicationId "com.xxx.xxx"
        minSdkVersion rootProject.ext.minSdkVersion
        targetSdkVersion rootProject.ext.targetSdkVersion
        versionCode rootProject.ext.versionCode
        versionName rootProject.ext.versionName
    }
}
```
Ȼ��ÿ���޸�project�����build.gradle����ʵ��ȫ��ͳһ���á�

7. �Զ��嵼����APK����
-------------

---------- 
Ĭ��android studio���ɵ�apk����Ϊapp-debug.apk����app-release.apk�����ж��������ʱ����Ҫͬʱ���50����������ʱ�򣬾��鷳�ˣ���֪��˭��˭�ˡ�
���ʱ�򣬾���Ҫ�Զ��嵼����APK�����ˣ���ͬ�����������APK���ļ���Ӧ���ǲ�һ���ġ�
```
android {
    // rename the apk with the version name
    applicationVariants.all { variant ->
        variant.outputs.each { output ->
            output.outputFile = new File(
                    output.outputFile.parent,
                    "ganchai-${variant.buildType.name}-${variant.versionName}-${variant.productFlavors[0].name}.apk".toLowerCase())
        }
    }
}
```
��apk̫��ʱ������ܰ�apk��debug��release��preview��һ����͸����ˣ���ʵ�ϣ���������������������ˣ�һ��������Ҫ������ʮ���汾���ˣ�debug��release�汾ȫ����һ��û������������ࣩ���򵥣�
```
android {
    // rename the apk with the version name
    // add output file sub folder by build type
    applicationVariants.all { variant ->
        variant.outputs.each { output ->
            output.outputFile = new File(
                    output.outputFile.parent + "/${variant.buildType.name}",
                    "ganchai-${variant.buildType.name}-${variant.versionName}-${variant.productFlavors[0].name}.apk".toLowerCase())
        }
    }
}
```
����������������ganchai-dev-preview-v2.4.0.0.apk������ʽ�İ��ˣ�preview�İ���Ȼ�ͷ���preview���ļ����£��������ˡ�

8. ���������
-------------

---------- 
����������Ĺؼ�֮�����ڣ����岻ͬ��product flavor, ����AndroiManifest�е�channel��������滻Ϊ��Ӧ��flavor��ʶ��
```
android {
    productFlavors {
        dev{
            manifestPlaceholders = [channel:"dev"]
        }
        official{
            manifestPlaceholders = [channel:"official"]
        }
        // ... ...
        wandoujia{
            manifestPlaceholders = [channel:"wandoujia"]
        }
        xiaomi{
            manifestPlaceholders = [channel:"xiaomi"]
        }
        "360"{
            manifestPlaceholders = [channel:"360"]
        }
}
```
ע��һ�㣬�����flavor����������ֿ�ͷ��������������������
����һ�£���������һϵ�е�Build Variant��:

    devDebug
    devRelease
    officialDebug
    officialRelease
    wandoujiaDebug
    wandoujiaRelease
    xiaomiDebug
    xiaomiRelease
    360Debug
    360Release
����debug, release��gradleĬ���Դ�������build type, ��һ�ڻ������˵����
ѡ��һ�������ܱ������Ӧ������apk�ˡ�    

9. ��̬����һЩ������Ϣ
-------------

----------     
������ѵ�ǰ�ı���ʱ�䡢����Ļ��������µ�commit�汾��ӵ�apk������Щ��Ϣ�ֲ���д�ڴ����ǿ���gradle�����Ҵ�����ܵ����ţ�
```
android {
    defaultConfig {
        resValue "string", "build_time", buildTime()
        resValue "string", "build_host", hostName()
        resValue "string", "build_revision", revision()
    }
}

def buildTime() {
    return new Date().format("yyyy-MM-dd HH:mm:ss")
}
def hostName() {
    return System.getProperty("user.name") + "@" + InetAddress.localHost.hostName
}
def revision() {
    def code = new ByteArrayOutputStream()
    exec {
        commandLine 'git', 'rev-parse', '--short', 'HEAD'
        standardOutput = code
    }
    return code.toString()
}
```
��������ʵ���˶�̬�������3���ַ�����Դ: build_time��build_host��build_revision, Ȼ���������ط������������ַ���һ��

