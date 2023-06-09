<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-08 19:19:00
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-09 17:24:01
 * @FilePath: \knowledge_planet\docs\md\idea-plugin\git\git常用命令.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

> ### 设置以及查看本地 git 账号邮箱

查看配置信息

```git
git config --list
```

设置本地账号信息

```git
git config --global user.name "xxx"
git config --global user.email "xxx"

```

> ### Git 常用命令：

Git 是一个分布式版本控制系统，被广泛应用于软件开发中。

1. git init：初始化一个 Git 仓库。
2. git clone：从远程 Git 仓库中克隆代码库到本地。
3. git add：将修改的文件添加到 Git 仓库中。
4. git commit：将更改提交到 Git 仓库中，并记录修改日志。
5. git push：将本地 Git 仓库中的修改推送到远程 Git 仓库中。
6. git pull：将远程 Git 仓库中的最新修改拉取到本地 Git 仓库中。
7. git status：查看当前 Git 仓库的状态。
8. git log：查看 Git 仓库的提交记录。
9. git branch：创建、查看或删除 Git 分支。
10. git merge：将两个分支合并为一个分支。
11. git tag：创建、查看或删除 Git 标签。
12. git stash：将当前修改暂存起来，以便在另一个分支上继续工作。
13. git reset：回退到之前的提交版本或取消之前的修改。
14. git revert：撤销之前的提交操作。
15. git rm：删除 Git 仓库中的文件。
16. git mv：移动或重命名 Git 仓库中的文件。

还有很多其他 Git 命令可以使用，请根据需要学习和使用。同时，建议在操作前先认真了解命令的含义，以避免误操作导致数据丢失等问题。
