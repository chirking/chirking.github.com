---
layout: post
title: "github+jekyll搭建博客流水帐"
description: ""
category: "tools"
tags: github
---
{% include JB/setup %}

# GitHub Pages

github pages是github提供的免费动态页面托管服务，我们可以通过github pages来搭建Blog。

# Jekyll

Jekyll是一个静态站点生成器，通过jekyll生成静态站点后，就可以提交到github，通过github pages生成博客了。

Jekyll支持markdown生成html，所以我们可以用markdown来写博客了。

生成的页面是纯静态的，动态功能只能用外部服务，比如评论可以用disqus。

# jekyll-bootstrap

jekyll-bootstrap简化了jekyll搭建Blog的过程，[jekyll-bootstrap官网](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)说是3分钟搭建好Blog。

# Jekyll安装

Jekyll是ruby实现的，先要安装ruby，然后安装jekyll。  
```
gem install jekyll
```

# 创建github repository
创建一个名为 USERNAME.github.com 的github 仓库

# 初始化jekyll到github
```
git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
cd USERNAME.github.com
git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
git push origin master
```
大概过10分钟，你就可以通过 USERNAME.github.com.git 看到你的博客了。

# 本地启动

进入刚刚的github项目本地目录，执行  
```
jekyll serve
```  
你可以在本地看到你的博客了[http://localhost:4000/](http://localhost:4000/)  

# 写文章

```
rake post title="Hello World"
```  
命令在_post文件夹下创建了一个.md文件，可以用本地的markdown编辑器来写博客了。

# push到github

```
git add .
git commit -m "Add new content"
git push origin master
```

# 

# jekyll目录结构
```
_config.yml:全局配置文件
_includes:博客模板等
_layouts:网页布局
_plugins:插件
_posts:文章
_site:最终生成的静态站点
assets:静态文件，js，css，图片等
index.md:主页
```
