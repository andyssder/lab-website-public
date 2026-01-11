---
layout: default
title: News
permalink: /news/
nav: true
nav_order: 5
---

{%- comment -%} 提取所有新闻并按日期倒序 {%- endcomment -%}
{% assign all_news = site.news | sort: 'date' | reverse %}

{%- comment -%} 调用模板 {%- endcomment -%}
{% if all_news.size > 0 %}
  {% include news/news_list.html datasource=all_news %}
{% else %}
  <p>Coming soon...</p>
{% endif %}
