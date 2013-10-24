---
layout: post
title: "Markdown基础教程"
description: ""
category: "tools"
tags: markdown
---
{% include JB/setup %}

# Part 1. Mrakdown 基础

### 换行

**普通换行符被当成空格:**

	hello
	world!
	
hello
world!
	
**行末2个空格加上换行符才是换行:**

	hello  
	world!
	
hello  
world!
	
**2个换行符号是硬换行:**

	hello
	
	world!
	
hello
	
world!

### 粗体和斜体

	*斜体* _斜体_
	**粗体** __粗体__

*斜体* _斜体_  
**粗体** __粗体__

### 链接和邮箱

**行内:**

	例: [这是一个链接](www.test.com "测试")

例: [这是一个链接](www.test.com "测试")

**行号列标表示法:**

	例: [这是一个链接][id1]. 在文档内的任何地方，定义这个链接

	[id1]:www.google.com "测试"
	
例: [这是一个链接][id1]. 在文档内的任何地方，定义这个链接

[id1]:www.google.com "测试"

### 邮箱

	邮箱地址: <xxx@gmail.com>.

邮箱地址: <xxx@gmail.com>.

### 图片

**行内:**

	实验室![图片](http://smallerapp.com/favicon.ico "测试图片")图片 
	
实验室![图片](http://smallerapp.com/favicon.ico "测试图片")图片 

**行号列标表示法:**

	![图片][2]
	[2]: http://mouapp.com/Mou_128.png "测试图片"

![图片][2]
[2]: http://mouapp.com/Mou_128.png "测试图片"

<!--more-->
	
### 标题

**方式1:**

	标题1
	===
	标题2
	---

标题1
===
标题2
---

**方式2:**
	
	# 标题1
	## 标题2
	###### 标题6

# 标题1
## 标题2
###### 标题6

### 列表

**列表1:**

	1. 第一行
		1. 子列表
		2. 子列表第二行
	2. 第二行

1. 第一行
    1. 子列表
    2. 子列表第二行
2. 第二行
	
**列表2:**

	* 第一行
		内容
	* 第二行
		* 4个空格生成子列表
		* 子列表第二行
	* 第3行
		- 4个空格生成子列表
		- 子列表第二行
	
* 第一行
    内容
* 第二行
    * 4个空格生成子列表
    * 子列表第二行
* 第3行
    - 4个空格生成子列表
    - 子列表第二行
	
### 引用

	> 引用
	> > 子引用
	
	> ### 引用内标题
	>
	> * 引用内列表
	> * 第二行
	
> 引用
> > 子引用

> ### 引用内标题
>
> * 引用内列表
> * 第二行
	
### 代码

**行内**

	行内`hello world`
	包含特殊符号 ``` `hello world` ```

行内`hello world`  
包含特殊符号 ``` `hello world` ```
	
**代码块**
	
	每行开始4个空格或1个tab:
	
		hello world!
		hello world!
		
每行开始4个空格或1个tab:

    hello world!
    hello world!

**包裹代码块**

	三个`包裹:
	```
	代码块
	hello
	world!
	```

三个`包裹:
```
代码块
hello
world!
```
		
### 横线

	---
	- - -
	***
	* * *

---
- - -
***
* * *

### 删除

	~~删除~~

~~删除~~


# part 2. Markdown 进阶

	
### 表格

	First Header | Second Header | Third Header
	:----------- | :-----------: | -----------:
	Left         | Center        | Right
	Left         | Center        | Right

First Header | Second Header | Third Header
:----------- | :-----------: | -----------:
Left         | Center        | Right
Left         | Center        | Right
	
### 锚点

**定义一个带锚点的标题:**
	
	## [标题1](id:锚点id)
	
**链接点击跳转到标题:**

	[跳到标题1](#锚点id)

## [标题1](id:锚点id)
[跳到标题1](#锚点id)

### 脚标

**脚标引用:**
	
	《Life of pi》[^1]

**脚标定义:**

	[^1]:《Life of pi》

《Life of pi》[^1]
[^1]:《Life of pi》
