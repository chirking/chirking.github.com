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

<div id="working-on" class="span-4 last">
  <p class="second">我的标签</p>  
  <!--[if lt IE 7]>      
  <p>
  Unfortunately, IE 6 is not capable of displaying these images without completely borking the page formatting, so they have been removed.
  </p>
  <p>
  You can go to <a href="http://dribbble.com/dlimiter">Dribble.com</a> to see them full size, or you can download a modern standards compliant browser like <a href="http://www.google.com/chrome">Chrome</a>, <a href="http://www.mozilla.com/en-US/firefox/">Firefox</a> or <a href="http://www.apple.com/safari/download/">Safari</a>.
  <![endif]-->    
  <div id="mydribbble">
    <ul class="tag_box inline">
      {% assign tags_list = site.tags %}  
      {% include tags_list %}
    </ul>


    <!--{% for tag in site.tags %} 
      <h2 id="{{ tag[0] }}-ref">{{ tag[0] }}</h2>
      <ul>
        {% assign pages_list = tag[1] %}  
        {% include JB/pages_list %}
      </ul>
    {% endfor %}-->
  </div>

  <br>
  <div>
    <p class="second">近期文章</p>
    <div id="mydribbble">
      <ul class="tag_box inline">
        {% for post in site.posts limit:10 %}
          <li><a href="{{ post.url }}">{{ post.title }}</a></li>    
        {% endfor %}
      </ul>
    </div>
  </div>
</div>