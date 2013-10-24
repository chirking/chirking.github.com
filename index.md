---
layout:   default
--- 

<div id="latest-notes" class="span-8">  
  {% for post in site.posts limit:10 %}
    {% include post_excerpt.html %}    
  {% endfor %}
  <p>
    For older posts, have a look in the <a href="/notebook.html">notebook</a>.
  </p>
</div>

</div>