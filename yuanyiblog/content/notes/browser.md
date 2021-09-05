---
title: "浏览器基本原理"
weight: 30
draft: true
---

# 浏览器原理

## 浏览器

目前的主流浏览器有五个：IE、Firefox、Safari、Chrome 和 Opera

浏览器的主要功能是向服务器发出请求，然后在浏览器窗口中呈现返回的资源

浏览器的主要组件有：

![](https://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/layers.png)

- 用户界面
- 浏览器引擎
- 渲染引擎
- 网络
- UI 后端
- JavaScript 解释器
- 数据存储

## 进程与线程

- 进程：资源（CPU、内存）分配的最小单位
- 线程：是在进程内部的程序运行单位

每打开一个新的标签页就新建了一个进程（如果后期标签页过多可能会合并进程）

浏览器中的主要进程：浏览器进程、第三方插件进程、GPU 进程、渲染进程

## 渲染进程

渲染进程也就是我们说的浏览器内核

### GUI 渲染线程


### JS 引擎线程



*JS 引擎线程与 GUI 渲染线程是互斥的无法同时进行，因为 JS 也可以操作 DOM，会影响渲染结果*

### 事件触发线程


### 定时触发器线程


### 异步http请求线程


## 事件循环

同步任务直接放入 JS 引擎线程中的执行栈中处理，异步任务放入事件触发线程中的事件队列中等待。

当 JS 引擎线程上的执行栈为空时，JS 引擎线程会询问事件触发线程，如果事件队列中有异步任务，就会被添加到执行栈中开始执行。








## 参考资料

[浏览器的工作原理：新式网络浏览器幕后揭秘](https://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/#Layered_representation)

[从浏览器多进程到JS单线程，JS运行机制最全面的一次梳理](https://juejin.cn/post/6844903553795014663#heading-0)
