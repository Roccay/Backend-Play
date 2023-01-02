# 文档加密(Encryption and Decryption)

本地文档/存档的加密，防止玩家自行修改存档文件。

## 利用AES的加密/解密方法 作者：Dubit
  
使用方法概括  
```
  加密：  
    原文 + 密码 --> 加密后内容 + IV  
  解密：  
    加密后内容 + 密码 + IV --> 原文  
```  
 [源代码链接（Github）](https://github.com/dubit/unity-crypto)
