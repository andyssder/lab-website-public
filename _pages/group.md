---
layout: default
permalink: /group/
title: Group
nav: true
nav_order: 3
---

<style>
  .row {
    display: flex;
    flex-wrap: wrap;
  }

  /* 卡片基础样式 */
  .card.member-card {
    transition: all 0.3s ease;
    border-radius: 8px;
    overflow: hidden;
    min-height: 170px; 
    border: 1px solid rgba(0,0,0,.08);
    background-color: var(--global-card-bg);
  }

  .card.member-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1) !important;
  }

  /* 极致压缩文字间距 */
  .member-info-text p {
    margin-bottom: 1px !important;
    font-size: 0.78rem;
    line-height: 1.2;
    white-space: normal;
    color: var(--global-text-color);
  }

  /* 名字样式 */
  .member-info-text p strong:first-child {
    font-size: 0.9rem;
    display: inline-block;
    margin-bottom: 2px;
    color: var(--global-theme-color);
  }

  .email-text {
    font-size: 0.72rem;
    margin-top: 3px !important;
    margin-bottom: 0 !important;
  }

  .member-info-text p:last-child {
    margin-bottom: 0 !important;
  }

  /* --- Alumni 表格表头美化 --- */
  .custom-thead {
    /* 这里可以修改为你喜欢的颜色：比如 #343a40 (深灰), #003366 (深蓝), 或 var(--global-theme-color) */
    background-color: var(--global-theme-color) !important; 
  }
  
  .custom-thead th {
    color: #ffffff !important; /* 表头文字设为白色 */
    font-weight: 500;
    border: none !important;
    padding: 12px 15px !important;
  }

  .table {
    border-radius: 8px;
    overflow: hidden;
    border-collapse: separate;
    border-spacing: 0;
    border: 1px solid #eee;
  }

  h2 {
    margin-top: 1.5rem;
    margin-bottom: 1rem;
    font-size: 1.5rem;
  }

  hr {
    margin: 2rem 0;
  }
</style>

{% assign all_members = site.group %}

## Principal Investigator
<div class="row">
{% assign pis = all_members | where_exp: "item", "item.path contains 'pi/'" | where: "role", "pi" | where: "status", "active" %}
{% for member in pis %}
  {% include group/member_card.html member=member %}
{% endfor %}
</div>

<hr>

## PhD Students
<div class="row">
{% assign phds = all_members | where_exp: "item", "item.path contains 'phd/'" | where: "role", "phd" | where: "status", "active" %}
{% for member in phds %}
  {% include group/member_card.html member=member %}
{% endfor %}
</div>

## Master Students
<div class="row">
{% assign masters = all_members | where_exp: "item", "item.path contains 'master/'" | where: "role", "master" | where: "status", "active" %}
{% for member in masters %}
  {% include group/member_card.html member=member %}
{% endfor %}
</div>

## Undergraduate Students
<div class="row">
{% assign undergrads = all_members | where_exp: "item", "item.path contains 'undergraduate/'" | where: "role", "undergraduate" | where: "status", "active" %}
{% for member in undergrads %}
  {% include group/member_card.html member=member %}
{% endfor %}
</div>

<hr>

## Alumni
<div class="table-responsive">
    <table class="table table-hover mt-2">
      <thead class="custom-thead">
        <tr>
          <th>Name</th>
          <th>Role in group</th>
          <th>Current position</th>
        </tr>
      </thead>
      <tbody>
        {% assign alumni = all_members | where_exp: "item", "item.path contains 'alumni/'" | where: "role", "alumni" | where: "status", "active" %}
        {% for member in alumni %}
        <tr>
          <td><strong>{{ member.name }}</strong></td>
          <td>{{ member.role_in_group }}</td>
          <td>{{ member.current_position }}</td>
        </tr>
        {% endfor %}
      </tbody>
    </table>
</div>