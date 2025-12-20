---
layout:  default
permalink: /group/
title: Group
nav: true
nav_order: 3

---

## Principal Investigator
{% assign pis = site.group | where_exp: "item", "item.path contains 'pi/' and item.role == 'pi' and item.status == 'active'" %}
{% for member in pis %}
  {% include group/member_card.html member=member %}
{% endfor %}

 
## PhD Students
{% assign phds = site.group | where_exp: "item", "item.path contains 'phd/' and item.role == 'phd' and item.status == 'active'" %}
{% for member in phds %}
  {% include group/member_card.html member=member %}
{% endfor %}

## Master Students
{% assign masters = site.group | where_exp: "item", "item.path contains 'master/' and item.role == 'master' and item.status == 'active'" %}
{% for member in masters %}
  {% include group/member_card.html member=member %}
{% endfor %}

## Undergraduate Students
{% assign undergrads = site.group | where_exp: "item", "item.path contains 'undergraduate/' and item.role == 'undergraduate' and item.status == 'active'" %}
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
        {% assign alumni = site.group | where_exp: "item", "item.path contains 'alumni/' and item.role == 'alumni' and item.status == 'active'" %}
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