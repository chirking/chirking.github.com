---
layout:   default
title:    Notebook 
---

<div class="span-12 last">
  <p class="first">
    文章分类
  </p>
</div>

<div class="span-3">
  <nav id="post-archive-category-list">
    <ul>
      {% for category in site.categories %}<li><a class="cat-{{  (category | first)  | replace:' ','-'}}" href="javascript:filterByCategory('cat-{{ (category | first) | replace:' ','-'}}')">{{ category | first }}</a></li>{% endfor %} 
      <li><a class="reset selected" href="javascript:filterByCategory('reset')">everything &#10033;</a></li> 
    </ul>
  </nav>
</div>

<div class="span-9 last">
  <nav id="post-archive-list">
    <ul>
      {% for post in site.posts %}        
        <li class="{% for category in post.categories %}cat-{{ category| replace:' ','-'}} {% endfor %}"><a class="title" href="{{ post.url }}">{{ post.title }}</a><span class="archive-listing-date">{{ post.date | date: "%d %b, %Y" }}</span></li>
      {% endfor %}
    </ul>
  </nav>
</div>

<script type="text/javascript">
  window.onload=initArchive();
</script>


