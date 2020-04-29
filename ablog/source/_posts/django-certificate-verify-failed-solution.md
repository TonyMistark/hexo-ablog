---
layout: post
title:  "django-certificate-verify-failed-solution"
date:   2020-04-29 15:55:40 +0800
categories: django
---

### django:certificate verify failed solution

##### 错误提示
```
<urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: unable to get local issuer certificate
```

##### 解决方法

Mac: 
命令行执行：
根据自己的python版本cd到对应的目录
```
cd /Applications/Python\ 3.7/
./Install\ Certificates.command
```

