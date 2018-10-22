1. 还原本地修改，已添加到暂存区的和新添加的文件不受影响

```
git checkout -- <filename>
```

2. 丢弃本地所有改动和提交，从服务器获取最新的历史版本

```
git fetch origin

git reset --hard origin/master
```

![](images/basic-usage.svg)