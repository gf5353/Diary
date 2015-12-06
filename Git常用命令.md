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
 # 将工作文件修改提交到本地暂存区
git add <file>       

#将所有修改过的工作文件提交暂存区    
git add .  

#查看文件状态  
git status 
# 从版本库中删除文件 
git rm <file>        

# 从版本库中删除文件，但不删除文件  
git rm <file> --cached

#撤销提交注意最后是有点的
git rm -r --cached . 

#提交你的修改  
git commit –m "你的注释"  

#推送你的更新到远程服务器,语法为 git push [远程名] [本地分支]:[远程分支]  
git push origin master   
```
4. 代码回滚
--------
```
#图形管理界面 主要看Child
gitk 
# 从暂存区恢复到工作文件 
git reset <file>   
# 从暂存区恢复到工作文件  
git reset -- .      
# 恢复最近一次提交过的状态，即放弃上次提交后的所有本次修改  
git reset --hard   
```

5. 查看提交记录
--------
```
git log  
# 查看该文件每次提交记录  
git log <file>     
# 查看每次详细修改内容的diff
git log -p <file>     
# 查看最近两次详细修改内容的diff  
git log -p -2       
#查看提交统计信息  
git log --stat      
```
6. 查看文件diff
--------
```
# 比较当前文件和暂存区文件差异
git diff <file>     
git diff

# 比较两次提交之间的差异
git diff <$id1> <$id2>   

# 在两个分支之间比较
git diff <branch1>..<branch2> 

# 比较暂存区和版本库差异
git diff --staged   

# 比较暂存区和版本库差异
git diff --cached   

# 仅仅比较统计信息 
git diff --stat         
```
7.版本标签
--------
```
git tag -a 0.1.3 -m “Release version 0.1.3″

#详解：git tag 是命令
#-a 0.1.3是增加 名为0.1.3的标签
#-m 后面跟着的是标签的注释
#打标签的操作发生在我们commit修改到本地仓库之后。完整的例子

git add .
git commit -m “fixed some bugs”
git tag -a 0.1.3 -m “Release version 0.1.3″

#分享提交标签到远程服务器上
    git push origin master
    git push origin --tags
    
#–tags参数表示提交所有tag至服务器端，普通的git push origin master操作不会推送标签到服务器端。

#删除标签的命令
git tag -d 0.1.3

#删除远端服务器的标签
git push origin :refs/tags/0.1.3
```
