---
layout: post
title:  "Creating Posts"
category: "GitHub Pages and Jekyll"
date:   2021-09-23 00:00:00 +0700
---

## The Posts Folder
The `_posts` folder is where your blog posts live. You typically write posts in Markdown, HTML is also supported.

## Creating Posts
To create a post, add a file to your `_posts` directory with the following format:

```
YEAR-MONTH-DAY-title.md
```

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `md` is the file extension representing the format used in the file. For example, the following are examples of valid post filenames:

```
2021-09-25-installation-windows.md
2021-09-25-creating-posts.md
```

All blog post files must begin with front matter which is typically used to set a layout or other meta data. For a simple example this can just be empty:

```yml
---
layout: post
title:  "Welcome to Jekyll!"
---

# Welcome

**Hello world**, this is my first Jekyll blog post.

I hope you like it!
```

## Categories
Categories for a post are defined in the post’s front matter using either the key `category` for a single entry or `categories` for multiple entries.  

All categories registered in the site are exposed to Liquid templates via `site.categories` which can be iterated over.

```liquid
{% raw %}
{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
{% endraw %}
```

Categories for posts can also be defined by a post’s file path. Any directory above `_post` will be read-in as a category. For example, if a post is at path `GitHub Pages and Jekyll/_posts/2021-09-25-creating-posts.md`, then GitHub Pages and Jekyll is automatically registered as categories for that post.

When the post also has front matter defining categories, they just get added to the existing list if not present already.

Categories of a post may be incorporated into the generated URL for the post.

Therefore, depending on whether front matter has `category: GitHub Pages and Jekyll`, or `categories: GitHub Pages and Jekyll`, the example post above would have the URL as either `github%20pages%20and%20jekyll/2021/09/09/welcome-to-jekyll.html` or `github%20pages%20and%20jekyll/github/pages/and/jekyll/2021/09/10/permalinks.html` respectively.

## Custom
But I don't want organize the categories above the `_post`, I want put all the categories under the `_post` folder.
For example, if a post is at path `_posts/GitHub Pages and Jekyll/2021-09-25-creating-posts.md`. But in this case the Jekyll cannot find our posts, so that we need to add the `category: "GitHub Pages and Jekyll"` to the front matter. And we have the URL like `github%20pages%20and%20jekyll/2021/09/25/installation-windows.html`.

## Reference
- [Posts](https://jekyllrb.com/docs/posts/)