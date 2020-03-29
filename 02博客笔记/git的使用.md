---
title: git的使用
date: 2020-03-21 17:17:59
categories:
- 工具
---
### git：分布式版本控制系统  
安装：
```
sudo apt-get install git
```
#### 创建版本库  
1. 先创建一个文件夹
2. git init 初始化一个git仓库
3. Git add <file> 添加文件
4. Git commit -m '说明'  提交到仓库
5. Git status 检查仓库变动的状态
6. git diff readme.txt 检查某个文件具体修改了哪些内容
7. Git log 查看提交日志
8. Git reset --hard HEAD^ 退回上一个版本，HEAD表示当前版本，^表示上一个版本，^^表示上上个版本
9. 跳回旧版本后想再跳回新的版本，需要在记录中找到版本的id号，Git reflog
10. git checkout -- readme.txt 把readme.txt文件在工作区的修改全部撤销,变得跟仓库的一样
11. git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。
12. git rm test.txt 删除文件

#### 链接到github
1. 先开启ssh服务，再将公钥添加到github中。
2. 建立一个新的仓库，按照提示将本地仓库同步上去
```
git remote add origin https://github.com/100824/git_test.git
git push -u origin master
# 以后可以用下面命令简化同步
git push origin master
# 从远程库克隆
git clone +远程库地址（github上面有）
```
到这里就同步成功了

#### 分支管理
```
# 创建分支
git branch dev
# 切换分支
git checkout dev   或     git switch dev
# 查看当前分支
git branch
# 在分支修改后记得add 与commit
# 将分支合并到当前分支上（master）
git merge dev
# 合并后就可以删除分支了
git branch -d dev
```
#### 解决冲突
当两个分支都有新的提交的时候，就无法使用上面的快速合并
```
# 尝试快速合并，失败,提示必须手动解决冲突后在提交
git merge newbranch
# 可以使用git status查看冲突的文件
# 直接打开冲突的文件，里面会有提示分支不同的信息，修改后再提交add 和commit
# 查看分支的合并情况
git log --graph --pretty=oneline --abbrev-commit
# 或者直接git log
# 尽量不要使用fast-forward合并，使用--no-ff可以见到合并前的分支情况
git merge --no-ff -m 'no fast-forward fixed' newbranch
```
#### bug分支
当你在工作区的任务进行到一半，出现bug时，可以通过创建bug分支来解决bug
使用stash可以将当前的工作现场隐藏起来,再创建一个bug的分支
```
git stash
git status
git branch debug-101
git checkout debug-101
# 修改提交后，再stash查看工作现场
git stash list
# 再用apply恢复，或者用pop恢复后同时把stash的内容删了
git stash apply
git stash pop
# 多次stash的时候可以使用list查看，再指定要恢复的stash
git stash apply stash@{0}
# 复制特定的提交到当前分支，不是整个分支  加的是特定的提交的编号
git cherry-pick 4c8043 
# 没有合并过的分支删除时需要加-D
git branch -D <name>
```
#### 多人协作
```
# 查看远程仓库的名称
git remote
# 推送分支，把该分支本地所有的提交推送到远程库,默认的名称是origin
git push origin master/newbranch
# 抓取分支，clone，只能看到本地的master分支
# 要在其他分支上开发需要创建远程分支到本地
git checkout -b dev origin/dev
# 修改后再push上去
git push origin dev
# 当其他人已经向origin/dev分支推送了他的提交，造成你的推送失败，先用git pull把新的提交从origin/dev抓下来，在本地合并解决冲突在推送
# 需要先设置本地的dev分支与origin/dev分支的链接（提示有），再pull
git branch --set-upstream-to=origin/dev dev
git pull
# 手动解决后再commit，push
```
多人协作的工作模式通常是这样：

1. 首先，可以试图用git push origin <branch-name>推送自己的修改；

2. 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

3. 如果合并有冲突，则解决冲突，并在本地提交；

4. 没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。

这就是多人协作的工作模式，一旦熟悉了，就非常简单。

#### 标签管理
```
# 在当前的分支打标签
git tag v1.0
# 在历史的commit上打标签，先找到他的id
git tag v0.9 f52c633
# 查看标签信息
git show v0.9
# 创建带有说明的标签，用-a指定标签名，-m指定说明文字
git tag -a v0.1 -m "version 0.1 released" 1094adb
# 标签的修改
# 删除
git tag -d v1.0
# 因为创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。
# 如果要推送某个标签到远程，使用命令git push origin <tagname>
git push origin v1.0
# 一次性推送全部尚未推送的标签
git push origin --tags
# 远程删除标签，需要特定格式
git push origin :refs/tags/v0.9
```




