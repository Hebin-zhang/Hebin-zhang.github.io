---
layout:     post
title:      Git操作与GitHub
subtitle:   基本的Git操作，如何使用Github。
date:       2021-12-11
author:     鹤彬
header-img: img/github.jpg
catalog: true
tags:

    - Linux
    - Git
    - Github
---
##  Git操作与GitHub

### ssh密钥

ssh-keygen 命令,生成公私钥,公私钥存放在主目录下的隐藏目录 .ssh 中的两个文件中。
```
cat ~/.ssh/id_rsa.pub
# 提取公钥
```
在github上添加SSH Key
### 克隆仓库至本地
git clone + [仓库地址]
在仓库首页clone ro download按钮下选择SHH地址

### 从本地仓库修改代码提交并推送到远程仓库

Git 本地仓库有三大区域:工作区、暂存区、版本区。
在仓库主目录,执行 git status 可查看整个仓库的状态。

#### 把新增文件添加到暂存区
使用git add [文件名] 命令把新增文件添加到暂存区,以备提交。
git add . ,全部添加到暂存区。
git reset -- [文件名] 或者 git rm --cached [文件名] 命令即可撤销暂存区的修改。
git reset -- 把暂存区的全部修改撤销。

git diff,它可以用来查看工作区被跟踪的文件的修改详情。
在工作区修改详情页,可按 Q 退出此页面

#### commit新增文件

git commit 命令把暂存区的修改提交到版本区,生成一个新的版本。

#### 将文件推送至远程仓库
git push 推送到GitHub
-f force强制推送

#### 查看版本
git status 查看仓库状态
git log,查看版本区的提交历史记录

版本号:十六进制序列号

|命令|说明|
|:-----:|:-----:|
|git log [分支名] |查看某分支的提交历史,不写分支名查看当前所在分支|
|git log --oneline| 一行显示提交历史|
|git log -n |其中 n 是数字,查看最近 n 个提交|
|git log --author [贡献者名字] |查看指定贡献者的提交记录|
|git log --graph |图示法显示提交历史|
|git log --reverse |时间正序排列 |

### 拉取远程仓库文件
git pull,拉取远程仓库文件

git remote add [主机名] [主仓库的地址],同步主仓库

### 回退版本


git reset --soft HEAD^ 撤销最近的一次提交,将修改还原到暂存区。

|参数|说明|
|:---:|:----:|
|--soft| 软退回|
|--hard|硬退回|
|HEAD^|撤销1次提交|
|HEAD^^ |撤销2次提交|
|HEAD~n|撤销n次|

#### 创建分支

git checkout -b [分支名] 创建分支并切换到新分支
git checkout [分支名] 切换分支

#### 查看分支

git reflog,记录本地仓库所有分支的每一次版本变化。
git branch -avv,查看全部分支信息


#### 将本地分支推送到远程仓库

git push [主机名] [本地分支名]:[远程分支名] ,将本地分支推送到远程仓库的分支中
若本地分支名字与远程分支名相同,可以省略 :[远程分支名]
git branch -u [主机名/远程分支名] [本地分支名] 将本地分支与远程分支关联
git push -u origin dev 在推送时就自动跟踪远程分支


#### 将远程仓库的分支信息拉取到本地仓库

git fetch,将远程仓库的分支信息拉取到本地仓库
仅是更新本地远程分支信息,执行 git branch -avv 命令时,可查看到的 remotes 开头行的分支信息。

#### 删除分支
本地:git branch -d [本地分支名]	
远程:git push [主机名] --delete [远程分支名]	