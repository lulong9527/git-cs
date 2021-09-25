# Git工具对项目版本切换管理

# 1、Git常用命令

* 1.1. 前提是对此修改和提交了文件

* 1.2. 提交日志的查看 

  * 查看当前提交日志，查看提交次数
    * git log
    * git log -10 查看最近10条提交的记录
  * 如果提交历史记录比较多，加入数字控制显示的版本记录数；并且使用 --pretty=oneline 简化输出
    * **git log --pretty=oneline**      ->以一行的形式进行展示，提交的所有内容

* 1.3.  git diff HEAD -- file，比较的是工作区中的文件与版本库中文件的差异。HEAD指向的是版本库中的当前版本，而file指的是当前工作区中的文件。

  * git diff HEAD -- 文件名称（带尾缀）

* 1.4.  git diff HEAD -- /README.md 终端打印值，各自值得是什么

  * diff --git a/README.md b/README.md

    进行比较的是，a版本的README.md（即变动前）和b版本的README.md（即变动后）。 

    index 5e6a0dc..29f2cd4 100644

    表示两个版本的git哈希值，（index区域的5e6a0dc对象，与工作目录区域的29f2cd4对象进行比较），最后的六位数字是对象的模式（100代表普通文件，644代表权限）。

    --- a/README.md     "---"表示变动前的版本

    +++ b/README.md    "+++"表示变动后的版本（红色）

    \ No newline at end of file 最后一行没有换行

    @@ -1,3 +1,4 @@

    代表的意思是源文件的1-3行与目标文件的1-4行有差异,下面才是具体的差异信息;

    -红色部分表示减少的部分

    +绿色部分表示增加的部分

+ 1.5 个人理解与解释

  - git diff ： 对比工作区(未 git add)和暂存区(git add 之后)

    git diff --cached: 对比暂存区(git add 之后)和版本库(git commit 之后)

    git diff HEAD:  对比版本库(未提交git commit)和版本库(git commit 提交之后)

# 2、GIt中提交的形目版本的切换

- 2.1. 版本的回退与切换，git reset 命令用于当前HEAD 复位到指定状态，一般用于撤销之前的一些操作（如：git add ,git commit等）
  - 2.1.2.回到最新的版本
    - git reflog    -> 用来记录用户操作的每一次命令
    - 在使用 git reset --hard  xxx 进行选择之前提交的版本
  - 2.1.2 回退到上一个版本
    - git reset --hard HEAD^ 
      - HEAD^ ：将指针指向上一个版本，如果上上一个 HEAD^^ ,上上上一个HEAD^^^；这样记比较麻烦，如果想后退版本较多，简写为HEAD~100, 往后退100个版本（后退多少版本，波浪号后加多少数字）
  - 2.1.3 退回到指定版本
    - git reset --hard commitid    -> commitid 指的是每次提交的id,
      - 可先使用 git log --pretty=oneline 进行查看所用提交，
      - 在使用 git reset --hard  xxx 进行选择提交的版本