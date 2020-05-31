---
layout: post
title:  "在macOS上安装Jekyll时遇到的问题"
date:   2020-05-30 17:26:21 +0800
tags: jekyll
color: rgb(0, 191, 255)
cover: '../assets/jekylltry.png'
subtitle: 'jekyll初尝试！'
---

第一次搭博客，留个记录。


### 错误1

安装Jekyll的分页插件：`gem install jekyll-paginate`

报错，权限问题

>ERROR:  While executing gem ... (Gem::FilePermissionError) You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.

查询之后发现是mac自带的ruby的问题，该文件夹只允许root用户操作。在前面加上`sudo`后问题解决。

### 错误2

`jekyll server`

报错，缺少包

>Could not find public_suffix-3.0.2 in any of the sources (Bundler::GemNotFound)

运行

`bundle install --path vendor/cache`

ps: 由于某种众所周知原因，在国内使用bundle install非常慢，需要把gem的源换成RubyChina的：

gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/

### 错误3

再次运行`jekyll server`

报错

You have already activated public_suffix 4.0.5, but your Gemfile requires public_suffix 3.0.2. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)

按照提示，改成

`bundle exec jekyll server`

问题解决！！！