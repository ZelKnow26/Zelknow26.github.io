---
layout: post
title: Mac下使用Jekyll + Github Pages搭建博客
author: ZelKnow26
tagline: "拥有自己的博客"
date: 2018.06.04 20:16:12
categories: other
tag: other
---

本文介绍了在Mac OS下使用Github Pages搭建自己个人的博客的方法。

# Mac下使用Jekyll + Github Pages搭建博客

## 0 环境准备
### 需要安装的环境列表

| 环境          | 使用的命令            |
|:-------------|:--------------------|
| git          | brew install git    |
| ruby         | brew install ruby   |
| gem          | gem update          |
| jekyll       | gem install jekyll  |
| bundler      | gem install bundler |

注：若安装过程提示无权限，尝试在命令前加入sudo，在命令后加入-n usr/local/bin，例如

```
sudo gem install -n /usr/local/bin jekyll
```

另外，在国内请替换gem镜像源，使用如下命令查看镜像源：
```
gem sources
```

若显示镜像源为https://rubygems.org/，则必须替换。

```
gem sources --remove https://rubygems.org/
gem sources -a https://gems.ruby-china.org/
```

## 申请Guthub Pages
打开[github](www.github.com)，登陆你的账号，并新建一个repository：

![repository]({{ site.url }}/assets/image/How_to_bulid_a_blog/Snip20180604_1.png)
将这个repository的名字改为USERNAME.github.io，其中USERNAME为你的github账号的用户名。例如我的就是ZelKnow26.github.io

然后你的Github Pages便生成了。

## 选择主题

打开新建立的repository，点击Settings，在Options选项卡中可以看到GitHub Pages选项。

![Github Pages]({{ site.url }}/assets/image/How_to_bulid_a_blog/Snip20180604_2.png)

点击Choose a theme，可以选择自己喜欢的主题。选择好主题后，选择Select theme即可将主题应用到自己的博客中。或者，点击[Jekyll主题网站](http://jekyllthemes.org/)，选择喜欢的主题，并将该主题所有github文件复制到自己的repository中。

## 将博客部署到本地

打开终端，进入某个你想要将博客部署到的文件夹，执行以下指令：

```
git init
git add remote origin https://github.com/USERNAME/USERNAME.github.io
```

其中，USERNAME为你的用户名。

```
git pull origin master
```

然后你的博客便部署至本地了。

## 写文章

jekyll的文章要求使用Markdown语言进行编写。可以通过把写好的文章放入_post文件夹里，便可将文章发布至博客上。但是其中还要执行如下操作：

### 命名

每篇博客必须以如下形式进行命名：

```
YYYY-MM-DD-title.md
```

例如，

```
2018-06-04-How-to-bulid-a-blog.md
```

### 头信息

每篇文章的开头必须加上如下的信息：

```
---
layout: post
title: Mac下使用Jekyll + Github Pages搭建博客
author: ZelKnow26
tagline: "拥有自己的博客"
date: 2018.06.04 20:16:12
categories: other
tag: other
---
```

其中，**layout: post**代表了这是一篇博文，**title**代表标题名，**author**代表作者名，**tagline**代表博文的摘要，**date**代表文章发布时间，**categories**代表文章分类，**tag**代表文章标签，可有多个。

## 个性化博客

可以看到，博客的根目录下有**about.md**，**contace.md**等文件，我们也可以修改它，添加自己想展示的信息，个性化我们的博客。

## 本地服务器上进行预览

当我们修改好相关信息后，想要先在本地预览我们的博客，可以执行以下指令：

```
bundle exec jekyll serve
```

然后其会输出如下信息：

```
Configuration file: /Users/username/Blog/_config.yml
            Source: /Users/username/Blog
       Destination: /Users/username/Blog/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 1.205 seconds.
 Auto-regeneration: enabled for '/Users/username/Blog'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

那么 http://127.0.0.1:4000 便是我们本地服务器地址，复制到浏览器中便可进行预览。

## 发布

将本地的修改push到github上便可完成发布。具体操作如下：

```
git push origin master
```

然后进入 `http://github.com/username/username.github.io` （username为你的github用户名）便可查看你的博客啦！
