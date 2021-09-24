---
layout: post
title:  "Creating Posts"
category: "GitHub Pages and Jekyll"
date:   2021-09-25 01:29:30 +0700
---

## The Posts Folder
The `_posts` folder is where your blog posts live. You typically write posts in Markdown, HTML is also supported.

## Creating Posts

I want to organize my posts under categories, so I create a `GitHub Pages and Jekyll` folder under the `_posts` folder.

Then I add a file to your `GitHub Pages and Jekyll` directory with the following format:

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
title:  "Creating Posts"
category: "GitHub Pages and Jekyll"
date:   2021-09-25 01:29:30 +0700
---
```

Because Jekyll doesn't support category as folder under the `_posts` folder, so I need to add `category` to front matter.
I also use add `date` in front matter because I want to sort my posts in a category.

## Problem
By default, the Jekyll generate the URl like `github%20pages%20and%20jekyll/2021/09/25/creating-posts.html` or `github%20pages%20and%20jekyll/2021/09/25/installation-windows.html`. There are two things need to improve with these URLs.
1. I want to remove the date in the URL: `2021/09/25/`
2. I also want to replace `%20` by `-`: `github-pages-and-jekyll/`

I will show you how to solve these problems in the next post.

## Reference
- [Posts](https://jekyllrb.com/docs/posts/)