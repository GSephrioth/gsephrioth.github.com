---
layout: post
title:  "MAC搭建github Page"
image: ''
comments: true
date:   2017-01-11 00:06:31
description: ''
serie: learn
---

## 初始环境

Mac version : Mac book Pro 15’ inch with touch bar
Memory : 16G
CUP : 2.7 GHz
OS version : 10.12.1
原生ruby version 2.0.0

### 1.安装 Homebrew
{% highlight ruby %}
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)”
{% endhighlight %}
安装位置 : /usr/local

### 2.安装 ruby
{% highlight ruby %}
$ brew install ruby
$ ruby —version
ruby 2.3.3p222 (2016-11-21 revision 56859) [x86_64-darwin16]
{% endhighlight %}
安装位置：/usr/local/Cellar

### 3.安装 RubyGems
{% highlight ruby %}
$ gem update —system
$ gem -v
2.6.8
{% endhighlight %}
安装位置在 ruby 内部

如果源不好用的话更换源
{% highlight ruby %}
$ gem sources --remove https://rubygems.org/
$ gem sources -a http://ruby.taobao.org/
{% endhighlight %}

### 4.安装 jekyll 
{% highlight ruby %}
$ gem install jekyll
$ Jekyll -v
jekyll 3.3.1
{% endhighlight %}
安装位置：/usr/local/bin

### 5.创建 jekyll 项目
{% highlight ruby %}
$ jekyll new myblog
{% endhighlight %}

myblog位置: ~/code/myblog

### PS: 在这一步出现问题 缺少库文件 bundler
{% highlight ruby %}
$ gem bundler
{% endhighlight %}

### 6.测试运行：
{% highlight ruby %}
$ jekyll serve

Configuration file: /Users/michellezhou/Blog/cenalulu.github.io/_config.yml
Source: /Users/michellezhou/Blog/cenalulu.github.io
Destination: /Users/michellezhou/Blog/cenalulu.github.io/_site
Generating...
done.
Auto-regeneration: enabled for '/Users/michellezhou/Blog/cenalulu.github.io'
Configuration file: /Users/michellezhou/Blog/cenalulu.github.io/_config.yml
Server address: http://127.0.0.1:4000/
Server running... press ctrl-c to stop.
{% endhighlight %}

访问 localhost:4000 得到结果页面

<img src="{{ "/assets/img/github-page/successfully-run-jekyll.png"}}" alt="">




