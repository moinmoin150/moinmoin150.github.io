---
layout: page
title: 搜索
permalink: /search/
---

<form action={{ "/search.html" | prepend: site.baseurl }} method="get">
  <label for="search-box">Search</label>
  <input type="text" id="search-box" name="query">
  <input type="submit" value="search">
</form>
