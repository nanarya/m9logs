---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

<div class="home">
  <h1 class="page-heading">カテゴリ別</h1>

  <a href="all_posts">
    時系列順ですべての記事を見る
  </a>
  
  {% for category in site.categories %}

    {%- if category[1].size > 0 -%}
        <h2 class="post-list-heading">{{ category[0] }}</h2>
      <ul class="post-list">
        {%- for post in category[1] -%}
        <li>
          {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
          <span class="post-meta">{{ post.date | date: date_format }}</span>
          <h3>
            <a class="post-link" href="{{ post.url | relative_url }}">
              {{ post.title | escape }}
            </a>
          </h3>
          {%- if site.show_excerpts -%}
            {{ post.excerpt }}
          {%- endif -%}
        </li>
        {%- endfor -%}
      </ul>
    {%- endif -%}

  {% endfor %}

</div>
