---
layout: default
title: Home
permalink: /
---

{% assign home_data = site.home | first %}

{% if home_data %}
  {% include home/home.html data=home_data %}
{% endif %}