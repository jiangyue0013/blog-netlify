---
title: 修改.gitignore使之生效
date: 2019-07-09 09:50:15
tags: git
---
清除tracked缓存

    git rm -r --cached .

重新添加文件

    git add .

最后需要提交

    git commit -m ".gitignore is now working"


参考:

http://stackoverflow.com/a/26137730/4349466

作者：eoeoops

链接：https://www.jianshu.com/p/17dc13c7a0a3

来源：简书

简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。