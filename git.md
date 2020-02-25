
1: 在当前目录实现git管理初始化
  git init

2: 配置当前操作者信息
  git config --global user.name 'wong';
  git config --global user.emal 'xx@xx.com'

3: 添加文件到staging区( . 指的是所有文件包括新增文件和修改过的文件)
   git add .

4： 提交文件
   git commit -m '描述性文字'

5: commited的文件编辑后状态变为unstaged需要再次 add 然后commit

6: 比较未添加到staging的文件与已经commited的文件的内容：
    git diff
7: 比较staging 文件和上次commited的文件内容：
   git diff --cached

8: 比较unstaged 和staging状态的内容对比：
  git diff HEAD

9: 查看提交信息：
    git log --oneline

10: 对历史提交进行修改：（先修改好xxx文件）(--no-edit： 不修改提示信息)
    git add xxx
    git commit --amend --no-edit

11： 从staging状态返回到unstage状态：(xxx.py文件)
    git reset xxx.py

12： 返回到具体的某个版本并删除log里的跨过的版本记录  (返回到对应的comittedID版本)
    git reset --hard commitedID

13： 查看所有的历史包括删除掉的：
    git reflog

14: 让单个文件回到某个comitted版本：(让xx.py文件回到 commitedID 版本时的状态)（然后进行编辑xx.py， 再次add commite）
    git checkout comittedID -- xx.py

15：按图表形式显示log:
   git log --oneline --graph

16: 创建分支xxx
    git branch xxx
17: 查看分支：
    git branch
18: 切换分支：
    git checkout xxx
19:  删除分支xxx:
    git checkout master (先切换到master分支)
    git branch -d xxx (后删除xxx分支)

20： 创建并切换到xxx新分支：
    git checkout -b xxx

21: 跳过add直接commited:(新创建的文件无效)
    git commit -am "xxxx"
    

22： 在master分支上合并xxx分支的版本(--no-ff 可以在历史中看到合并的信息)
    git checkout master
    git merge xxx --no-ff -m "merge info"

23：如果merge分支的时候主分支已经被同事合并过多次， 此时如果你直接merge就会报错冲突（此时需要手动修改冲突）手动修改之后：
    git commit -am  '手动解决冲突'

23_1: 如果master分支上修改了多次；此时自己的feature分支也修改了多次， 但是feature分支是在最初的master分支上创建的， 此时要把feature分支基于最新的master分支继续创建内容，就可以使用rebase
    git checkout feature (确保自己不在master分支)
    git rebase master (基于最新的master分支来更新feature分支的内容)

24：暂存当前分支的修改去做其他事情
    git stash (将当前任务暂存)
    git checkout -b boss (创建boss分支做其他事情，做完commit， 切换master分支合并boss分支的任务)
    git checkout xxx (返回自己的xxx分支)
    git branch -D boss (强行删除boss分支)
    git stash pop (从暂存区拿回来自己之前缓存的任务继续写)

25：链接github
    git remote add origin https://
26: 把本地的master 推送到github的origin管理库里：
    git push -u origin master

