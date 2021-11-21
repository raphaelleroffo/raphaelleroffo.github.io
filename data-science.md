---
layout: page
title: Data Science Portfolio
---

&nbsp; 



<div class="posts">
  <ul>
    {% for data-science in site.categories.data-science %}
      <li>
        <a href="">{{data-science.title}}</a>
        <p>{{data-science.description}}</p>
      </li>
    {% endfor %}
  </ul>
  
</div>

<div class="pagination">
  {% if paginator.next_page %}
    <a class="pagination-item older" href="{{ paginator.next_page_path | absolute_url }}">Older</a>
  {% else %}
    <span class="pagination-item older">Older</span>
  {% endif %}
  {% if paginator.previous_page %}
    {% if paginator.page == 2 %}
      <a class="pagination-item newer" href="{{ '/' | absolute_url }}">Newer</a>
    {% else %}
      <a class="pagination-item newer" href="{{ paginator.previous_page_path | absolute_url }}">Newer</a>
    {% endif %}
  {% else %}
    <span class="pagination-item newer">Newer</span>
  {% endif %}
</div>
