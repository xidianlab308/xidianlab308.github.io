---
weight: 4
title: "24级招新题"
date: 2024-09-30T09:40:28+08:00
draft: false
author: "yaoliu"
description: "本篇文章针对24级进行考核."
resources:
- name: 
  src: 

tags: ["Markdown", "HTML"]

lightgallery: true
---

针对24级的同学，我们准备了以下的小任务，难度并不是很大，各位同学可以挑选自己感兴趣的部分完成。同学们可以选择自己感兴趣的部分完成。同时可以制作一个简历(推荐使用WonderCV)，简要介绍一下自己。

<!--more-->

# 前置篇：学习Markdown

## markdown的概念与使用

Markdown 是一种轻量级的标记语言，可用于在纯文本文档中添加格式化元素。Markdown 由 John Gruber 于 2004 年创建，如今已成为世界上最受欢迎的标记语言之一。本文即用markdown编写。

使用markdown写东西可以使双手在95%的时间都不用离开键盘，与vim同理，可以使人更专注，更容易进入心流状态。且markdown语法比较简单，没有过多的学习成本，可以使用markdown写笔记，博客(博客园,知乎都支持markdown编辑)。

github上的项目都有一个叫README的文件，用于介绍你的项目的功能特性，启动方式，使用示例等等。该文件由markdown语法编辑。

markdown的学习成本极低，你可以在他的[官网](https://markdown.com.cn/intro.html)迅速学会它。

## 选择一个markdown编辑器

markdown的官网上推荐了以下编辑器：

1. 现代编辑器
VSCode / Atom

2. 传统编辑器
Vim / Emacs / Sublime Text / Notepad++

3. IDE 自带编辑器
IntelliJ IDEA / Android Studio / WebStorm

4. 专用编辑器
Ulysses / Mou / 妙言 / Markpad

5. 在线编辑器
各种支持 Markdown 的网站都提供了在线 Markdown 编辑器

除此之外，我个人推荐使用Notion或飞书。


# 前置篇：搭建Vscode的C语言环境

## 理解编译与汇编

如果你使用DEVC++写C语言的话，那你可能对C语言程序的理解停留在点了一个绿色按钮，然后弹出来一个黑乎乎的命令行，这是我们绝大多数人对编程的第一印象。 **Thats not cool at all！**

但请不要灰心，虽然你现在做的只是打印点星星或是计算方程的根，但做这些事情跟写一个网站，做一个游戏没有本质的区别，代码最后都会变成01的序列，然后在机器上执行罢了。那么代码从人类能理解的语言到机器能理解的语言，这中间到底发生了什么？这对配置一个Vscode的C语言开发环境，乃至理解编程的本质都有很大的帮助。

首先有一个工具叫做gcc，当你点devc++的绿色小按钮时，实际上就是执行了一个gcc的编译命令，中间发生了什么，可以参考这篇[博客](https://zhuanlan.zhihu.com/p/111500914)。

```
这个时候你可能会问了：在没有gcc之前是怎么编译出来gcc的呢？这个问题好比是先有鸡还是先有蛋一样，实际上这设计到编译原理里的一个重要问题。你可以从gcc的wiki中找到答案。https://zh.wikipedia.org/wiki/GCC
```

## 配置你自己的vscode

vscode是微软的一款开源编辑器，他的优点在于轻量级，可拓展性好，界面美观。

使用vscode写c语言需要一定的门槛，当你理解编译与汇编的原理后，就可以很轻松的搭建好环境了。

具体要配置的东西包括：gcc可执行文件的路径，gdb可执行文件的路径，要编译的c语言文件的路径和生成的可执行文件的路径。

可参考该[问题](https://www.zhihu.com/question/333233461/answer/1090969691)下面的回答。

# 前置篇：学习使用Git，创建一个Github账号

git是代码版本控制工具，简单来说，代码开发是一个迭代的过程，可能新增一个功能就全盘崩溃了，这时就要回退版本，这就是版本控制的意义。

git由linux的开发者，传奇程序员Linus Torvalds开发。你可以在[这里](https://liaoxuefeng.com/books/git/introduction/index.html)入门git。


# 前置篇：矩阵的概念与运算

## 线性代数基本概念

线性代数（英语：linear algebra）是关于向量空间和线性映射的一个数学分支。它包括对线、面和子空间的研究，同时也涉及到所有的向量空间的一般性质。

你可以通过阅读博客来了解线性代数和矩阵运算的基本概念，如果你要深入学习，我们推荐吉尔伯特的线性代数课程。

[线性代数](https://www.bilibili.com/video/BV1SY4y1b7Ti/?spm_id_from=333.337.search-card.all.click)

# 进阶篇(可选)

创建一个github账号并用任意面向对象语言实现一个矩阵类并实现简单的运算，附有README