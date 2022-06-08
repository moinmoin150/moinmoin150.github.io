---
layout: page
permalink: /categories/
title: 分类
---

<div>
  <span class="all-categories">
    <h3 class="all-categories-head">所有分类</h3>
    <br>
  {% capture categories %}
    {% for category in site.categories %}
      {{ category[1].size | plus: 1000 }}#{{ category[0] }}#{{ category[1].size }}@
    {% endfor %}
  {% endcapture %}
  {% assign sortedcategories = categories | split:'@' | sort | reverse %}

  {% for category in sortedcategories %}
    {% assign categoryitems = category | split: '#' %}
    {% if categoryitems[1] != null %}
        <a href="{{site.baseurl}}/categories/#{{ categoryitems[1] | slugize }}"><code class="highligher-rouge"><nobr>
          {{ categoryitems[1] }}
        </nobr></code>&nbsp;</a>
    {% endif %}
  {% endfor %}
    <br>
  </span>
</div>
<hr style="height:2px;border:none;color:#333;background-color:#333;">
<br>
<br>
<div id="archives">
  {% for category in sortedcategories %}
    {% assign categoryitems = category | split: '#' %}
    {% if categoryitems[1] != null %}
      <div class="archive-group">
        <a name="{{ categoryitems[1] | slugize }}"></a>
        <h3 class="category-head">{{ categoryitems[1] }} <span>({{ categoryitems[2] }})</span></h3>
        <div class="category-posts">
        {% capture category_name %}{{ categoryitems[1] | slugize }}{% endcapture %}
        {% assign sortedPosts = site.categories[category_name] | sort: 'title' %}
        <ul>
        {% for post in sortedPosts %}
        <article class="archive-item">
            <li><a href="{{ site.baseurl }}{{ post.url }}">
              {{post.title}}
            </a></li>
        </article>
        {% endfor %}
        </ul>
        <hr class="rounded">
        </div>
      </div>
    {% endif %}
  {% endfor %}
</div>
