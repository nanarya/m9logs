---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---


<div class="home">
  <h1 class="page-heading">HOME</h1>

  のんびり更新中

  {% include post_list.html title="最近の記事" posts=site.posts limit=10 %}

  <a href="all_posts">
    全件見る
  </a>
  {%- if site.posts.size > 0 -%}
    <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
  {%- endif -%}

</div>
