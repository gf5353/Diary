# Git��������

��ǩ���ո�ָ����� δ����

---

���������������ӷ���������http://git-scm.com/download/
��װ�Ͳ�ϸ˵��

1. ����Git Config
--------
Ӧ�ó���Git Bash �������һ���git�����ļ����������棬���õ��ļ�·��һ����C���û��µ�.gitconifg
��������ߵ���C:\Users\Guf\.gitconfig
��Ȼ���ǿ�������ȫ�ֵĻ�����Ե�ǰ�ֿ�ģ�����������������ȫ�ֵ�config

```
#�о���������
git config -1 

#����ʹ��git�ֿ����Ա����
git config --global user.name "Your Name Comes Here"

#����ʹ��git�ֿ����Աemail
git config --global user.email 562401002@qq.com

#���õ����� Ĭ��15����
git config --global credential.helper cache 

#�޸Ļ���ʱ��
git config --global credential.helper 'cache --timeout=3600'  

git config --global color.ui true
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global core.editor "mate -w"    # ����Editorʹ��textmate

#�û���git�����ļ�~/.gitconfig

```
2. �����汾��
--------


```
#����Ŀ¼��ɿ��Թ���Ĳֿ�
git init

#CloneԶ�̰汾��  
git clone https://github.com/gf5353/Diary.git

#���Զ�̰汾��origin���﷨Ϊ git remote add [shortname] [url]  
git remote add origin https://github.com/gf5353/Diary.git 
  
#�鿴Զ�ֿ̲�  
git remote -v  
```

3. �ύ���汾��
--------


```
 # �������ļ��޸��ύ�������ݴ���
git add <file>       

#�������޸Ĺ��Ĺ����ļ��ύ�ݴ���    
git add .  

#�鿴�ļ�״̬  
git status 
# �Ӱ汾����ɾ���ļ� 
git rm <file>        

# �Ӱ汾����ɾ���ļ�������ɾ���ļ�  
git rm <file> --cached

#�����ύע��������е��
git rm -r --cached . 

#�ύ����޸�  
git commit �Cm "���ע��"  

#������ĸ��µ�Զ�̷�����,�﷨Ϊ git push [Զ����] [���ط�֧]:[Զ�̷�֧]  
git push origin master   
```
4. ����ع�
--------
```
#ͼ�ι������ ��Ҫ��Child
gitk 
# ���ݴ����ָ��������ļ� 
git reset <file>   
# ���ݴ����ָ��������ļ�  
git reset -- .      
# �ָ����һ���ύ����״̬���������ϴ��ύ������б����޸�  
git reset --hard   
```

5. �鿴�ύ��¼
--------
```
git log  
# �鿴���ļ�ÿ���ύ��¼  
git log <file>     
# �鿴ÿ����ϸ�޸����ݵ�diff
git log -p <file>     
# �鿴���������ϸ�޸����ݵ�diff  
git log -p -2       
#�鿴�ύͳ����Ϣ  
git log --stat      
```
6. �鿴�ļ�diff
--------
```
# �Ƚϵ�ǰ�ļ����ݴ����ļ�����
git diff <file>     
git diff

# �Ƚ������ύ֮��Ĳ���
git diff <$id1> <$id2>   

# ��������֧֮��Ƚ�
git diff <branch1>..<branch2> 

# �Ƚ��ݴ����Ͱ汾�����
git diff --staged   

# �Ƚ��ݴ����Ͱ汾�����
git diff --cached   

# �����Ƚ�ͳ����Ϣ 
git diff --stat         
```
7.�汾��ǩ
--------
```
git tag -a 0.1.3 -m ��Release version 0.1.3��

#��⣺git tag ������
#-a 0.1.3������ ��Ϊ0.1.3�ı�ǩ
#-m ������ŵ��Ǳ�ǩ��ע��
#���ǩ�Ĳ�������������commit�޸ĵ����زֿ�֮������������

git add .
git commit -m ��fixed some bugs��
git tag -a 0.1.3 -m ��Release version 0.1.3��

#�����ύ��ǩ��Զ�̷�������
    git push origin master
    git push origin --tags
    
#�Ctags������ʾ�ύ����tag���������ˣ���ͨ��git push origin master�����������ͱ�ǩ���������ˡ�

#ɾ����ǩ������
git tag -d 0.1.3

#ɾ��Զ�˷������ı�ǩ
git push origin :refs/tags/0.1.3
```
