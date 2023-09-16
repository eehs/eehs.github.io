---
layout: home
---

<ul class="posts-list">
  {% for post in site.posts %}
    <li>
      <a id="post-link" href="{{ post.url }}">{{ post.date | date: "%F" }} 
        <div style="display: inline-block">{{ post.title }}</div>
     </a>
    </li>
  {% endfor %}
</ul>
