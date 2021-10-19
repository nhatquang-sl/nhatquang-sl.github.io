---
layout: post
title:  "Link to Next/Previous post in a category"
category: "GitHub Pages and Jekyll"
date:   2021-09-26 00:00:00 +0700
---

When in a post, we usually need to go next/back to another post. So it would be great if our post has links to next/previous post.

## Get the Next/Previous post link
Use the following code to get the next/previous post link then assign to `next_post`/`prev_post`.
```liquid
{% raw %}
    {% assign cat = page.category %}
    {% for post in site.categories[cat] %}
        {% if post.url == page.url %}
            {% assign post_index0 = forloop.index0 %}
            {% assign post_index1 = forloop.index %}
        {% endif %}
    {% endfor %}
    {% for post in site.categories[cat] %}
        {% if post_index0 == forloop.index %}
            {% assign next_post = post %}
        {% endif %}
        {% if post_index1 == forloop.index0 %}
            {% assign prev_post = post %}
        {% endif %}
    {% endfor %}
{% endraw %}
```

## Display the Next/Previous post link
Use the following code to display the next/previous post.
```liquid
{% raw %}
    {% if prev_post %}
        <div class="article-previous">
            <a href="{{ prev_post.url }}">
                <span class="iconify-inline" data-icon="akar-icons:arrow-left"></span>
                &nbsp;&nbsp;&nbsp;&nbsp;{{ prev_post.title }}</a>
        </div>
    {% endif %}
    {% if next_post %}
        <div class="article-next">
            <a href="{{ next_post.url }}">
                {{ next_post.title }}&nbsp;&nbsp;&nbsp;&nbsp;
                <span class="iconify-inline" data-icon="akar-icons:arrow-right"></span>
            </a>
        </div>
    {% endif %}
{% endraw %}
```

## Add links to Post layout
Now I want to add the next/previous post link to the Post layout so that these links will display as default for all posts. So that we will override the Post layout.

1. Create a `_layouts` folder under `docs` folder.

1. Get the theme path, run `bundle info --path` followed by the name of the theme’s gem, e.g., `bundle info --path minima` for Jekyll’s default theme.

2. Browse to the theme path, you will see the following structure folders.
```
.
├── LICENSE.txt
├── README.md
├── _includes
│   ├── disqus_comments.html
│   ├── footer.html
│   ├── google-analytics.html
│   ├── head.html
│   ├── header.html
│   ├── icon-github.html
│   ├── icon-github.svg
│   ├── icon-twitter.html
│   └── icon-twitter.svg
├── _layouts
│   ├── default.html
│   ├── home.html
│   ├── page.html
│   └── post.html
├── _sass
│   ├── minima
│   │   ├── _base.scss
│   │   ├── _layout.scss
│   │   └── _syntax-highlighting.scss
│   └── minima.scss
└── assets
    └── main.scss
```
4. Copy the `post.html` to our `_layouts` folder.

5. Update the `post.html` file to display next/previous post link as the following:

```liquid
---
layout: default
---
{% raw %}
{% assign cat = page.category %}
{% for post in site.categories[cat] %}
    {% if post.url == page.url %}
        {% assign post_index0 = forloop.index0 %}
        {% assign post_index1 = forloop.index %}
    {% endif %}
{% endfor %}
{% for post in site.categories[cat] %}
    {% if post_index0 == forloop.index %}
        {% assign
next_post = post %}
    {% endif %}
    {% if post_index1 == forloop.index0 %}
        {% assign prev_post = post %}
    {% endif %}
{% endfor %}
{% endraw %}

<article class="post h-entry" itemscope itemtype="http://schema.org/BlogPosting">
    <header class="post-header">
        <h1 class="post-title p-name" itemprop="name headline">{% raw %}{{ page.title | escape }}{% endraw %}</h1>
    </header>

    {% raw %}
    {% if prev_post %}
        <div class="article-previous">
            <a href="{{ prev_post.url }}">
                <span class="iconify-inline" data-icon="akar-icons:arrow-left"></span>
                &nbsp;&nbsp;&nbsp;&nbsp;{{ prev_post.title }}</a>
        </div>
    {% endif %}
    {% if next_post %}
        <div class="article-next">
            <a href="{{ next_post.url }}">
                {{ next_post.title }}&nbsp;&nbsp;&nbsp;&nbsp;
                <span class="iconify-inline" data-icon="akar-icons:arrow-right"></span>
            </a>
        </div>
    {% endif %}
    {% endraw %}
    <div class="post-content e-content" itemprop="articleBody">{% raw %}{{ content }}{% endraw %}</div>

    {% raw %}
    {%- if site.disqus.shortname -%}
        {%- include disqus_comments.html -%}
    {%- endif -%}
    {% endraw %}
    <a class="u-url" href="{% raw %}{{ page.url | relative_url }}{% endraw %}"></a>
</article>

{% raw %}
{% if prev_post %}
    <div class="article-previous">
        <a href="{{ prev_post.url }}">
            <span class="iconify-inline" data-icon="akar-icons:arrow-left"></span>
            &nbsp;&nbsp;&nbsp;&nbsp;{{ prev_post.title }}</a>
    </div>
{% endif %}
{% if next_post %}
    <div class="article-next">
        <a href="{{ next_post.url }}">
            {{ next_post.title }}&nbsp;&nbsp;&nbsp;&nbsp;
            <span class="iconify-inline" data-icon="akar-icons:arrow-right"></span>
        </a>
    </div>
{% endif %}
{% endraw %}
```

## Add style for next/previous post link
1. Create a `_sass` folder under `docs` folder.

2. Create a `_pager.scss` file under `_sass` folder with the following code:
```css
.article-previous,
.article-next {
  display: inline;
  a {
    text-decoration: none;
  }
}

.article-next {
  float: right;
}

```
3. Create `css` folder under `assets` folder.

4. Create `styles.scss` file under `css` folder with the following code:
```css
---
---

@import "pager";
```

5. Add the following code at the end of `_config.yml` file:
```YAML
sass:
  sass_dir: _sass
```

6. Add the following code to `default.html` file:
```HTML
<link rel="stylesheet" type="text/css" href="{{site.baseurl}}/assets/css/styles.css"/>
```

7. Finally we will get the result.  
![shot_211018_225404](../../assets/img/github-pages-and-jekyll/shot_211018_225404.png)

## Reference
- [Overriding theme defaults](https://jekyllrb.com/docs/themes/#overriding-theme-defaults)