---
title: "关于本站"
date: 2022-01-19T22:45:33+08:00
draft: false
tags: ["hugo","blog"]
categories: ["杂技浅尝"]
---

### 安装hugo

`choco install hugo-extended --confirm`

### 创建文档库

`hugo new site {name}`

### 选择主题

[theme库](https://themes.gohugo.io/)

### 下载主题

根据选择的主题地址下载: `git clone https://github.com/olOwOlo/hugo-theme-even themes/even`

### 应用配置

拷贝主题示例库的config.toml文件

### 新建文章

`hugo new post/hello.md`

配置说明
```
draft: true                 #是否草稿状态
tags: ["hugo","blog"]       #所在标签
categories: ["杂技浅尝"]    #所在分类
```

### 编写模式

`hugo server -D`

可在编码过程中,即时预览[http://localhost:1313](http://localhost:1313)

### 发布

`hugo -D`

将结果发布到public文件夹

### 源码

本站源码发布在github: [jiajiawei/blog](https://github.com/jiajiawei/blog.git)

### ci/cd

我还不会...

未完待续...