# gitLearnRecords
>学习工作常用git命令记录

## git tag

发布一个版本时，我们通常在版本库中打一个标签（tag），这样，就唯一确定了打标签时刻的版本。将来无论什么时候，取某个标签的版本，就是把那个打标签的时刻的历史版本取出来。

1. 创建版本标签

    在命令行切换到需要打标签的分支上，输入git命令`git tag -a <tagname> -m 'someMsg'`，如`git tag -a v1.0.0 -m '新增xxx，优化xxx'`，`tagname`一般用**发布版本号**表示，默认标签是打在最新提交的commit上，也可指定`commit id`，如`git tag v1.0.0 6ac4327`.

2. 推送标签到远程分支

    在命令行输入`git push origin <tagname>`，如`git push origin v1.0.0`，或者推送全部尚未推送到远程的本地标签：`git push origin --tags`。

3. 删除远程标签

    在命令行输入`git tag -d <tagname>`,如`git tag -d v1.0.0`。此操作需要`master`权限。
    
## git stash 用于保存和恢复工作进度
```
git stash
```
保存当前的工作进度。会分别对暂存区和工作区的状态进行保存
```
git stash save "message..."
```
这条命令实际上是第一条 git stash 命令的完整版
```
git stash list
```
显示进度列表。此命令显然暗示了git stash 可以多次保存工作进度，并用在恢复时候进行选择
```
git stash pop [--index] [<stash>]
```
如果不使用任何参数，会恢复最新保存的工作进度，并将恢复的工作进度从存储的工作进度列表中清除。

如果提供参数（来自 git stash list 显示的列表），则从该 <stash> 中恢复。恢复完毕也将从进度列表中删除 <stash>。

选项--index 除了恢复工作区的文件外，还尝试恢复暂存区。
```
git stash apply [--index] [<stash>]
```
除了不删除恢复的进度之外，其余和 git stash pop 命令一样
```
git stash clear
```
删除所有存储的进度
