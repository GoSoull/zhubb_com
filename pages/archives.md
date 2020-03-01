---
layout: page
title: 归档
permalink: /archives/
---

<div class="post">
  <div class="post-archive">
  {% for post in site.posts  %}
      {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
      {% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}

      {% if forloop.first %}
        <h2>{{this_year}}</h2>
        <ul>
      {% endif %}

      <li><span class="date">{{ post.date | date: "%m月%d日" }}</span><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></li>

      {% if forloop.last %}
        </ul>
      {% else %}
        {% if this_year != next_year %}
          </ul>
          <h2>{{next_year}}</h2>
          <ul>
        {% else %}    
          {% if this_month != next_month %}
            </ul>
            <ul>
          {% endif %}
        {% endif %}
      {% endif %}
  {% endfor %}
  </div>
</div>
