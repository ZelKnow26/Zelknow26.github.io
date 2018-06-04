---
layout: page
title: Guide
tagline: 导航
permalink: /guide.html
---

# 文章汇总

## 编程学习

<ul>
  {% for post in site.categories.learn %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

## 杂谈

<ul>
  {% for post in site.categories.other %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

[回到首页]({{ site.url }}{{ site.baseurl }})