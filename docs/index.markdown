---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
---

<ul>
  {% for category in site.categories %}
    <h3>{{ category[0] }}</h3>
    <ul>
      {% assign sorted = category[1] | sort: 'date' %}
      {% for post in sorted %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>
  {% endfor %}
</ul>