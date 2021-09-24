---
layout: post
title:  "Installation on Windows"
category: "GitHub Pages and Jekyll"
---

## Install Requirements

1. Use `Chocolatey` to install `ruby` and `msys2`
```
choco install ruby
choco install msys2
```
2. Open a new command prompt window from the start menu, so that changes to the `PATH` environment variable becomes effective. 
3. Check your Ruby version using `ruby -v`. Ruby version **3.0** or higher.
4. Check you Gems version using `gem -v`

## Instructions
1. Create a new Jekyll site at `./blog`.
```
jekyll new blog
```
2. Change into your new directory.
```
cd blog
```
3. Open the `Gemfile`, then add the following code to the end of the file.
```
gem "webrick", "~> 1.7"
```
4. Install the jekyll and bundler *gems*.
```
gem install jekyll bundler
```
5. Build the site and make it available on a local server.
```
bundle exec jekyll serve
```
6. Browse to http://localhost:4000



