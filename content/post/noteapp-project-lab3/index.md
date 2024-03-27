---
title: "Noteapp Lab 3"
date: 2022-05-04T00:00:00+08:00
draft: false
---

# 项目简介

NoteApp 是一个笔记软件，采用前后端分离的开发模式。

用户可以通过网页前端注册账户，并通过注册时的信息登录。
登录后可以看到自己创建的所有笔记（notes），同时支持新建、删除、编辑笔记。

Lab 3 的内容为实现一个 NoteApp 后端的简易版。

# Lab 3 具体要求

后端的样例项目在 [https://github.com/truc0/noteapp-lab/tree/v1](https://github.com/truc0/noteapp-lab/tree/v1).
Lab 3 完成的标志是通过所有测试样例。

## 运行测试

测试代码全部位于 [https://github.com/truc0/noteapp-lab/blob/v1/notes/tests.py](https://github.com/truc0/noteapp-lab/blob/v1/notes/tests.py).
如果需要用到该文件中定义的函数，建议复制到项目文件中（即不要引入`tests.py`）。

你可以通过以下命令运行测试：

```bash
python manage.py test
```

## 项目描述

该项目需要实现对 Note 的增删改查功能，输入和输出均使用`json`格式。

项目需要实现的API文档可以在[openapi.yml](https://raw.githubusercontent.com/truc0/noteapp-lab/v1/openapi.yml)里找到，
将其复制到[Swagger](https://editor.swagger.io)中可以以可视化方式查看该文件。

在`Django`中，你可以使用`django.http.response.JsonResponse`构造一个`json`格式的 Response。
在Lab 3中，你可能需要将`list`等类型不是`dict`的元素作为`JsonResponse`的第一个参数。
在这种情况下，`Django`会抛出一个异常，这是因为在`ECMAScript 5`标准之前，返回一个数组可能导致[安全问题](http://haacked.com/archive/2009/06/25/json-hijacking.aspx/)。
然而现在大多数浏览器已经支持更高版本的`ECMAScript`，所以在Lab 3中我们忽略此问题。

你可以在`JsonResponse`中将关键字参数`safe`赋值为`False`以防止`Django`抛出错误，具体实现如下。

```python
def index(request):
    ...
    return JsonResponse([], safe=False)
```

## 扩展练习

这个练习十分简单，但是并不能被实际应用。

尝试使用自己编写的中间件（Middleware）解决`CORS`和`CSRF`的问题。

