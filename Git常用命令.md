# Git常用命令

标签（空格分隔）： 未分类

---

首先贴个官网链接方便今后下载http://git-scm.com/download/
安装就不细说了

1. 配置Git Config
--------
应用程序Git Bash 进入命令，一般的git配置文件都在这里面，配置的文件路径一般在C盘用户下的.gitconifg
比如我这边的是C:\Users\Guf\.gitconfig
当然我们可以配置全局的或者针对当前仓库的，我们先来看下配置全局的config

```
#列举所有配置
git config -1 

#配置使用git仓库的人员姓名
git config --global user.name "Your Name Comes Here"

#配置使用git仓库的人员email
git config --global user.email 562401002@qq.com

#配置到缓存 默认15分钟
git config --global credential.helper cache 

#修改缓存时间
git config --global credential.helper 'cache --timeout=3600'  

git config --global color.ui true
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global core.editor "mate -w"    # 设置Editor使用textmate

#用户的git配置文件~/.gitconfig

```
2. 创建版本库
--------


```
#所在目录变成可以管理的仓库
git init

#Clone远程版本库  
git clone https://github.com/gf5353/Diary.git

#添加远程版本库origin，语法为 git remote add [shortname] [url]  
git remote add origin https://github.com/gf5353/Diary.git 
  
#查看远程仓库  
git remote -v  
```

3. 提交到版本库
--------


```
#添加文件
git add android常用.md

#添加当前修改的文件到暂存区  
git add .  

#查看文件状态  
git status 

#撤销提交注意最后是有点的
git rm -r --cached . 

#提交你的修改  
git commit –m "你的注释"  

#推送你的更新到远程服务器,语法为 git push [远程名] [本地分支]:[远程分支]  
git push origin master   
```
