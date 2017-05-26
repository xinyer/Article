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
