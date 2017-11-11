---
layout: post
title:  "Disqus comments and Open Graph"
date:   2017-11-10 22:16:00 -0500
categories: Disqus Open-Graph
excerpt: "Read about how I implemented Disqus comments and Open Graph on this site."
permalink: /Disqus-Open-Graph/
---
# How I implemented Disqus comments and Open Graph

Disqus Comments is built in to the minima theme. The only thing one need to do to activate it is to add som code to the _config.yml file.

```yaml
  disqus:
    shortname: my_disqus_shortname (in my case it is 1DV022)
```

For Open Graph it is a little bit more work.
The tags needs to be in the meta data of the website which is stored in the "./_includes/head" folder. I have chosen to use four tags: Title, Type, Image & URL. I have also chosen to try out different methods for applying them.

## Title

I have chosen to use an if tag for this tag (og:title). If the blog post contain a front matter title that will be used otherwise the site title will be used as standard (site.title).

## Type

For this tag (og:type) I have chosen to hardcode the type "Blog"

## Image

For the image tag ia have chosen a combination between a static path and a conditional one. If another image than the logo should be used then it needs to be put into the "./images/" folder. I have chosen to put an image tag as front matter and i have set the default value for all files as "logo.png" in the _config.yml. This means that if nothing else is specified it will use the logo.png that is found in the images folder of the website. But this can be overwritten bu adding an image front matter.

## URL

Here i have chosen to default to site.url combined with page.permalink. which could be a little dangerous but that made it possible to use four different techniques in order to create the tags. But since all my pages has a permalink the Open Graph will always point to the right address.
