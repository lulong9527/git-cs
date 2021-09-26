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

  + 使用Https（步骤）

    + 绑定Https远程地址到本地，执行命令 git remote add origin https://github.com/xxx/xxx.git
    + git push -u origin main(分支)

  + 使用SSH

    使用Https推送比较简单，使用SSH加密的方式是Git建议的一种推送，时间与相应相率都更改，这里介绍SSH推送方式配置

    + 1、使用本地的Git客户端生成SSH公钥与私钥，执行命令 ssh-keygen -t rsa -C "GitHub账户邮箱"
      + 
    + 2、将公钥上传到GitHub上，本地保留私钥
    + 3、检查测试连接（公私钥是否配置正确）,执行命令 ssh -T git@github.com
    + 4、使用SSH执行推送操作

