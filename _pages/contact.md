---
layout: default
permalink: /contact/
title: Contact
nav: true
nav_order: 7
---

{% assign contact_data = site.contact | first %}

{% if contact_data %}
  {% include contact/contact.html info=contact_data %}
{% endif %}
