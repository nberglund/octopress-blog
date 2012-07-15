---
layout: post
title: "An idea for dealing with 'to do' notes"
date: 2012-06-15 16:03
comments: true
categories: productivity
---
So I had this idea when I saw 
[this question](http://tex.stackexchange.com/q/22972/215)
on the TeX Stack Exchange site.
Indeed, this is more or less an elaboration of my answer to that question.

I'm sure that I'm not the only person whose
draft documents are littered with comments like
`%TODO fix this paragraph` or
`%TODO substantiate this claim`.
With a little discipline about how you format these 'to-do'
comments, there are some neat things you can do with them.

<!-- more -->

If all your to-do notes actually start with `%TODO`
then you can use a tool like `grep` to find them all.
This is pretty obvious.
So this is a good argument for getting into the habit of 
formatting your notes to yourself in some such
easily greppable way.
(Is "greppable" a word? 
Sure, why not.)

Here's an initial specification for making 
your to-do notes greppable.

 - Each note starts on a new line.
 - Each note stays on one line only.
 - Each note starts with `%TODO` or some other easily searchable phrase.
 
Next, we need to search for them.

```
grep -n '%TODO' file.tex
```

This searches for the pattern `%TODO` in the file
`file.tex` and prints the line, with its line number 
(that's what the `-n` tag is for).
This gives us a quick way to see what's going on
in our file.
If we had a big multi file project –
like, say, that PhD dissertation I'm supposed to be writing –
then we could grep across all the `.tex` files in the dreaded
`thesis` folder.
This would give us a neat overview of where the problems were.
I actually defined a command `\worries`
which writes its argument in a marginpar
so that the to-do note appears where it is relevant in the text.
But these notes aren't all on one line.
I could overcome this problem somewhat with grep's
`-A 5` tag which would print the line with, say `\worries` on it, and the next
five lines.
But this isn't ideal,
since it isn't smart enough to _only_ print the lines
that relate to the note.
Anyway, grepping "worries" still gives a pretty good overview of where the issues are.

If I'd had more discipline and kept my notes on one line each,
this would have been more useful.
Once we've got our list of `%TODO`s,
we can write that to a file and then input the file
at the end of our document.
We'll have to use `\verbatiminput` (from 
[`verbatim`](http://ctan.org/pkg/verbatim))
or some other such command,
because of the comment symbols in `%TODO`.
Presumably with some regex/awk/grep magic on that file
we could even make it amenable to having each to-do note
render as an item in a LaTeX `itemize` environment.
You could also then call a script which runs your grep command
within your `.tex` file (with the appropriate
`write18` settings etc).

"Gosh, Seamus, you're so clever (and handsome)"
I hear you cry "but surely you know that
the [`todonotes`](http://ctan.org/pkg/todonotes)
package already does most of this sort of stuff."
I reply:
`todonotes` does some things, but not others.
That package is quite good at indicating, 
in the output file, where the problems are.
You can do a `\listoftodos` (I think it's called)
that lists all your to-do notes.
That's pretty neat.
But it lists them by page in the output.
What my method ends up with is
a list of notes linked to where they crop up
in the _input file_ which is, after all,
what you will be editing.
This, I think, can be more useful.
There may be packages which achieve what I do here,
but I think there's something pleasingly basic
about this solution.
While we're on the subject of line numbers
and input files,
I hope to have a go at fixing up my
[`draftinputlines`](https://github.com/scmbradley/draftinputlines)
package and submitting it to CTAN.
What fun.

Note that with the current theme, 
inline code blocks that also happen to be links don't
show up as much different from inline code blocks
that aren't links.
Some of the inline code here is clicky.

