# Git sync fork

1. 主要使用 git remote -v 查看远程状态。

  ```
  git remote -v
  ```

  结果

  ```
  origin  https://github.com/xinyer/bitcoinj.git (fetch)
  origin  https://github.com/xinyer/bitcoinj.git (push)
  ```

2. 添加一个将被同步给 fork 远程的上游仓库

  ```
  git remote add upstream https://github.com/bitcoinj/bitcoinj.git
  ```

  使用 git remote -v 查看结果

  ```
  origin https://github.com/xinyer/bitcoinj.git (fetch)
  origin https://github.com/xinyer/bitcoinj.git (push)
  upstream https://github.com/bitcoinj/bitcoinj.git (fetch)
  upstream https://github.com/bitcoinj/bitcoinj.git (push)
  ```

3. sync fork

  ```
  git fetch upstream
  ```

4. checkout local master branch

  ```
  git checkout master
  ```

5. merge upstream/master branch

  ```
  git merge upstream master
  ```

6. push origin master

  ```
  git push origin master
  ```
