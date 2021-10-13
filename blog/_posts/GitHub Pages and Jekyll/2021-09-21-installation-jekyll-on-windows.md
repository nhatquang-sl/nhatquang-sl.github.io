---
layout: post
title:  "Installation Jekyll on Windows"
category: "GitHub Pages and Jekyll"
date:   2021-09-21 00:00:00 +0700
---

## About Jekyll
Jekyll is a static site generator with built-in support for GitHub Pages and a simplified build process. Jekyll takes Markdown and HTML files and creates a complete static website based on your choice of layouts. Jekyll supports Markdown and Liquid, a templating language that loads dynamic content on your site.

## Install Requirements
1. Use `Chocolatey` to install `ruby` and `msys2`
```
choco install ruby
choco install msys2
```
2. Open a new command prompt window from the start menu, so that changes to the `PATH` environment variable becomes effective. 
3. Check your Ruby version using `ruby -v`. Ruby version **3.0** or higher.
4. Check you Gems version using `gem -v`
5. Install Jekyll and Bundler using `gem install jekyll bundler`
6. Check if Jekyll has been installed properly `jekyll -v`

## Reference
- [Jekyll on Windows](https://jekyllrb.com/docs/installation/windows/)
- [Quickstart](https://jekyllrb.com/docs/)
