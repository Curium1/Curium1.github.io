---
layout: post
title:  "My thoughts about Pre-compiling"
date:   2017-11-10 21:16:00 -0500
categories: Jekyll SASS Pre-compilers
excerpt: "Read about the different techniques i used to build these posts."
permalinks: /initial-thoughts/
---
# My thoughts about precompiling CSS

## CSS or a pre-compiler like SASS

Using SASS rather than ordinary CSS basically means that you have more options. If you want you could ignore the pre-compilers additional functions and just write the CSS like you normally would in the .css file. But that doesn’t make much sense does it?
The ability to write the css using variables are in my opinion enough to make me want to use a pre-compiler. This is however in the works for ordinary CSS but until it is widely supported for clients it is still better to use these pre-compilers. 

Advantages of using pre-compilers

- Easy to organize
  - using Pre-compilers makes it posstible to separate the CSS files into smaller parts creating structure.
- No Databse connections requiered
  - this creates a safe website as well as a fast one.
- Possible to use markdown files
  - This makes it easy to edit and there is a smaller chance to mess up the final HTML output.

But there are some things to be aware of before deciding to use a pre-compiler or not.

- Harder to degbug the code
  - this is due to that the line numbers of the generated code will not match the line numbers of the pre-compiler code.
- Potenitally huge CSS files
  - Since your not the one writhing the final CSS file it could be hard to determine the size of the file and it is that file that the client will use. A large file means more work for the client.

## What techniques is used in this site?

Variables & color operators
As I mentioned above it is possible to use variables in SASS. They always begin with a “$” and the “:”  assigns the variable the property that follows. After defining a variable it is then possible to use it by writing the name instead of rewriting the value that a property holds.
I have only added a few of these from the original code and it looks like this:

{% highlight ruby %}
$grey-color-lighter: lighten($grey-color, 45%) !default;

.postCategories {
  font-weight: bolder;
  background-color: $grey-color-lighter;
  padding-left: 10px;
}

{% endhighlight %}

This specifies that the background color of the class “postCategories” will be a lighter version of the variable $grey-color by 45%. The ability to specify a % instead of defining the color it what color operators is all about.

## Nesting

Nesting is a great way of arranging the CSS selectors into top level categories. For example in the following example I nest all properties and their corresponding value for a elements without having to rewrite the selector for each new combination of selectors by using the curly brackets for each level of nesting. 

{% highlight ruby %}
a {
  color: $brand-color;
  text-decoration: none;

  &:visited {
    color: darken($brand-color, 15%);
  }

  &:hover {
    color: darken($brand-color, 15%);
    text-decoration: underline;
  }

  .social-media-list &:hover {
    text-decoration: none;

    .username {
      text-decoration: underline;
    }
  }
}
{% endhighlight %}

## If/else statements

I have only used these techniques during the test phase in order to check variables that were needed in order to get Disqus and Open Graph up and running.

{% highlight ruby %}
{% if jekyll.environment == 'production' %}
  I'm in production!
{% else %} 
  I'm in development!
{% endif %}
{% endhighlight %}

This test if the Jekyll.enviroment is set to production and if it is it prints out “I'm in production!” on the webpage.

## Extends

Is a way of defining a base code and then resuing that same code as a base and then defining some new properties that add to that existing code. In the example below the wrapper will add the properties in the clearfix to itself. Changes made to the clearfix fill then affect the wrapper.

{% highlight ruby %}
.wrapper {
  max-width: -webkit-calc(#{$content-width} - (#{$spacing-unit} * 2));
  max-width:         calc(#{$content-width} - (#{$spacing-unit} * 2));
  margin-right: auto;
  margin-left: auto;
  padding-right: $spacing-unit;
  padding-left: $spacing-unit;
  @extend %clearfix;
}

%clearfix:after {
  content: "";
  display: table;
  clear: both;
}
{% endhighlight %}

##Mixins

There are only two small mixins in this project by default and I have not added any extras. A mixin is comparable to a function I JavaScript. You can choose to include arguments but you can also hard code all properties and use the mixin as a way to format markup.

{% highlight ruby %}
@mixin relative-font-size($ratio) {
  font-size: $base-font-size * $ratio;
}
{% endhighlight %}

In the above code it is possible to specify a font size by passing the argument ratio. It will then take the previously defined variable $base-font-size and multiply it by ratio. This foumula will not work if an argument isn’t passed.

## When is it suitable to us static site generators?

As these site generators doesn't integrate with databases you are requiered to have all the files and markup on the server. This makes it ideal for websites that reqiure text pictures and other static media. Blogs are an perfect example of this. You write your post and then it is what it is until you change it. It is static.