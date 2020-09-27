# Git和GitHub使用

## 安装
+ Git官方网站: https://git-scm.com/

+ Git完整命令手册地址: http://git-scm.com/docs 


## 查看
+ git version

## config设置
+ 设置用户名
    + git config --global user.name "username"
+ 设置邮箱
    + git config --global user.email username@example.com
+ 设置代理提速(解决clone速度较慢的问题)
    + 设置代理(端口号需要自己设置)
        + git config --global https.proxy http://127.0.0.1:1080

        + git config --global https.proxy https://127.0.0.1:1080
    + 取消代理
        + git config --global --unset http.proxy

        + git config --global --unset https.proxy

## 建立仓库
+ 建立本地仓库（直接使用命令创建或者进入文件夹后使用git init）
    + git init [project-name]
+ 克隆项目
    + git clone [url]


## 修改管理
+ 查看修改
    + git status
+ 比对还未暂存的(未add)
    + git diff
+ 将修改提交到暂存区
    + git add [file]
+ 比对暂存区与修改前区别
    + git diff --staged
+ 从暂存区删去文件修改
    + git reset [file]
+ commit提交
    + git commit -m "[descriptive message]"


## 修改同步
+ 获取远程代码
    + git fetch [bookmark]
+ 将branch合入到当前分支
    + git merge [bookmark]/[branch]
+ 推送本地commit到远程
    + git push [alias] [branch]
+ 删除git pull相当于git fetch和git merge组合
    + git pull

## 回滚commit
+ 回滚到对应commit但修改不消失
    + git reset [commit]
+ 回滚到对应commit所有修改消失
    + git reset --hard [commit]


## 查看历史提交修改
+ 当前分支的提交记录
    + git log
+ 某个文件的修改提交记录
    + git log --follow [file]
+ 查看两个分支的代码区别
    + git diff [first-branch]...[second-branch]
+ 查看某个commit号的修改
    + git show [commit]


## branch分支管理
+ 查看分支
    + git branch
+ 创建分支
    + git branch [branch-name]
+ 切换到对应分支
    + git checkout [branch-name]
+ 删除分支
    + git branch -d [branch-name]
+ 合并分支修改(将branch-name中的修改合并到当前分支)
    + git merge [branch-name]

## tag标签管理
+ 查看标签
    + git tag
+ 创建标签(默认创建当前branch的最近commit)
    + git tag [tag-name]
+ 创建历史commit的标签(给指定的commit打标签)
    + git tag [tag-name] [commit-number]
+ 删除标签
    + git tag -d [tag-name]


## Patch管理


## Git与GitHub

+ echo "# repository name" >> README.md

+ git init

+ git add README.md

+ git commit -m "first commit"

+ git remote add origin [github repository url]

+ git push -u origin master
