---
title: No module named 'django.core.urlresolvers'
date: 2019-07-13 17:04:24
tags: [python, django]
---
使用xadmin的过程中出现下面这个错误。
```
No module named 'django.core.urlresolvers'
```
查看报错的文件其中导入部分如下：
```
import json
import django
from django.db import models
from django.utils import timezone
from django.conf import settings
from django.contrib.contenttypes.models import ContentType
from django.utils.translation import ugettext_lazy as _, ugettext
from django.core.urlresolvers import NoReverseMatch, reverse
from django.core.serializers.json import DjangoJSONEncoder
from django.db.models.base import ModelBase
from django.utils.encoding import python_2_unicode_compatible, smart_text

from django.db.models.signals import post_migrate
from django.contrib.auth.models import Permission

import datetime
import decimal
from xadmin.util import quote
```
修改含有 django.core.urlresolvers 为 django.urls

出现这个问题是因为我的Django版本比较高.需要修改太麻烦所以直接弃用xadmin.