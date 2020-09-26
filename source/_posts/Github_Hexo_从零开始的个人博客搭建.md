---
title: Github_Hexo_从零开始的个人博客搭建
date: 2020-09-26 18:27:41
tags: 
- git 
- hexo 
- 博客搭建
catagories: 
- 目标检测
description: 一起来搭建博客吧！
---
# 为什么要搭建博客
* ~~因为太菜~~
* 因为热爱分享
* 对所学知识进行总结

# 如何使用github+hexo搭建博客
## 准备工作
### 安装nodejs
* 什么是nodejs，为什么要安装
* 如何安装
* 相关安装命令
### 注册github
### 安装git
* 什么是git
git是目前最先进的分布式版本控制系统,他能够跟踪所有文本文件的内容改动和文件大小变化，比如txt文件、md文件、网页、程序代码等。同时他也能跟踪图片、音频、视频等文件的改动，但由于这些文件本质属于二进制编码，因此具体改了什么地方，git是不知道的。
* git语法学习
git教程有很多，下面是经过整理后的个人非常推荐的网站:
* [git使用教程](https://www.cnblogs.com/tugenhua0707/p/4050072.html)讲解非常详细，强烈推荐先看这个
* [progit第一版](https://gitee.com/progit/)
* git常见语法总结
``` bash
# 文件的产生、读取、写入、复制、提交
# 将当前所在目录变成git可以管理的仓库（repository）
git init
# 查看当前分支
git branch
# 创建一个名称为taishiji的分支 
git branch taishiji
# head指针指向source，说人话就是切换到source分支
git checkout -b source 
# 产生xxx文件的副本，并将该文件副本移动到暂存区（stage）中
git add xxx 
# 查看文件具体修改内容
git diff readme.md
# 查看文件修改记录 空格向下 b向上
git log
# 以非常漂亮的格式，通过只查看注释来查看文件的修改
git log –pretty=oneline
# 查看当前所处分支，以及是否有文件内容已经修改，但并未提交的情况
# 在提交文件之前和提交之后，推荐先使用该命令进行核对和确认
git status
# 取出暂存区中的文件副本，并将其保存到git仓库中，同时附上修改注释“提交readme.md文件”
git commit -m "提交readme.md文件"
# 将版本回退到上一个版本
git reset --hard HEAD^
# 将版本回退到上上个版本
git reset --hard HEAD^
```
## 搭建个人博客
### 新建仓库
### 安装hexo
* 什么是hexo，为什么要安装
* 如何安装
* hexo相关命令
### 预览搭建好的基本博客
## 美化博客
### 主题下载和筛选
### 推荐主题：Next
## 写博客
### 初识markdown
**markdown**是一种标记语言，这种标记语言不需要掌握复杂的html语言编程，仅仅通过简单的语法，就可以完成文字的撰写、图片的添加甚至音频的插入，非常适合于完成博客内容的撰写和网页的搭建。
### markdown语法的学习
具体语法可参照[Markdown 语法说明 (简体中文版)](https://www.appinn.com/markdown/#%E9%93%BE%E6%8E%A5),大约半小时左右就可以快速上手入门。这里就简单展示一下一些常用的语法
``` python
# 一级标题
## 二级标题
### 三级标题
[原图是如何映射为特征图的呢](https://blog.csdn.net/jingtingxu369/article/details/84800154) 插入外部网页链接
```
# 搭建过程中遇到的坑（都是泪）
## 错误1
![由于代理问题导致的错误](https://github.com/baltam/tupian/raw/master/Github_Hexo_%E4%BB%8E%E9%9B%B6%E5%BC%80%E5%A7%8B%E7%9A%84%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BA/%E9%94%99%E8%AF%AF1.png)

### 错误原因
### 解决方案
## 错误2
### 错误原因
### 解决方案
# 强迫症患者需要解决的问题
## 不同的电脑上如何修改博客
## 如何提高打字准确度
## 寻找更简单的图床方法
# 参考文献or网站
* [【Hexo搭建独立博客全纪录】（一）使用Git和Github](https://baoyuzhang.github.io/2017/04/28/%E3%80%90Hexo%E6%90%AD%E5%BB%BA%E7%8B%AC%E7%AB%8B%E5%8D%9A%E5%AE%A2%E5%85%A8%E7%BA%AA%E5%BD%95%E3%80%91%EF%BC%88%E4%B8%80%EF%BC%89%E4%BD%BF%E7%94%A8Git%E5%92%8CGithub/)
* [GitHub-Hexo-从零开始搭建个人博客](https://mumaxu.github.io/2018/12/09/GitHub-Hexo-%E4%BB%8E%E9%9B%B6%E5%BC%80%E5%A7%8B%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)