---
layout: page
title: Archive
subtitle: All posts by date
permalink: /en/archive/
---

{% assign lang_posts = site.posts | where: "lang", "en" %}
{% assign posts_by_year = lang_posts | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year_group in posts_by_year %}
<div class="archive-year">
  <h2 class="archive-year-title">{{ year_group.name }}</h2>
  <ul class="archive-list">
    {% for post in year_group.items %}
    <li class="archive-item">
      <span class="archive-date">{{ post.date | date: "%m/%d" }}</span>
      <span class="archive-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </span>
    </li>
    {% endfor %}
  </ul>
</div>
{% endfor %}
