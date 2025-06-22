---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

<div class="home">
  <h1 class="page-heading">すべての記事</h1>


  全記事{{ site.posts.size }}件
  <a href="categories">
    カテゴリ別で見る
  </a>
  
  {% include post_list.html title="時系列順" posts=site.posts %}

  {%- if site.posts.size > 0 -%}
    <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
  {%- endif -%}

</div>
