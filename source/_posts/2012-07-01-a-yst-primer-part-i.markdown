---
layout: post
title: "A yst primer: Part I"
date: 2012-07-01 11:30
comments: true
categories: yst-primer tutorial
---
I'm about to roll out a new version of my website,
a version based on John Macfarlane's excellent 
[yst](https://github.com/jgm/yst).
Yst is a nice little program that takes some `yaml` data files
(or csv, or SQL) and some templates and builds a static website.
The documentation on the github page is a little spare,
so I thought I'd write an introduction to the program.
This will be super basic, but I hope it will help some people
take their first steps.

This is the first of a projected series of posts on 
yst.
The series will live in 
[this category.](/blog/categories/yst-primer/)
I'm writing this more to get clear in my head
what the structure is.
It's a little confusing at first
because you need quite a few files
working together to get things working.

<!-- more -->

First, what is yst and why would I use it?
Here's what attracted me to the idea:
I can have, say, my list of publications
or my list of conference talks as yaml data.
I can then use yst to build a CV page for my website.
I can also use yst to generate a `.tex` file 
for a pdf version of my CV.
This way, I don't need to make the same edits in two different places when
I give another talk.

Yst uses Pandoc under the hood, 
so you could in theory also generate an
ebook of your CV, or any number of other output formats that
Pandoc supports.
I can't believe I just used the phrase "under the hood".

What I am not going to is explain how to install
Haskell, Cabal, Pandoc and Yst.
The instructions on the yst site were enough for me,
and I don't really know any more about the process
than I learned from reading that page.
So I will jump straight to building a site with yst.

On the yst documentation it recommends running `yst create mysite`
to generate a sample site for you to play with.
The documentation then goes through some of the cool stuff 
that this sample site demonstrates.
I did this, but I found it a little complicated to get my head around
at first.
So here I'm instead going to start from scratch and build things up very slowly.
The intention here is that we will end up at a point
where you will be able to understand what the sample site is showing off.
Incidentally, the documentation is in the `README` file in the `mysite/` directory.

The first thing to do is to move to your new directory
and create a file called `config.yaml`.
This is the file that yst will look at to work out what's going on.
Here is the `config.yaml` that the starter site generates:

```
indexfile: index.yaml
title: My Website
templatedir: .
datadir: .
filesdir: files
layout: layout.html.st
```

The important lines for now are `indexfile`, `title` and `layout`.
The `title` will appear in the `<title>` of your website.
You can change it to whatever you like,
but beware the "yaml gotchas" mentioned in the `README`.
The main page we will need is the `index.yaml` file mentioned
above.
Let's make one of them now.
The `index.yaml` file basically lists all your pages
that will appear on the site.
Here's a very simple example.

```
- url: index.html
  title: Home
  template: index.st
```

All that's listed here is the url of the page to make,
the title it should have,
and where its template lives.
Later on we'll see more complex versions of this scheme.

OK. 
We now need to write `index.st`.
This will be where the main content of the page is written.
You can basically write this page in markdown.
Here's my simple example.

```
# Welcome to the basic website
 
Here is the world's simplest `yst` website.
```

Before we continue, we need one more file.
The `layout.html.st` file is basically the place
where the html template for the site lives.
Copy the version from the starter site for now.
At this stage, I just want to point out one thing about this.
Look at the `<title>` tag.
It should say:

```
<title>$sitetitle$ - $pagetitle$</title>
```

This uses string templates to replace the text between
dollar symbols with the right stuff.
So `$sitetitle$` is the title of the site, 
as set by the `title` line in `config.yaml`
and then a dash and then 
the `$pagetitle$` as set by the `title` line
of the page in `index.yaml`.
We'll see some much cooler examples of string template's
power later.
Note also that the `layout.html.st` contains
things like `$nav$` and `$content$`.

So you should now have a directory with the following 
files in it:

 - `config.yaml`
 - `index.st`
 - `index.yaml`
 - `layout.html.st`
 
You should now copy the `files/css/` subdirectory
of the sample site into `files/css/` of the basic site 
we are creating.
The css is a mess, but it's easier just to do this
for now.
 
Running `yst` inside this directory should
generate a *very* basic website.
It should generate a folder called `site` with a file called `index.html`
(and the css directory).
The `index.html` file should appear more or less like this:

{% img /images/yst-pic-1.png My first yst site %}

So this is the basic structure of files that `yst` uses to build a website.
So far, this seems quite a round-about way of doing
something rather simple.
We needed a total of five files just to build a single
page!
(That is, the four listed above, and a css file:
as things stand we actually needed a whole bunch of messy
css files, but that's not important).
That seems overkill.
But things will make sense when we see the power of 
the combination of yaml and string templates.
Next time, we're going to see how to use other YAML files
to use some structured data and automagically have it added to our
site.
