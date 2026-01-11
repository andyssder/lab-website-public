---
layout: default
permalink: /publications/
title: Publications
nav: true
nav_order: 4
---


{%- comment -%} 1. 提取三类数据 {%- endcomment -%}
{% assign cover_data = site.publication | where_exp: "item", "item.path contains 'cover/' and item.type == 'cover'" | sort: 'order' %}
{% assign typical_data = site.publication | where_exp: "item", "item.path contains 'typical/' and item.type == 'typical'" | sort: 'date' | reverse %}
{% assign recent_data = site.publication | where_exp: "item", "item.path contains 'recent/' and item.type == 'recent'" | sort: 'date' | reverse %}


{%- comment -%} 2. 分别调用模板，并将数据通过参数传入 {%- endcomment -%}

{% include publication/pub_cover.html datasource=cover_data %}

<hr>

{% include publication/pub_typical.html datasource=typical_data %}

<hr>

{% include publication/pub_recent.html datasource=recent_data %}

