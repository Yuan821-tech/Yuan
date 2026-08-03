# \# Git 功能实操尝试记录
\#\# 一、核心功能实操过程
\#\#\# 1\. 仓库初始化（git init）
\*\*操作步骤\*\*：
打开 Git Bash，进入 GitTest 目录：cd GitTest
执行初始化命令：git init

\*\*执行结果\*\*：
终端提示：Initialized empty Git repository in D:/GitTest/\.git/，目录下生成隐藏文件夹 \.git，包含 objects、refs、HEAD 等核心文件，仓库初始化完成。

\#\#\# 2\. 文件跟踪与提交（git add / git commit）
\*\*操作步骤\*\*：
在 GitTest 目录新建文件 test\.txt，内容为“第一次 Git 测试”。
将文件添加到暂存区：git add test\.txt
提交暂存区内容到本地仓库：git commit \-m "初始化提交：添加 test\.txt 文件"

\*\*执行结果\*\*：
终端显示提交信息，包含 commit 哈希值、提交人、时间及提交说明，test\.txt 成功被 Git 跟踪并保存到本地仓库。

\#\#\# 3\. 状态查看与差异对比（git status / git diff）
\*\*操作步骤\*\*：
修改 test\.txt 内容，新增“新增一行测试内容”。
查看工作区状态：git status
查看工作区与暂存区的差异：git diff
将修改添加到暂存区后，查看暂存区与仓库的差异：git add test\.txt，再执行 git diff \-\-staged

\*\*执行结果\*\*：
git status 显示 test\.txt 已修改但未提交；git diff 清晰展示修改的内容；git diff \-\-staged 显示暂存区与本地仓库的差异，确认修改无误。

\#\#\# 4\. 分支操作（git branch / git switch / git merge）
\*\*操作步骤\*\*：
查看当前分支：git branch（默认分支为 main）
新建分支 dev：git branch dev
切换到 dev 分支：git switch dev
在 dev 分支修改 test\.txt 内容，提交修改：git add test\.txt，git commit \-m "dev 分支：修改 test\.txt"
切换回 main 分支：git switch main
合并 dev 分支到 main：git merge dev

\*\*执行结果\*\*：
成功创建并切换分支，dev 分支的修改顺利合并到 main 分支，无冲突（因仅修改同一文件且无分歧），合并后 main 分支包含 dev 分支的修改内容。

\#\#\# 5\. 撤销与回滚操作（git restore / git reset）
\*\*操作步骤\*\*：
修改 test\.txt 内容，未执行 git add，撤销工作区修改：git restore test\.txt，查看文件内容恢复为修改前。
再次修改 test\.txt，执行 git add 添加到暂存区，撤销暂存：git restore \-\-staged test\.txt，文件回到工作区状态。
执行 git reset \-\-soft HEAD\~1（撤销最近一次提交，保留暂存区），查看提交记录，最近一次提交被撤销。

\*\*执行结果\*\*：
撤销操作均成功，文件状态按预期恢复，\-\-soft 模式仅撤销提交，不改动暂存区和工作区，符合预期需求。

\#\#\# 6\. 远程仓库操作（git remote / git push / git pull）
\*\*操作步骤\*\*：
在 GitHub 新建远程仓库 GitTestRepo，复制仓库地址。
关联本地仓库与远程仓库：git remote add origin 远程仓库地址
推送本地 main 分支到远程：git push \-u origin main
在远程仓库修改 test\.txt 内容，拉取远程更新到本地：git pull origin main

\*\*执行结果\*\*：
本地仓库成功关联远程，推送操作顺利完成，远程仓库更新后，本地通过 git pull 成功获取远程修改内容，实现本地与远程的同步。

\#\#\# 7\. 储藏操作（git stash）
\*\*操作步骤\*\*：
修改 test\.txt 内容，未提交，执行储藏：git stash save "临时储藏未提交修改"
查看储藏列表：git stash list
恢复储藏内容：git stash pop

\*\*执行结果\*\*：
未提交的修改被临时储藏，工作区恢复干净状态；通过 git stash list 可查看储藏记录，git stash pop 成功恢复储藏内容并删除该储藏记录。

\#\# 二、实操总结
1\. Git 核心操作围绕“工作区\-暂存区\-本地仓库\-远程仓库”的文件流转展开，每个命令对应明确的流转方向，需熟练掌握各命令的作用范围。
2\. 分支操作可高效实现并行开发，合并时需注意冲突问题（本次实操无冲突，后续可针对性测试冲突场景）。
3\. 撤销与回滚操作需谨慎使用，尤其是 git reset \-\-hard，会直接删除工作区和暂存区的修改，操作前需确认内容无需保留。
4\. 远程操作需确保本地与远程仓库关联正确，推送前需拉取远程更新，避免出现推送失败的情况。

> （注：部分内容可能由 AI 生成）
