---
title: Django中Middleware中的函数
date: 2019-07-09 18:16:38
tags: django
---
一个middleware的例子
````
import time

from django.urls import reverse
from django.utils.deprecation import MiddlewareMixin


class TimeItMiddleware(MiddlewareMixin):
    def process_request(self, request):
        return

    def process_view(self, request, func, *args, **kwargs):
        if request.path != reverse('index'):
            return None

        start = time.time()
        response = func(request)
        costed = time.time() - start
        print('process view: {:.2f}s'.format(costed))
        return response

    def process_excepttion(self, request, exception):
        pass

    def process_template_response(self, request, response):
        return response

    def process_response(self, request, response):
        return response
````

middleware中的函数有：
* process_request
* process_view
* process_tmplate_response
* process_response
* process_exception

下面分别进行介绍:
#### process_request:
这是请求来到 middleware 中时讲入的第一个方法。一般情优下,我们以在这里做一些校验,比如
户登录或者 HTTP 中是否有认证头之类的验证.这个方法可以有两种返回值 HttpResnonse 或者None，如果返回 HttpResponse，那么接下米的处理方法只会执行 process_response，其他方法将不会被执行。这里需要注意的是，如果你的 middleware 是 settings 配置的 MIDDLEWARE 的第一个，那么剩下的 middleware 也不会被执行；如果返回 None，那么 Diango会继续执行其他方法。
#### process_view:
这个方法是在 process_request 方法之后执行的,参数如上面代码所示，其中 func 就是我们将要执行的 view 方法。因此，如果要统计一个view的执行时间，可以在这里做。它的返回值跟 process_request 一样，是HttpResponse 或者 None，其逻辑也一样。如果返回 None，那么 Django 会帮你执行 view 函数,从而得到最终的 response。 
#### Process_template_response:
执行完上面的方法，并且 Django 帮我们执行完 view，拿到最终的 response 后，如果使用了模板的 response (这是指通过 return render(request,'index.html',context={})方式返回的 response),就会来到这个方法中。 在这个方法中，我们可以对 response 做一下操作,比如 Content-Type 设置,或者其他 header 的修改/增加。
#### process_response:
当所有流程都处理完毕后，就来到了这个方法。这个方法的逻辑跟 process_template_response是完全一样的,只是后者是针对带有模板的response的处理。
#### process_exception:
上面的处理方法是按顺序介绍的，而这个方法不太一样。只有在发生异常时,才会进入这个方法。哪个阶段发生的异常呢?
可以简单理解为在将要调用的 View 中出现异常(就是在process_view 的 func 函数中)或者返回的模板 response 在渲染时发生的异常。但是需要注意的是，如果你在process_view 中手动调用了 func，就像我们上面做的那样,就不会触发 process_exception 了。这个方法接收到异常之
后，可以选择处理异常，然后返回一个含有异常信息的 HttpResponse，或者直接返回 None 不处理，这种情况下 Django会使用自己的异常模板。

以上节选自《Django企业开发实战》 胡阳著。