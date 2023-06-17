---
layout: post
title: about compose of jekyll
date: 2023-06-17 14:53 +0800
---
这个博客内容主要是展示有关于`jekyll compose`的相关用法，主要展示一些关于它的语法使用要点 

在这里贴出该插件的源地址：[Jekyll-Compose][compose]

[compose]: https://github.com/jekyll/jekyll-compose

如果你需要安装这个插件，那么你需要在项目的`Gemfile`文件中添加以下代码段：  
````ruby
gem 'jekyll-compose', group: [:jekyll_plugins]
````
然后运行：
````ruby
bundle
````
### 如何使用
如果是想通过这个文本来寻找指令的话，大可不必。你可以直接在项目的根目录下运行`bundle exec jekyll help`来查看相关的全部指令。

初学的话可以参考我下面给出的一些命令和相关的作用：

如果你想创建一个新的网页界面，运行：
````ruby
bundle exec jekyll page "new page's name"
````

当然，最主要的还是用这个插件来创建博客，运行：
````ruby
bundle exec jekyll post "new post's name"
# 你也可以在创建空白博客的时候添加时间信息
bundle exec jekyll post "new post's name" --timestamp-format "%Y-%m-%d %H:%M:%S %z"
````
````ruby
# 或者用compose进行创建
bundle exec jekyll compose "name"
# 当然，如果要加入post集合的话还得添加一些东西
bundle exec jekyll compose "name" --post
# 更加完整的话是这样的
bundle exec jekyll compose "name" --collection "posts"
````

除了创建一个新的将投入使用的博客之外，你也可以创建一个需要进一步完善的草稿
````ruby
bundle exec jekyll draft "name"
````
````ruby
# 同样的也可以用compose命令操作
bundle exec jekyll compose "name" --draft
bundle exec jekyll compose "name" --collection "drafts"
````
重命名也是一项重要的功能，它可以让你轻易的改变已经生成了的文件的名字
````ruby
bundle exec jekyll rename ******** "new name"
````
当创建的草稿已经完善到可以发布的时候，你可以通过以下的命令将它展示在你的网页窗口上
````ruby
bundle exec jekyll publish _drafts/name.md
````
````ruby
# 如果你想自定义这篇文章的发布日期，那么也可以
bundle exec jekyll publish _drafts/name.md --date ****-**-**
# 如果还要进一步设置发布这篇文章的时间，那么
bundle exec jekyll publish _drafts/name.md --timestamp-format "%Y-%m-%d %H:%M:%S %z"
````
给已经发布的博客进行改名也是可以的
```ruby
bundle exec jekyll rename _posts/2014-01-24-my-new-draft.md "My New Post"
```

```ruby
# 同时更改时间戳
bundle exec jekyll rename _posts/2014-01-24-my-new-post.md "My Old Post" --date "2012-03-04"
```

```ruby
# 或者改成现在的时间
bundle exec jekyll rename _posts/2012-03-04-my-old-post.md "My New Post" --now
```
如果觉得发布的博客有些问题，也可以将其退回

```ruby
bundle exec jekyll unpublish _posts/2014-01-24-my-new-draft.md
```

Create your new file in a collection using:

```ruby
bundle exec jekyll compose "My New Thing" --collection "things"
```