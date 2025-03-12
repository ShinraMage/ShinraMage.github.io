---
layout: page
---



{% assign podcast_pages = site.pages | where_exp: "item", "item.url contains '/Podcast/'" %}
{% assign sorted_podcast_pages = podcast_pages | sort: 'url' | reverse %}
<ul id="podcast-list">
  {% for subtitle in sorted_podcast_pages %}
      <li><a href="{{ subtitle.url }}" data-title="{{ subtitle.url }}"></a></li>
  {% endfor %}
</ul>



<script>
  document.addEventListener('DOMContentLoaded', (event) => {
    document.querySelectorAll('#podcast-list a').forEach((element) => {
      element.innerHTML = decodeURIComponent(element.getAttribute('data-title'));
      element.href = decodeURIComponent(element.href);
    });
  });
</script>