---
layout: default
permalink: /group/
title: Group
nav: true
nav_order: 3
---

{%- comment -%} 获取初始集合 {%- endcomment -%}
{% assign all_members = site.group %}

## Principal Investigator
{%- comment -%} 多级过滤：先滤路径，再滤角色，最后滤状态 {%- endcomment -%}
{% assign pis = all_members | where_exp: "item", "item.path contains 'pi/'" %}
{% assign pis = pis | where: "role", "pi" | where: "status", "active" %}
{% for member in pis %}
  {% include group/member_card.html member=member %}
{% endfor %}

## PhD Students
{% assign phds = all_members | where_exp: "item", "item.path contains 'phd/'" %}
{% assign phds = phds | where: "role", "phd" | where: "status", "active" %}
{% for member in phds %}
  {% include group/member_card.html member=member %}
{% endfor %}

## Master Students
{% assign masters = all_members | where_exp: "item", "item.path contains 'master/'" %}
{% assign masters = masters | where: "role", "master" | where: "status", "active" %}
{% for member in masters %}
  {% include group/member_card.html member=member %}
{% endfor %}

## Undergraduate Students
{% assign undergrads = all_members | where_exp: "item", "item.path contains 'undergraduate/'" %}
{% assign undergrads = undergrads | where: "role", "undergraduate" | where: "status", "active" %}
{% for member in undergrads %}
  {% include group/member_card.html member=member %}
{% endfor %}

## Alumni
<div class="table-responsive">
    <table class="table table-hover">
      <thead>
        <tr>
          <th>Name</th>
          <th>Role in group</th>
          <th>Current position</th>
        </tr>
      </thead>
      <tbody>
        {% assign alumni = all_members | where_exp: "item", "item.path contains 'alumni/'" %}
        {% assign alumni = alumni | where: "role", "alumni" | where: "status", "active" %}
        {% for member in alumni %}
        <tr>
          <td>{{ member.name }}</td>
          <td>{{ member.role_in_group }}</td>
          <td>{{ member.current_position }}</td>
        </tr>
        {% endfor %}
      </tbody>
    </table>
</div>