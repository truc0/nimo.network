---
title: "0x00 常用工具"
date: 2021-10-08T16:05:16+08:00
draft: false 
---

`Web`开发主要分为前端（`Frontend`）和后端（`Backend`）。后端主要负责数据的处理、存储等功能，前端则主要负责对数据的展示和与用户的交互。以你部后台为例，虽然网管员和普通用户能看到的内容不同，但是都属于数据的展示和新数据的输入，故均属于前端范畴。用户和网管员都可以在前端中提交报修请求，报修请求会由前端发送到后端，后端的处理流程大致如下：
1. 用户是否为网管员
2. 如果是用户，验证该用户是否有未完成的报修
3. 确认无误后将请求保存到数据库


## Web 前端开发相关工具

前端常用的工具如下

- [NodeJS](https://nodejs.org): `NodeJS` 可以让开发者在非浏览器的环境下运行`Javascript`
- [NPM](https://nodejs.org): `NPM` 是 `NodeJS` 的一个包管理器，一般会在安装`NodeJS`的时候自动安装
- [Yarn](https://yarnpkg.com): **[Optional]** Yarn 是`NPM`的另一个包管理器（据说比`NPM`好一些）

**注意**: 我们**并不**推荐安装 _最新版_ 的`NodeJS`和`NPM`。一个更加明智的选择是安装`LTS(Long Term Support)`版本（当前是`v14.18.x`）。我们将会使用最新的`LTS(Long Term Support)`版本。

### NodeJS Version Manager (Optional)

`NodeJS`开发迭代的速度非常快，导致有些现在仍在使用的项目用的`NodeJS`版本与当前版本相差甚远。有些使用低版本的项目不能直接用高版本运行，所以对于开发人员来说，在自己的电脑上安装多个`NodeJS`版本对开发有很大的帮助。`NVM (Node Version Manager)`是其中一个解决方案。

但是在本学期的学习中，我们的项目均会使用最新的`LTS`版本，所以这并不是必须的。

`NVM`可以在[Github](https://github.com/nvm-sh/nvm)找到。

## 项目管理

[Git](https://git-scm.com)是一个被广泛使用的版本控制工具，在团队协作中常有突出的作用。

我们强烈建议在开始做项目之前安装并学习使用[git](https://git-scm.com)。

一些推荐教程如下：
- [Learn Git Branching](https://learngitbranching.js.org/): 建议完成`Introduction Sequence`和`Ramping Up`两个章节
- [Doc from Git SCM](https://git-scm.com/doc): （笔者也没看过）

你可以在[Github](https://github.com)上创建一个账号用以练习。

祝好！
