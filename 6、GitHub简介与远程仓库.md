# GitHub简介与远程仓库

# 1、GitHub简介

+  gitHub是一个面向[开源](https://link.jianshu.com?t=https%3A%2F%2Fbaike.baidu.com%2Fitem%2F%25E5%25BC%2580%25E6%25BA%2590%2F20720669)及私有[软件](https://link.jianshu.com?t=https%3A%2F%2Fbaike.baidu.com%2Fitem%2F%25E8%25BD%25AF%25E4%25BB%25B6%2F12053)项目的托管平台，因为只支持git 作为唯一的版本库格式进行托管，故名gitHub。gitHub于2008年4月10日正式上线，除了git代码仓库托管及基本的 Web管理界面以外，还提供了订阅、讨论组、文本渲染、在线文件编辑器、协作图谱（报表）、代码片段分享（Gist）等功能。目前，其注册用户已经超过350万，托管版本数量也是非常之>. 多，其中不乏知名开源项目 [Ruby](https://link.jianshu.com?t=https%3A%2F%2Fbaike.baidu.com%2Fitem%2FRuby%2F11419) on Rails、jQuery、[python](https://link.jianshu.com?t=https%3A%2F%2Fbaike.baidu.com%2Fitem%2Fpython%2F407313) 等。

# 2、远程仓库

## 2.1、从远程仓库下载代码

+ 对https://github.com/xxx/xxx.git仓库进行下载(下载远程仓库到本地)
  + git clone https://github.com/xxx/xxx.git

## 2.2 将本地仓库推送远程仓库--步骤

+ 2.2.1创建远程仓库（公共的-私有的都是可以的）
  + <img src="/Users/apple/Library/Application Support/typora-user-images/image-20210926104531937.png" alt="image-20210926104531937" style="zoom:40%;" />

+  2.2.2推送有两种方式

  + 1、使用Https（步骤）

    + 绑定Https远程地址到本地，执行命令 git remote add origin https://github.com/xxx/xxx.git
    + git push -u origin main(分支)

  + 2、使用SSH

    使用Https推送比较简单，使用SSH加密的方式是Git建议的一种推送，时间与相应相率都更改，这里介绍SSH推送方式配置

    + 1、使用本地的Git客户端生成SSH公钥与私钥，执行命令 ssh-keygen -t rsa -C "GitHub账户邮箱"

      + 注意事项：执行ssh-keygen -t rsa -C "384069xxx@qq.com" enter后每一步都是enter，最后生成如下

        + 身份信息(私钥)保存在（/Users/apple/.ssh/id_rsa）中，/Users/apple/.ssh/id_rsa->地址根据生成值改变
          + Your identification has been saved in /Users/apple/.ssh/id_rsa.   

        + 您的公钥已保存在（/Users/apple/.ssh/id_rsa.pub）中
          + Your public key has been saved in /Users/apple/.ssh/id_rsa.pub.

        + 生成的关键指纹为
          + SHA256:5SAQsJNLAuRvoSNL+4ZdlLtU4W74SeA+vWtbUEZQWLM 3840xxx@qq.com

    + 2、找到公钥（/Users/apple/.ssh/id_rsa.pub），将公钥上传到GitHub上，本地保留私钥

      + 公钥填写路径 个人信息login->setings->SSH and GPG keys-SSH keys->New SSH key(填写完两个值)->点击Add SSH key
        + New SSH key中填写两个值
          + Title 随意填写，尽量填写需要添加仓库的名称（方便辨识）
          + Key 填写/Users/apple/.ssh/id_rsa.pub中的共有key值

    + 3、检查测试连接（公私钥是否配置正确）,执行命令 ssh -T git@github.com

      + 执行完命令可以看到校验结果是否成功
      + 成功-欢迎进入
        + 返回值 例如：Hi lulong9527! You've successfully authenticated, but GitHub does not provide shell access.
      + 失败-拒绝访问
        + git@github.com: Permission denied (publickey).

    + 4、使用SSH执行推送操作

      + 4.1 将远程仓库的地址绑定到本地与删除绑定
        + git remote add origin git@github.com:lulong9527/xxx.git
          + 其中 origin 叫做远程仓库的别名
          + git@github.com:lulong9527/xxx.git   指的是远程仓库地址
        +  git remote rm origin   删除origin远程仓库连接，origin根据上面设置的仓库别名来定
      + 4.2 创建分支（若创建分支推送的分支也写成此处更改的分支）
        + git branch -M main(本地仓库主干分支名)   创建一个叫做main的主干分支，此时会将本地的master(主干分支)改成main(主干分支)
      + 4.3 将本地文件传到远程仓库
        + git push -u origin main(远程仓库主干分支)   为了跟本地的分支名一致，如果上面不进行创建分支，此处写的是初始值(master)

# 3、本地仓库文件推送到GItHub总结

+ 1、Github 账户注册 

+ 2、GitHub 创建仓库（不允许中文）
+ 3、本地生成ssh的公钥和私钥
  +  ssh-keygen -t rsa -C "GitHub账户邮箱"

+ 4、上传公钥到github
+ 5、校验ssh环境
  + ssh -T git@github.com

+ 6、执行远程推送

  + 1、绑定远程仓库地址
    + git remote add origin git@github.com:lulong9527/xxx.git
  + 2、本地创建主干分支
    + git branch -M main

  + 3、本地文件推送到远程仓库
    + git push -u origin main

+ 7、刷新远程仓库，查看是否上传成功
