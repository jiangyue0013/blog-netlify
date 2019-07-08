---
title: '''Django中Queryset的使用（一）'''
date: 2019-06-30 22:14:15
tags: [python, django, Queryset]
---
### Queryset的使用

Queryset是懒加载的，部分支持链式调用。

 

支持链式调用的接口：

 

* all接口: 用于查询所有数据

* filter接口: 根据条件进行过滤

* exclude接口: 同filter，只是相反的逻辑

* reverse接口: 把Queryset中的结果倒序排列

* distinct接口: 用来进行去重查询

* none接口: 返回空的Queryset

 

不支持链式调用的接口：

 

* get接口：用于查询，存在返回对应的实例，不存在，则抛出DoesNotExist异常

* create接口：直接创建一个Model对象

* get_or_create接口：根据条件查找，如果没有查找到，就调用create创建

* update_or_create接口：同get_or_create，只是用来做更新操作

* count接口：用于返回Queryset有多少条记录

* latest接口：用于返回最新一条记录，但需要在Model的Meta中定义：get_latest_by = <用来排序的字段>

* earliest接口：同上，返回最早的一条记录

* first接口：从当前Queryset记录中获取第一条

* last接口：同上，获取最后一条

* exists接口：返回True或者False，只需要判断Queryset是否有数据用这个接口最合适

* bulk_create接口：同create，用来批量创建记录

* in_bulk接口：批量查询

* update接口： 用来根据条件批量更新记录

* delete接口： 同update，这个接口是用来根据条件批量删除记录。update和delete都会出发Django的signal

* values接口:当我们明确知道只需要返回某个字段的值，不需要Model实例时，可以使用

* values_list接口：同values，但直接返回的是包含tuple的Queryset