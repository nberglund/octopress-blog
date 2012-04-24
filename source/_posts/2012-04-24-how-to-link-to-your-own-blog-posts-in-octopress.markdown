---
layout: post
title: "How to link to your own blog posts in Octopress"
date: 2012-04-24 17:08
comments: true
categories: octopress
---
So it turns out that some of the links on this blog were broken.
They should all be fixed now and I thought it would be worth 
writing a quick post to explain how I make links to my own posts.

<!-- more -->

First, I have made my root directory be `/blog`.
That is, I have the line `root: /blog` in `_config.yml`.
This is relevant to what follows.
Now you could link to your own posts just by linking the whole
URL starting `http://…` and so on.
But I prefer to make the links shorter.
So to link to this post I would write the following:

{% codeblock How to link to your own posts %}
[This](/blog/2012/04/24/how-to-link-to-your-own-blog-posts-in-octopress) is a working link
{% endcodeblock %}

Note that the link starts with `/blog` 
(since that's the root).
I had some problem with a few links not liking having a 
trailing slash, but I can't replicate the problem now.

I've also had some trouble writing this post.
I don't know how to get syntax highlighting for markdown.
I tried `lang:markdown` in the 
[`codeblock`](http://octopress.org/docs/plugins/codeblock/)
but that didn't seem to work.
