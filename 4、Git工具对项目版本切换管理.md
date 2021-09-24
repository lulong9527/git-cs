# 1、Git工具对项目版本切换管理

* 1.1. 前提是对此修改和提交了文件

* 1.2. 
  * 查看当前提交日志，查看提交次数
    * git log


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