---
title: 博客开发的痛苦记录-giscus评论系统的报错和解决
categories: 博客开发相关
tags: [Hexo, NexT, Giscus, 痛苦, 挑战, 问题解决]
toc: true
date: 2025-08-25 10:32:34
updated: 2025-08-25 10:32:34
description: 文章回顾了一名 Hexo 博客新手，最近尝试在 Next 主题中集成 Giscus 评论系统时，遇到的一个棘手的模板渲染错误，包括错误内容、解决思路和解决方案。
---

# 1 问题背景
{% asset_img idea1.jpg 图1：menci使用的giscus评论系统 %}

**好奇心跑断腿**：偶像menci的博客使用giscus评论系统。通过这个系统，网友可以对博客文章进行评论。

## 1-1 查看博客框架

方法1：使用命令行
```bash
npx hexo -v
INFO  Validating config
hexo: 7.3.0
hexo-cli: 4.3.2
node: 20.19.3
```
方法2： github博客使用的是`hexo`框架，所以是Hexo项目。在hexo项目根目录下的package.json文件中查看 Hexo 的版本，在文件中找到"hexo"字段，其对应的值就是 Hexo 的版本号

```python
{
  "hexo": {
    "version": "7.3.0"
    }
}
```

## 1-2 查看博客主题

方法1：从hexo项目中打开 Next 主题目录，一般是`themes/next`，找到该目录下的package.json文件，其中"version"字段对应的值就是 Next 主题的版本号。
```python
{
  "name": "hexo-theme-next",
  "version": "7.8.0",
}
```

## 1-3 要实现的功能和发生的错误

要实现的功能：在 `Next` 主题中集成 `Giscus `评论系统，说人话就是，在每个博客下面添加评论区
错误类型：模板渲染错误

# 2 遇到的问题

**问题描述**：当使用`npx hexo clean && npx hexo s`命令进入本地浏览器浏览博客渲染效果时，发生了以下错误：
{% asset_img error1.jpg 图1：心烦的报错1 %}

```bash
Unhandled rejection Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig) [Line 36, Column 23]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig) [Line 54, Column 17]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_partials\head\head-unique.swig) [Line 10, Column 23]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig) [Line 3, Column 3]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_partials\header\index.swig) [Line 6, Column 15]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_partials\header\sub-menu.swig) [Line 2, Column 29]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_partials\header\sub-menu.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig) [Line 5, Column 3]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig) [Line 10, Column 14]
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_partials\pagination.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_partials\comments.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_partials\languages.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_third-party\math\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\index.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\_third-party\quicklink.swig)
  Template render error: (E:\baltam.github.io\themes\next\layout\inject\bodyEnd\giscus.swig)
  Error: Unable to call `next_data`, which is undefined or falsey
    at Object._prettifyError (E:\baltam.github.io\node_modules\nunjucks\src\lib.js:32:11)
    at E:\baltam.github.io\node_modules\nunjucks\src\environment.js:464:19
    at Template.root [as rootRenderFunc] (eval at _compile (E:\baltam.github.io\node_modules\nunjucks\src\environment.js:527:18), <anonymous>:45:3)
    at Template.render (E:\baltam.github.io\node_modules\nunjucks\src\environment.js:454:10)
    at E:\baltam.github.io\themes\next\scripts\renderer.js:32:29
    at _View._compiled (E:\baltam.github.io\node_modules\hexo\dist\theme\view.js:120:67)
    at _View.render (E:\baltam.github.io\node_modules\hexo\dist\theme\view.js:37:21)
    at E:\baltam.github.io\node_modules\hexo\dist\hexo\index.js:60:29
    at tryCatcher (E:\baltam.github.io\node_modules\bluebird\js\release\util.js:16:23)
    at E:\baltam.github.io\node_modules\bluebird\js\release\method.js:15:34
    at RouteStream._read (E:\baltam.github.io\node_modules\hexo\dist\hexo\router.js:43:9)
    at Readable.read (node:internal/streams/readable:739:12)
    at resume_ (node:internal/streams/readable:1257:12)
    at process.processTicksAndRejections (node:internal/process/task_queues:82:21)
```

# 3 解决思路

不知道如何下手
**解决思路1**：无

# 4 消融实验

实验内容：在`themes\next\_config.yml`文件中，将`Comments Settings`板块中`giscus`部分的代码取消注释
实验结果：使用`npx hexo clean && npx hexo s`命令，在本地服务器上预览修改，**发生报错**

实验内容：在`themes\next\_config.yml`文件中，将`Comments Settings`板块中`giscus`部分的代码进行注释
实验结果：使用`npx hexo clean && npx hexo s`命令，在本地服务器上预览修改，不会发生报错




# 5 最终解决方案
**是否解决**：未解决