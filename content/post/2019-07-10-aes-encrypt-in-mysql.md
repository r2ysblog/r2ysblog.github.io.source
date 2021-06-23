---
layout: post
title:  "aes encrypt in mysql"
date:   2019-07-10 10:53:00 +0800
categories: encrypt
---

## 在mysql中对字符串aes加密和解密


#### 直接上函数

```mysql
# 加密
SELECT HEX(AES_ENCRYPT('123456','root')) 
# 解密
SELECT AES_DECRYPT(unhex('537AB41AAABDEC3BAB09BE15392B916A'), 'root')
```

