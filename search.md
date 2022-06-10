---
layout: page
title: 搜索
permalink: /search/
---
<br/>&nbsp;
<form action="get" id="site_search">
<center>
  <input style="font-size:20px;" type="text" id="search_box">
  <input style="font-size:20px;" type="submit" value="Go!">
</center>
</form>
<br/>&nbsp;
<br/>&nbsp;

<ul id="search_results"></ul>

<script src="{{ "assets/js/lunr.js"  | prepend: site.baseurl  }}"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<script src="{{ "assets/js/search.js"  | prepend: site.baseurl  }}"></script>
