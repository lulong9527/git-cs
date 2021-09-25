# 1、服务器的SSL证书没有经过第三方机构的签署

+ 报错形式
  + fatal: unable to access 'https://github.com/lulong9527/Git-.git/': OpenSSL SSL_read: Connection was reset, errno 10054

* 解决方法
  * 确定登录GitHub后，在多次尝试操作推送等操作
  * git config --global http.sslVerify “false”

+ 参考文档: <https://www.cnblogs.com/jfen625/p/12995408.html>

