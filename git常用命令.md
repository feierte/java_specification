# git常用命令





## git代码提交流程

- git status	# 查看本地分支代码状态
- git add .         # 添加本地所有修改过的代码到缓存
- git commit -m "更新信息"        # 提交代码
- git push         # push到远程仓库



## git创建空白新分支

- 创建并切换新分支

  git branch <new_branch>

  git checkout <new_branch>

  git rm --cached -r .

  git clean -f -d

- 创建空的commit

  git commit --allow-empty -m "empty commit"

- 推送新分支

  git push origin <new_branch>



## git分支管理

- git branch 	# 查看本地分支
- git branch -a     # 查看远程分支
- git checkout -b 分支名    # 切换分支（如果不存在，则新建分支）
- git checkout 分支名    # 切换分支



### 从master切一个新分支

1.切换到master分支

git  checkout  master

2.获取最新的代码

git pull origin master

3.从当前分支拉copy开发分支：(新建了一个和master一样的分支Dev)

git checkout -b dev

4.把新建的分支push到远端

git push origin dev

5.关联

git branch --set-upstream-to=origin/dev

6.再次拉取验证

git pull origin dev

7.就可以在新的分支上开发了



### 合并分支到master上

假如我们现在在dev分支上，刚开发完项目，执行了下列命令

git add .
git commit -m ‘dev'
git push -u origin dev

然后我们要把dev分支的代码合并到master分支上 该如何？
首先切换到master分支上

git checkout master

如果是多人开发的话 需要把远程master上的代码pull下来

git pull origin master

如果是自己一个开发就没有必要了，为了保险期间还是pull

然后我们把dev分支的代码合并到master上

git merge dev

然后查看状态

git status

On branch master
Your branch is ahead of 'origin/master' by 12 commits.
(use "git push" to publish your local commits)
nothing to commit, working tree clean

上面的意思就是你有12个commit，需要push到远程master上
执行下面命令即可

git push origin master

这样就可以了



## git删除分支

- git checkout 分支名	# 先切换到别的分支
- git branch -d 分支名       # 删除本地要删除的分支
- git branch -D 分支名      # 强制删除分支
- git push origin -delete 分支名        # 删除远程分支



## git多人协作工作模式

1. 首先，可以试图用`git push origin <branch-name>`推送自己的修改；

2. 如果推送失败，则因为远程分支比你的本地更新，需要先用`git pull`试图合并；

3. 如果合并有冲突，则解决冲突，并在本地提交；

4. 没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功！

5. 如果`git pull`提示`no tracking information`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>`

   

## git设置编码格式

- git config --global core.quotepath false  	# 显示 status 编码
- git config --global gui.encoding utf-8      # 图形界面编码
- git config --global i18n.commit.encoding utf-8      # 提交信息编码
- git config --global i18n.logoutputencoding utf-8      # 输出 log 编码

## git仓库迁移



## git删除已经提交的文件夹



1、git pull origin master	# 将远程仓库里面的项目拉下来

2、git rm -r --cached .idea	# 删除.idea文件夹

3、git commit -m "删除.idea"	# 提交

4、git push -u origin master	# 将本次更改更新到github上去





