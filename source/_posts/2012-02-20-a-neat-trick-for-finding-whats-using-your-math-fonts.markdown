---
layout: post
title: "A neat trick for finding what's using your math fonts"
date: 2012-02-20 15:18
comments: true
categories: LaTeX
---
So here is a neat trick I saw in response to a question 
I asked on [tex.stackexchange](http://tex.stackexchange.com/q/40757/215).
This post also serves as a way for me to try out some
code markdown.
<!-- more -->

```latex Finding math alphabets http://tex.stackexchange.com/a/40767/215
\newcommand{\PrintMathFonts}{%
  \count255=0
  \loop\ifnum\count255<16
    \typeout{(\the\count255:~\fontname\textfont\count255)}
    \advance\count255 by 1
 \repeat}
```

Now add `\PrintMathFonts` at various places to see what math
alphabets have been used up to that point.
It will print them to the `.log` file.

Using "math" rather than the proper "maths" here might rile
my British English (also known as "proper English") readers.
Let me explain.
I have decided that used in this context,
"math alphabet" and related concepts like "math mode"
are terms of art, and thus can have an alternate spelling.
Likewise, I'm happy to say that I "program" a computer,
though I would insist that I watch "programmes" on TV.
This started as a way to try out code blocks and seems to have
descended into a vain attempt to forestall language
peevery.
Lucky there's no comment section for people
to complain on.
My comment policy is explained on the "About" page at the top.