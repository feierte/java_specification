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



