---
layout: page
title: "Posts"
tagline: test tagline
---
{% include JB/setup %}

<div class="posts">
  {% for post in site.posts limit:5 %}
    <div class="post">
      <div class="title"><a href="{{ post.url }}">{{post.title }}</a></div>
      <div class="date">Posted on {{ post.date | date: "%B %d %Y" }}</div>
      <div class="excerpt">{{ post.content | split:'<!--more-->'| first }}</div>
      <p><a href="{{post.url}}">Read more »</a></p>
    </div>
    <hr />
  {% endfor %}
</div>
