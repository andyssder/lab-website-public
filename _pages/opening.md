---
layout: default
title: Openings
permalink: /opeings/
nav: true
nav_order: 7
---
{% assign opening_data = site.opening | first %}

{% if opening_data %}
  {% include opening/opening.html entry=opening_data %}
{% else %}
  <p>Coming soon...</p>
{% endif %}
