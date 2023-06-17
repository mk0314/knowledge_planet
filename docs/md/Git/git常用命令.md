<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-08 19:19:00
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-14 15:45:49
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

17. git rebase 命令时，通常需要指定目标分支和待重构分支，并在执行过程中解决可能出现的冲突。具体步骤如下：

切换到待重构分支：git checkout <await-rebase-branch>

执行 rebase 操作：git rebase <target-branch>

解决冲突（如果有）：Git 会打开冲 [Something went wrong, please try again later.]

> ### 更新.gitignore

可以按照以下步骤进行更新：

打开您项目中的 .gitignore 文件。

添加或删除需要忽略的文件和文件夹，例如 \*.log 或 myfolder/。

保存并关闭 .gitignore 文件。

执行以下命令将新的 .gitignore 文件添加到 Git 仓库中：git add .gitignore

提交 .gitignore 文件的修改：git commit -m "Update .gitignore file."

注意，修改 .gitignore 文件将只影响未被 Git 跟踪的文件。如果您之前已经将某个文件添加到 Git 仓库中并推送到远程仓库，那么即使将这个文件添加到 .gitignore 文件中，Git 也不会自动从历史记录中删除它。此时，您需要手动将其删除，再将更改推送到远程仓库。

总之，.gitignore 文件是一个非常有用的工具，可以帮助您管理 Git 仓库中的文件，减少代码冲突和混乱。
