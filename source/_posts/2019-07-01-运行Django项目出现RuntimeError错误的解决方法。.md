---
title: '''运行Django项目出现RuntimeError错误的解决方法。'''
date: 2019-07-02 22:16:45
tags: [python, django]
---
运行Django项目出现：
```
RuntimeError: cryptography is required for sha256_password or caching_sha2_password
```
使用：
```
pip install cryptography
```
安装cryptography即可解决。