# Git

**配置**

当前配置

```
git config --list
```

第一次使用git，配置用户信息

```
git config --global user.name "your name"
git config --global user.email "youremail@github.com"
```

**工作区上的操作命令**

新建仓库

```
#新建仓库
git init
#相关联
git remote add [remote-name] [url] #git remote add example git://github.com/example/example.git
git remote rm [remote-name]

#新的项目名或者省略
git clone git://github.com/wasd/example.git mygit
```

提交

```
提交工作区所有文件到暂存区：
git add .
提交工作区中指定文件到暂存区：
git add <file1> <file2> ...;
提交工作区中某个文件夹中所有文件到暂存区：
git add [dir];
```

撤销

```
删除工作区文件，并且也从暂存区删除对应文件的记录：git rm <file1> <file2>;
从暂存区中删除文件，但是工作区依然还有该文件:git rm --cached <file>;
取消暂存区已经暂存的文件：git reset HEAD <file>...;
```

**暂存区的操作**

提交文件到版本库

```
将暂存区中的文件提交到本地仓库中，即打上新版本：git commit -m "commit_info";
将所有已经使用git管理过的文件暂存后一并提交，跳过add到暂存区的过程：git commit -a -m "commit_info";
提交文件时，发现漏掉几个文件，或者注释写错了，可以撤销上一次提交：git commit --amend
```

查看信息

```
git diff --cached
```



**完整流程**

```
git init
git remote add origin https://github.com/wzkong/PythonLearnNote.git
git pull --rebase origin master
git add .
git commit -m 'update'
git push -u origin master
```

