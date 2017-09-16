![](images/git.png)

# Git命令

1. 新建Repository／初始化本地Repository

  ```
  git init
  ```

2. 提交代码到本地仓库

  ```
  git add .
  git commit -m "commit message."
  ```

3. 给本地Repository设置远程地址

  ```
  git remote add origin https://github.com/xinyer/test.git
  ```

4. 修改本地Repository的远程地址

  ```
  git remote set-url origin URL
  ```

5. 本地代码推送到远程Repository

  ```
  git push origin master
  ```

6. 新建本地分支

  ```
  git checkout -b name-of-branch
  ```

7. 本地分支推送到远程

  ```
  git push origin name-of-branch
  ```

8. 删除本地分支

  ```
  git branch -d name-of-branch
  ```

9. 删除远程分支

  ```
  git push origin :name-of-branch
  ```

10. cherry-pick

  ```
  合并一个其他分支的commit到当前分支
  git cherry-pick commit-id
  ```

11. clone

  ```
  git clone repo-url
  ```

12. 配置git信息

  ```
  查看所有配置信息
  git config --list
  ```

  ```
  设置提交代码时的用户信息
  git config [--global] user.name "[name]"
  git config [--global] user.email "[email address]"
  ```

13. 查看分支

  ```
  查看本地分支
  git branch
  ```

  ```
  查看所有远程分支
  git branch -r
  ```

  ```
  查看所有分支
  git branch -a
  ```

14. stash

  ```
  暂存代码
  git stash save "save message"
  ```

  ```
  查看所有暂存信息
  git stash list
  ```

  ```
  移除暂存
  git stash pop stash-id
  ```

  ```
  清空暂存区
  git stash clear
  ```

15. .gitignore

  ```
  修改.gitignore文件之后，使之生效

  git rm -r --cached .
  git add .

  之后可以进行提交：
  git commit -m "fixed untracked files"
  ```

16. 查看远程tag

  ```
  git ls-remote --tags
  ```

17. 新建本地tag

  ```
  含附注的标签
  git tag -a v1.4 -m 'my version 1.4'

  轻量级标签
  git tag v1.4
  ```

18. 删除本地tag

  ```
  git tag -d tag-name
  ```

19. 删除远程tag

  ```
  git push origin :refs/tags/tagName
  ```

20. 查看tag信息

  ```
  git show v1.4
  ```

21. 本地标签推送到远程代码库

  ```
  推送一个
  git push origin v1.5

  推送所有
  git push origin --tags
  ```

22. 删除本地分支

  ```
  git branch -D branch_name
  ```

23. 删除远程分支

  ```
  git push origin :br
  ```
