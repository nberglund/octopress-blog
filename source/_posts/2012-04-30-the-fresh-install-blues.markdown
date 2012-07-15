---
layout: post
title: "The fresh install blues"
date: 2012-04-30 16:08
comments: true
categories: linux, octopress
---
I recently installed Ubuntu 12.04.
I decided to do a fresh install, 
rather than upgrading from 11.10.
This inevitably involved a whole bunch of 
customisation-faff.
Let me tell you about it.

<!-- more -->

So in 11.10, I followed
[these instructions](http://askubuntu.com/a/104744/702)
and octopress worked fine.
But on 12.04 it didn't.
This was weird because as the poster says, 
he's writing from 12.04.
Anyway.

I needed to install `zlib1g-dev` and `libssl-dev`
as explained in this 
[blog post](http://blog.bigdinosaur.org/setting-up-octopress/).
This needed to be done _before_ building ruby.
So then I installed `rbenv` and `ruby-build`.
These had better instructions,
and seems simpler than the other suggested alternative:
`rvm`.

Since I use `zsh` and this shell
[likes doing clever pattern matching and
other fancy shenanigans on your terminal input](http://www.refining-linux.org/archives/37/ZSH-Gem-2-Extended-globbing-and-expansion/),
I needed to add the following line to my
`.zshrc`:

```
alias rake='noglob rake'
```

Thanks to 
[this guy](http://travisjeffery.com/b/2012/01/zshs-extended-glob-and-octopresss-new-post-script/)
for that trick.

This works fine, it seems.
Or rather, if this post gets onto the blog,
then everything is working fine.

I also had to do various things like 
get a new rsa key and have 
[Nearly Free Speech](http://www.nearlyfreespeech.net/)
and [github](http://www.github.com/)
accept it.

I've still not got emacs customised
to my liking.
[I couldn't get the toolbar and menu bar to go away!](http://askubuntu.com/q/128376/702)
But I got aucTeX and refTeX working,
and I got the 
[Solarized colour theme](http://ethanschoonover.com/solarized)
going.
I haven't yet tried to compile my thesis.
I am scared this will break.
I foolishly forgot to backup my `.stumpwmrc` so 
I need to customise that again.

I also need to reinstall things like R,
Haskell (for [Pandoc](http://johnmacfarlane.net/pandoc/)),
netlogo and so on.
And get my compose key working and so on.
And decide whether to carry on using Thunderbird
(the pass of least resistance),
switch to claws, or even mutt.

Oh, and I also have a thesis to write.
