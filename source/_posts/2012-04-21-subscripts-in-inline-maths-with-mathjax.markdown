---
layout: post
title: "Subscripts in inline maths with MathJax"
date: 2012-04-21 13:58
comments: true
categories: octopress
---
Here's a brief note to say that you need to escape underscores in inline 
MathJax mathmode in order to have subscripts work properly.

<!-- more -->

```latex Proper subscripts in inline mathmode
Here is text and then: $X\_y$. More text.
```

This  produces the following.
Here is text and then: $X\_y$. More text.

You don't need to escape underscores in display mode.

```latex No need to escape underscores in display mode
$$
X_y
$$
```
produces:

$$
X_y
$$

I am using 
[Kramdown](http://kramdown.rubyforge.org/index.html).
I don't know whether similar remarks apply to other markdown engines.
See [this post](blog/2012/02/18/a-first-post/)
for more on my octopress configuration.
