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
#����ļ�
git add android����.md

#��ӵ�ǰ�޸ĵ��ļ����ݴ���  
git add .  

#�鿴�ļ�״̬  
git status 

#�����ύע��������е��
git rm -r --cached . 

#�ύ����޸�  
git commit �Cm "���ע��"  

#������ĸ��µ�Զ�̷�����,�﷨Ϊ git push [Զ����] [���ط�֧]:[Զ�̷�֧]  
git push origin master   
```
