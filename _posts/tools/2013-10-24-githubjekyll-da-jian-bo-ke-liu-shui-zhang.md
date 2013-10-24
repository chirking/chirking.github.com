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

# jekyll主题

jekyllbootstrap提供的主题[http://themes.jekyllbootstrap.com/](http://themes.jekyllbootstrap.com/)  
当然，还可以去网上找其他人的主题  

```
rake theme:install git="https://github.com/jekyllbootstrap/theme-the-program.git"
```

也可以随时切换  

```
rake theme:switch name="the-program"
```

# jekyll目录结构

```
_config.yml:全局配置文件  
_includes:博客主题等  
_layouts:网页布局  
_plugins:插件  
_posts:文章  
_site:最终生成的静态站点  
assets:静态文件，js，css，图片等  
index.md:主页  
```

# 中文支持

1.ruby目录下修改gems/jekyll-0.11.0/lib/jekyll/convertible.rb


```
self.content = File.read(File.join(base, name), :encoding => "utf-8")
```

2.Jekyll默认的markdown解析器maruku对中文支持不够完善，换成RDiscount解析器

```
gem install rdiscount
```

在_config.yml文件中，添加一行：

```
markdown: rdiscount
```

3.rake脚本不支持中文，修改Rakefile文件

```
desc "Begin a new post in #{CONFIG['posts']}"  
task :post do  
  abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])  
  title = ENV["title"] || "new－post"  
  # 新增用来接收category和description参数  
  category = ENV["category"] || "default"  
  description = ENV["description"] || ""  
  tags = ENV["tags"] || "[]"  
  # 新增用来将汉字转换成拼音，因为url好像不支持中文。当然在文件顶部  require了Hz2py  
  slug = Hz2py.do(title, :join_with => '-', :to_simplified => true)  
  slug = slug.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')  
  begin  
    date = (ENV['date'] ? Time.parse(ENV['date']) :   Time.now).strftime('%Y-%m-%d')  
  rescue Exception => e  
    puts "Error - date format must be YYYY-MM-DD, please check you typed it correctly!"  
    exit -1  
  end  
  # 新增，首先判断分类目录是否存在，不存在则创建  
  filename = File.join(CONFIG['posts'], category)  
  if !File.directory?(filename)  
    mkdir_p filename  
  end  
  filename = File.join(filename, "#{date}-#{slug}.#{CONFIG['post_ext']}")  
  if File.exist?(filename)  
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'  
  end  
  # 新增用户提示，在创建博客之前最后再检查一次是否按照自己的需求正确创建  
  # User confirm   
  # abort("rake aborted!") if ask("The post #{filename} will be created in category #{category}, are you sure?", ['y', 'n']) == 'n'  
  
  puts "Creating new post: #{filename}"  
  open(filename, 'w') do |post|  
    post.puts "---"  
    post.puts "layout: post"  
    post.puts "title: \"#{title.gsub(/-/,' ')}\""  
    post.puts 'description: ""'  
    post.puts "category: \"#{category.gsub(/-/,' ')}\""  
    post.puts "tags: #{tags}"  
    post.puts "---"  
    post.puts "{% include JB/setup %}"  
  end  
end # task :post  
```  

这里把中文和分类都支持了，可以这样创建文章：

```
post title="中文文子" category="中文" date="2013-01-01" tags="中国 文字" description="聊聊中文文字"
```

# 坚持写下去