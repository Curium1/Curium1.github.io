---
layout: post
title:  "Första posten"
date:   2017-11-02 13:26:02 -0500
categories: jekyll update
comments: true
---
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND
     *  UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC
     *  VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT:
     *  https://disqus.com/admin/universalcode/#configuration-variables
     */

    var disqus_config = function () {
      this.page.url = Pcanonical URL variable;
      this.page.identifier = PAGE_IDENTIFIER;
    };

    (function() {
        var d = document, s = d.createElement('script');

         // IMPORTANT: Replace EXAMPLE with your forum shortname!
        s.src = 'https://EXAMPLE.disqus.com/embed.js';

        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

{% if jekyll.environment == 'production' %}
  I'm in production!
{% else %} 
  I'm in development!
{% endif %}

{% if site.disqus.shortname %}
  {{site.disqus.shortname}}
{% endif %}

{% if page.comments != false %}
  Kommentarer på
{% endif %}