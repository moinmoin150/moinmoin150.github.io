---
layout: page
permalink: /categories/
title: 分类
---

<div>
  <span class="all-categories">
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
    <br>
    <br>
  </span>
</div>

<div id="archives">
  {% for category in sortedcategories %}
    {% assign categoryitems = category | split: '#' %}
    {% if categoryitems[1] != null %}
      <div class="archive-group">
        <a name="{{ categoryitems[1] | slugize }}"></a>
        <h3 class="category-head">{{ categoryitems[1] }} <span>({{ categoryitems[2] }})</span></h3>
        <div class="category-posts">
        {% capture category_name %}{{ categoryitems[1] | slugize }}{% endcapture %}
        {% for post in site.categories[category_name] %}
        <article class="archive-item">
          <h4>
            <a href="{{ site.baseurl }}{{ post.url }}">
              {{post.title}}
            </a>
          </h4>
        </article>
        {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
</div>
