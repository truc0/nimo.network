---
title: "Noteapp Lab 2"
date: 2022-04-02T15:00:00+08:00
draft: false
---

# 项目简介

NoteApp 是一个笔记软件，采用前后端分离的开发模式。

用户可以通过网页前端注册账户，并通过注册时的信息登录。
登录后可以看到自己创建的所有笔记（notes），同时支持新建、删除、编辑笔记。

项目的前端创建与后端搭建可以参照[Lab 1](/post/noteapp-project-lab1)。

## 模型关系简介

本项目中的模型（Model）主要有两个：用户（User）和笔记（Note）。

用户和笔记是一对多的关系，即：
- 每个用户可以拥有若干个笔记
- 每个笔记均属于（且只能属于）一个用户

具体表现为在笔记模型中有一个`owner`字段，此字段的值为该笔记所属的用户的id。

# Lab 2 内容简介

在[Lab 1](/post/noteapp-project-lab1)中我们完成了注册/登录功能，
在Lab 2中，我们将会完善该应用的主要功能，即对**Notes**的`CRUD`操作。

## 用户验证

由于用户与笔记有一对多的关系，我们要求每个用户只能对**自己的笔记**进行
增加、删除、更改、查询的操作。这意味着对笔记进行任何操作都必须要先登录。

在Lab 1中我们已经完成了登录页面的设计与功能。该页面可以实现用户的登录，并获得一个`token`。
前端需要在请求中附带`token`以证明自己的身份，后端会利用`token`进行鉴权。

具体的实现为给后端发送请求时加上一个名为`Authentication`的HTTP请求头（HTTP Request Header）。
该请求头的值格式为`Token <token>`，其中`<token>`为登录是得到的`token`（不含尖括号）。

## 在请求中附带请求头

`fetch`API和`axios`库都可以方便地设置请求头。

### Fetch

我们可以在`fetch`函数的`init`参数（第二个参数）中设置`headers`字段以添加请求头。如：

```js
fetch('http://localhost:8080'. {
  method: 'POST',
  mode: 'cors',
  headers: {
    Authentication: 'Token <replace with your token>'
  }
})
```

参考网站为：[https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

### Axios

`axios`函数同样允许在`config`参数中设置`headers`。`axios`的用法有很多，下例只是其中一个。

```js
axios.request('http://localhost:8080', {
  headers: {
    Authentication: 'Token <replace with your token>'
  }
})
```

## 具体内容

根据[openapi.yml](https://raw.githubusercontent.com/truc0/simple-noteapp/master/openapi.yml)提供的接口
实现笔记的创建、更新、查询、删除功能，并对可能发生的异常进行处理（如用户访问一个不属于自己的笔记时会出错）。

推荐的`path`与具体功能的对应关系如下：
- `/`：列出当前用户的所有笔记
- `/notes/create`：创建笔记的页面
- `/notes/:id`：查询指定id的笔记
- `/notes/:id/edit`：编辑指定id的笔记

细心的读者可能会发现上面的`id`前面有个冒号，这是带参数的动态路由的表示。

由于为每篇笔记都编写一条路由十分麻烦，也不适用于笔记数量不定的情况。
[Vue Router](https://router.vuejs.org/zh/guide/)提供了带参数的动态路由，
相关文档为[https://router.vuejs.org/zh/guide/essentials/dynamic-matching.html](https://router.vuejs.org/zh/guide/essentials/dynamic-matching.html).

