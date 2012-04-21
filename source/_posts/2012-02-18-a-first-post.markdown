---
layout: post
title: "A first post"
date: 2012-02-18 12:57
comments: true
categories: octopress
---
[My old blog](http://incompetnce.wordpress.com) is being retired,
and my new blog (this one) is commencing.
Over the course of the next few weeks I will be moving some of the 
more interesting philosophical posts onto this blog.

This post is more of a test than anything else.
I am now using the [Octopress](http://www.octopress.org) 

I am now testing whether mathematics works.
First, a display formula:

$$e^{i\pi}+1 = 0$$

Next, a more ambititous inline version of the same formula.
$e^{i\pi}+1 = 0$.
Let's see if either of these work.
It looks like things are working.

Here's how I got things working with a minimum of fuss.
First, I switched to kramdown, as recommended 
[here](http://kqueue.org/blog/2012/01/05/hello-world/).
This got display maths working.
But inline maths was still broken.
So using the MathJax configuration script described
[here](http://luikore.github.com/2011/09/good-things-learned-from-octopress/)
I got inline maths working too.
In fact, a neater explanation appears 
[here](http://steshaw.org/blog/2012/02/09/hello-mathjax/).

There's a bunch of other posts recommending different ways of dealing with 
$\LaTeX$ maths, but this is what worked for me.
Unfortunately, this means you need to use the dreaded "double dollars"
for display maths.
And as we know, in PDF documents, this is [evil](http://tex.stackexchange.com/q/503/215).
