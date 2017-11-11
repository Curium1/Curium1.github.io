---
layout: post
title:  "Disqus comments and Open Graph"
date:   2017-11-10 22:16:00 -0500
categories: Disqus Open-Graph
excerpt: "Read about how I implemented Disqus comments and Open Graph on this site."
permalink: /Disqus-Open-Graph/
---
# How I implemented Disqus comments and Open Graph

Disqus Comments and Open Graph is built in to the minima theme. The only thing one need to do to activate it is to add som code to the _config.yml file.

For Disqus it is the the following code that needs to be added:

```yaml
  disqus:
    shortname: my_disqus_shortname (in my case it is 1DV022)
```

For Open Graph it is the following code that needs to be added:

```yaml
  google_analytics: UA-NNNNNNNN-N
```