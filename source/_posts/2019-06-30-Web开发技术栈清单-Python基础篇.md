---
title: Web开发技术栈清单-Python基础篇'
date: 2019-06-30 22:06:57
tags: [python, django]
---
问题答案由本人整理

----------
#### 1.基础语法是否熟悉？介绍一下
Python和其他语言最大的区别就是使用行和缩进，而不是大括号（{}）或者分号（;）来控制类、函数或者逻辑判断。Python使用换行来表示语句的结束。但同时可以用左斜杠（\）将一行语句分成多行。Python 使用单引号（'）、双引号（")和三引号（'''或"""）来表示字符串。其中单引号和双引号的区别不大，字符串中含有单引号或者双引号时需用转义符号（\）或双引号及单引号包裹即可。三引号则支持字符串换行。

#### 2.有哪些关键字？解释其作用

Python中的关键字可以在Python交互模式中输入下面代码查看：

    import keyword
    keyword.kwlist

 - False 表示布尔类型中的假
   
 - None 
   
 - True
   
 - and 表示逻辑 ’与‘
   
 - as 用于类型转换
   
 - assert 断言，用于判断变量或者条件表达式的值是否为真
   
 - async
   
 - await
   
 - break 用于中止循环，brea后的语句不会执行，跳出分支或者循环
   
 - class 用于创建类
   
 - continue 用于继续下一次循环
   
 - def 用于定义函数或方法
   
 - del 用于list列表操作，删除一个或多个元素
   
 - elif 用于定义if中的其他分支的操作
   
 - else 用于定义if语句中所有条件都不满足时执行的操作
   
 - except except包含捕获异常后的操作代码块，与try,finally结合使用
   
 - finally 用于异常语句，出现异常后，始终要执行finally，包含的代码块，与try，except结合使用
   
 - for 用于for循环语句
   
 - from 导入模块 用 import ... 或from ... import
   
 - fwrom
   
 - global 用于声明全局变量
   
 - if 用于if语句
   
 - import 用于导入模块
   
 - in 用于判断变量是否在序列中
   
 - is 用于判断两个对象是否时同一对象
   
 - lambda 定义匿名变量
   
 - nonlocal
   
 - not 表示逻辑’非‘
   
 - or 表示逻辑’或‘
   
 - pass 空的类、方法和函数的占位符。
   
 - raise 用于异常抛出操作
   
 - return 用于函数的返回值
   
 - try 用与捕捉异常
   
 - while 用于控制循环，允许重复执行一个代码块
   
 - with 用于简化python中的语法 https://zhuanlan.zhihu.com/p/32122124
   
 - yield 用于函数依此返回函数值 https://zhuanlan.zhihu.com/p/32178981

#### 3. 有哪些内置方法？解释其作用

- abs(x) # 返回x的绝对值

- all(x) # x列表或可迭代数据全部为真才为真（非0即为真）

- any(x) # x列表或可迭代数据有一个为真即为真

- ascii(x) # 和repr()一样把x对象转换成ascii字符串对象打印出来

- bin(x) # 把十进制转换为二进制

- bool(x) # 判断x是否为真（非空即为真）

- bytes() # 把字符转换成字节，使用时必须加上编码如 a=bytes('abcde', encoding='utf-8')字符串不可被修改，所以二进制的字节也是不可被修改，如被切换或替换只是生成了一个新串，原始字符串不会被修改。

- bytearray() # 可修改的二进制字节格式，它时以array方式进行修改
- callable(x) # 判断对象是否可被调用
- chr(x) # 返回ascii码对应的字符
- ord(x) # 返回字对应的ascii码
- compible() # 将字符串转化为代码进行执行
- dict() # 字典
- dir() # 查看参数有什么方法可用
- divmode(x,y) # 除完返回商和余数的元组
- eval() # 把字符串变字典，也可把简单的数学算法进行计算，若像斐波那契那样的算法就需要采用exec()方法
- exec()
- filter() # 用于数据过滤
- lambda() # 匿名函数，lambda 只能处理简单的数学公式，最复杂只能到三元运算
- map() # 对传入的每个值进行处理，再把原来的结果覆盖掉
- reduce() # 在Python2中可以直接使用reduce，在Python3中需要引用functools
- reduce() 函数会对参数序列中元素进行累积。函数将一个数据集合（链表，元组等）中的所有数据进行下列操作：用传给 reduce 中的函数 function（有两个参数）先对集合中的第 1、2 个元素进行操作，得到的结果再与第三个数据用 function 函数运算，最后得到一个结果。
- set() # 集合set()函数创建一个无序不重复元素集，可进行关系测试，删除重复数据，还可以计算交集、差集、并集等。
- frozenset() # 不可变的集合
- globals() # globals()函数会以字典类型返回当前位置的全部全局变量。
- hash() #hash()用于获取取一个对象（字符串或者数值等）的哈希值。
- hex() # 用于将10进制整数转换成16进制，以字符串形式表示。
- locals(x) # locals() 函数会以字典类型返回当前位置的全部局部变量。对于函数, 方法, lambda 函式, 类, 以及实现了 __call__ 方法的类实例, 它都返回 True。
- max() # 返回字符串中最大的字母，或数组中的最大值。
- min() # 返回字符串中最小的字母，或数组中的最小值。
- object() # 在Python中一切皆为对象
- oct() # 将一个数字转化为八进制
- pow(x,y) # 返回x的y次方 的值。
- reversed(seq) # 返回一个反转的迭代器。
- round() # 返回浮点数x的四舍五入值。
- sorted() # 对所有可迭代的对象进行排序操作。

#### 4.解释一下什么是动态语言？动态强类型是指什么？

动态语言是一类在运行时可以改变其结构的语言：比如新的函数、对象、甚至代码都可以被引进，已有的函数可以被删除或是其他结构上的变化，
动态强类型要分成两部分理解，一部分是动态类型，另一部分就是强类型。
动态类型语言就是在运行时，确定类型的语言。即编译时月类型无关。一般在变量使用之前不需要声明变量类型，而变量的类型通常是有被赋值的值的类型决定。
强类型语言就是强制类型定义的语言。也就是说，一旦一个白能量被指定了某个数据类型，如果不经过强制转换，那么它就永远是这个数据类型了。
强类型定义语言是类型安全的语言。
#### 5.是否有编码规范的概念？采用的是那种编码规范

我理解的代码规范就是类似操作指南，最简单的就是变量的命名方式。对于个人来说使用好的编码规范可以提高自己代码的可读性。对于团队而言可以提高团队合作的效率、降低维护成本。
Python 中最有名的编码规范就是PEP 8-Python
Python PEP-8编码风格指南中文版

#### 6.解释一下深拷贝和浅拷贝

深拷贝需要导入copy模块，使用deepcopy()

    b = copy.deepcopy(a)

a和b完全拷贝了父对象和及其子对象，两者是完全独立的

浅拷贝使用copy

    b = a.copy()

a和b 是独立的对象，但他们的子对象还是指向同一对象（相当于引用）

#### 7.lambda的用法及其作用

下面是一个lambda的例子：

    g = lambda x:x+1

lamdba 定义了一个匿名函数，例子中的x为入口参数， x+1为函数体。如果用函数表示的话 ：

    def g(x):
        return x+1

lamdba 简化了函数定义的书写形式。lamdba的作用就是减少了单行函数的定义。

#### 8.解释一下闭包及其作用

在计算机科学中，闭包（Closure）是词法闭包（Lexical Closure）的简称，是引用了自由变量的函数。这个被引用的自由变量将和这个函数一同存在，即使已经离开了创造它的环境也不例外。

闭包的作用就是有一些功能需要重用但不足以定义为类的行为就可以使用闭包。闭包会比类占用更少的资源。装饰器就是闭包的一个应用，除此之外闭包还可以用于封装。

9.实现一个简单的装饰器，用来对某个函数的结果进行缓存

    import functools
    import time
    
    
    CACHE = {}
    
    
    def cache_it(func):
        @functools.wraps(func)
        def inner(*args, **kwargs):
            key = repr(*args, **kwargs)
            try:
                result = CACHE[key]
            except KeyError:
                resuslt = func(*args, **kwargs)
                CAHE[key] = result
            return result
        return inner
     
    
    import functools import time CACHE = {} def cache_it(func): @functools.wraps(func) def inner(*args, **kwargs): key = repr(*args, **kwargs) try: result = CACHE[key] except KeyError: resuslt = func(*args, **kwargs) CAHE[key] = result return result return inner

10.Python中集中容器类型的差别及使用场景有哪些？

11.列表推导式的使用和场景有哪些？

12.介绍一下yield的用法

13.常见的内置库有哪些？具体说明它们的用法

14.介绍一下你了解的 magic method （魔术方法）及其作用

15.解释一下面向对象的概念及其在编程中的作用

16.如何实现单例模式？

17.如何对python对象进行序列化？

18.是否能够熟练编写多线程和多进程程序？

19.使用socke编写一个简单的HTTP服务器，成功返回success即可

20.如何理解Python中的GIL？这对我们的日常开发有什么影响？

21.解释一下协程、线程和进程之间的差别


 

 

 

 

 

 

 

 

 

引用来源：

https://segmentfault.com/a/1190000004461404

https://foofish.net/python-closure.html

https://www.cnblogs.com/evening/archive/2012/03/29/2423554.html

https://kdboy.iteye.com/blog/407572

http://www.voidcn.com/article/p-uozlkadx-vt.html

https://blog.csdn.net/zxr15709447338/article/details/80872389

python关键字详解 - 削微寒 - 博客园

Python3 基础语法 | 菜鸟教程