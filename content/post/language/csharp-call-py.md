---
title: "C#调用Python"
date: 2022-01-22T23:15:26+08:00
draft: true
tags: ["c#","py","pythonnet"]
categories: ["language-engine"]
---

## Python

Python解释器或Python虚拟机有很多种实现，有CPython、PyPy、Jython以及IronPython等。CPython是最主流的实现。CPython同时也是别的虚拟机实现的参考解释器。PyPy是用Python实现的Python解释器，Jython是用Java实现运行在JVM上的解释器，IronPython是用Microsoft.NET CLR实现的解释器。除非解释器的选择非常非常重要，我们一般都用CPython。


## IronPython

[IronPython](https://ironpython.net/)当前最新的有2.7.11版本和3.4版本两个版本,使用IronPython可以很方便的和C#等.Net语言集成. 

[官方文档](https://ironpython.net/documentation/dotnet/)中有很多示例,因为本身IronPython就是.Net平台的实现,所以底层的数据类型用的一套.使用上没有什么差异:Array|List <---> list, Dictionary <---> dict

## Python.Net

[pythonnet](http://pythonnet.github.io/)


### C#调用Python

### Python调用C#

`pip install pythonnet`
以python为启动项也可以,安装pythonnet库,直接调用.net平台的dll

## IronPython vs Python.Net

都能在.Net平台调用python,两套引擎也有很多差异
|        | IronPython                         | Python.Net                    |
| ------ | ---------------------------------- | ----------------------------- |
| dict   | 直接对应C#的Dictionary             | C#中不能接受python的dict      |
| 其他库 | 不能使用numpy等CPython平台的其他库 | 直接使用CPython的生态及其他库 |


## 做一个Python引擎

### 简单的例子

一个按钮,一个文本输入框,执行python

### 提供一些库

定义一个c#类,提供方法,将实例化的对象通过setItem注入到mylocals,exec(compile('',mylocals))

