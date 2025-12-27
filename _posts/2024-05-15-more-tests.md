---
layout: post
title:  "More tests!"
date:   2024-05-15 12:46:46 +0200
categories: [blog]
tags: [jekyll, instruction, workflow]
author : Loopy
excerpt : "Here is a brief workflow for setting up Jekyll"
math: true
mermaid: true
featured_image : ./assets/img/tilt-cuba3.jpg
image:
  path : ./assets/img/tilt-cuba3.jpg
  alt : Miniature Havana Cafe
excerpt_separator: <!--more-->
published: false
---
# How to do things in order

## 1. Installation :
Let's bebing with a bit of an except that will telling us bascially waht this post is about : Jekyll Workflow.
<!--more-->

1. Ruby
    - install `sudo apt-get install ruby-full build-essential`
    - check version : `Ruby -v`
2. Install Jekyll : run `gem install jekyll bundler`
3. run `jekyll new blogname`
4. go into the directory where you created teh site
`cd blogname`
2. ` bundle exec jekyll serve`
and hten can just type `jekyll serve` after teh first time

## 2. Inforamtion about the files in the jekyll site foldres/stuff :
- the **_site folder_** : stuff related to the blog. this holds the finished final website (that you put on a web server). dotn modify too much in here, it gets modified by itself
- the **_post folder_** : your markdown posts
- the **_yaml config_** file : important values for the site
- the **_gem_** file : stores dependencies, for example the `theme`.

## 3. Front Matter :

```yaml!
layout : post
title : "Post Title "
date : 20240-04-04 15:34:30 -0200
categories : jekyll update (the category it gets updates, so changes teh folder it's saved in)
```
can create own categories like `author`, etc
some other elements :
- permalink : "/new-url" or permalink:/categories or
good idea to define a permalink for each post so that they dont break in case you change a date or somethign later on.

```yaml
layout: post
permalink: /blog/my-first-post/
slug: index.html
title: My first blog post
date: 2020-01-31 07:30 +0000
last_modified_at: 2024-01-16 12:01 +0800
category: [category1, category2]
tags: [tag1, tag2, tag3]
excerpt: This is the first blog post for my Jekyll site.
```

```yaml
Attribute	Description
layout:	The Jekyll layout file to use.
Options: page, post, archive, category-list and tag-list.
Note: page-right-sidebar and post-left-sidebar are deprecated.
title:	The title of the page or post.
date: The date here overrides the date from the name of the post file. *Note: A date is specified in the format YYYY-MM-DD HH:MM:SS +/-TTTT; hours, minutes, seconds, and timezone offset are optional.*
last_modified_at:	(Optional) The date when the post was the last modified: *Note: A date is specified in the format YYYY-MM-DD HH:MM:SS +/-TTTT; hours, minutes, seconds, and timezone offset are optional*.
permalink:	(Optional) The custom URL for the page or post, if you need your processed blog post URLs to be something other than the site-wide style. Default: /year/month/day/title.html.
slug:	(Optional) The custom name for the page or post file, if you need your processed blog post file names to be something other than the original name. Default: The original file name. "Note: If the permalink option is set to a string that ends with /, you need to set the slug option to " " or index.html to avoid generating an invalid URL for the site preview feature of Front Matter CMS."
category:	(Optional) One or multiple categories that the post belongs to.
tags:	(Optional) One or multiple tags that the post associates with.
excerpt:	(Optional) The short text to show on the card of the list/grid of posts, and use as the meta description of the page or post.
```

## 4. Building a default Front Matter through `yaml config` file under `#build settings` :

`defaults:
 -
    scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
`

:::info
**Note that** :

- if you dont specify layout in a post/page, it'll go to THIS default. but if you type a default layout manually into a front matter it'll supercede the default.
-
:::    

## 5.  Themes :

1. (rubygems.org to get the theme name)
2.  go into the `Gemfile`
3.  in teh `Gemfile` go to the `theme` section and below the deafult (minima) add : `gem "theme-name (wahtever the name is)"`
4.  go into terminal : `bundle install` inorder to install all teh gems, including new one
5. restart jekyll server `bundle exec jekyll serve`
6. the new theme might not have teh same layout elements as before, which woudl break things. so have to check the new theme's "defaults" document/file.

## 6. Hosting on GitHub :
1. create new repository, public and DONT `initialize with README`
2. modification of `yaml` config file : `baseurl` which is the urlof the site/file so here on github pages it'd be `rep_name` otherwise the url of the page on custom domain name
3. go into Git :
```bash!
git checkout -b gh-pages #switches to github pages branch
git add . #prepares all teh filres to be added to the repo
git commit -m "initial commit " #commits this files to teh repo with teh title
git remote add origin https://github ... /blogname.git #to keep connected to the local
git push origin gh-pages #to push to the GH repo

#each time there is a change to commit
git commit -m "commit message"
git push origin gh-pages
```
the link for the blog then becomes `zloopy.github.io/blogname`
