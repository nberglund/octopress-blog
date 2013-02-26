---
layout: post
title: "Thesis statistics: Take 1"
date: 2012-07-24 18:58
comments: true
categories: thesis linux
---
"Hey, I wonder how hard it would be to generate
a stacked graph of the word count of my thesis over time."
And bang goes an evening.

<!-- more -->

How are we to find a good word count of a
`.tex` file?
There's a whole post in this question itself.
For now, let's just say that we are going to be using
the [texcount](http://app.uio.no/ifi/texcount/index.html)
script.
Here is how we are going to be word-counting
our files:

```
texcount -q -template={SUM} -nosub $FILE
```

The `-q` flag suppresses errors which would
otherwise mess up our output,
the `-template="{SUM}"` flag
tells texcount that we only want the sum
of words in text, headings, footnotes and so on.
The `-nosub` flag tells `texcount` not to bother doing subcounts
(how many words in each section).
It doesn't seem to have any effect on performance,
but better safe than sorry.

How do we find out what the word count
was at some point in the past?
What, you mean you don't have version control
for your thesis?
I use [git](http://git-scm.com/)
to keep track of changes to my thesis.
I can find out what a previous version of a file looked by doing:

```bash
git show $COMMIT:$FILE
```

Obviously, replace `$COMMIT` and `$FILE` with 
the name of the commit and the file you are interested in.
So if I pipe this into `texcount`,
I can find out what the word count was at various past times.

Next, we want to loop over a bunch of different
commits, and get the word count for each previous version of the file.
Here's how to do that for `git`:

```bash
for COMMIT in	$(git rev-list -n 10 master)
do
    printf "$(git show  $COMMIT:$FILE 2>/dev/null | texcount  -q -nosub -template="{SUM}" -), "
    2>/dev/null
done
```

We use `git rev-list` to get us the last 
ten commits from the `master` branch
and then pipe the output of `git show` into `texcount`
for each `$COMMIT`.
This we output to the terminal with `printf`.
We also send `stderr` to `/dev/null` to avoid
errors cluttering up out output.
There will be errors if you try to `show` a file from a commit
before the file was created.
This isn't a problem since then `texcount` will output `0`
as expected, so it's best just to ignore the errors.
Once we get this working, we can get information on all the commits
by removing the `-n 10` flag.

As well as each word count, we want the *time* the
commit was made.
We can get that with the following:

```bash
	printf "$(git log -1  --date=iso --pretty=format:%ad $commit) \n"
```

Note our previous `printf` (in the `git show` line) ends with a comma and then a space.
This means that our output will be `wordcount, date`.
We'll want the next record to be on the next line, 
hence the `\n` explicit newline at the end of this command.

We want to word count for several files,
so let's work out how to loop over them.
I don't know much about how bash scripting works,
so I'm pretty much stumbling around experimenting until something seems to work.
The following seems to work.

```bash
#! /bin/bash

FILES="unavoidable.tex
betterdecisions.tex
milnor.tex"
# for FILE in $FILES
# do
#     printf "$FILE, "
# done
# printf "\n"
for commit in	$(git rev-list -n 5 master)
do
	for FILE in $FILES
	do
	    printf "$(git show $commit:$FILE 2>/dev/null | texcount  -q -nosub -template="{SUM}" -), "
        # printf "$(git show -s --oneline $commit:$FILE 2>/dev/null |wc -w ), "
	done
	printf "$(git log -1  --date=iso --pretty=format:%ad $commit) \n"
done
```

I define a list of files.
I don't know what sort of list structures bash understands,
so I basically worked out by trial and error that putting each file on a line works.
There's probably a nicer way, but whatever.
I have three files in this example.
Note also the commented out line that pipes the `show`
to `wc -w` instead of `texcount`.
For testing purposes, this is useful,
since it's *way* quicker.
Note also the commented out stuff at the top
which would put a header row on your
CSV table.

Now obviously you'll want to put this in a file
with an appropriate header, e.g. `#! /bin/bash` or similar
and then run it, and send the output to a file.
I'll assume the file is called `dates.csv`.

Here's a little output from one version of
my `dates.csv` file.

```
14805, 10867, 2170, 2011-08-22 15:48:04 +0100
14805, 10845, 2170, 2011-08-19 16:20:17 +0100
14805, 10793, 2170, 2011-08-19 16:04:46 +0100
14805, 10669, 2170, 2011-08-15 18:21:13 +0100
14805, 10648, 2170, 2011-08-15 12:59:24 +0100
14805, 10443, 2170, 2011-08-14 16:25:54 +0100
14805, 10443, 2170, 2011-08-14 16:24:57 +0100
```

Wouldn't it make more sense to put the date column first rather than last?
Maybe, but I didn't.
This way you don't have to worry about trailing commas after the last column,
which is an advantage, I guess?

Anyway.
Now we want to use 
[gnuplot](http://www.gnuplot.info/)
to create some funky graphs.
Rather than explain how to build the graph,
I'll point you to 
[this post](http://freesoftware.zona-m.net/how-to-create-stacked-area-graphs-with-gnuplot/)
which shows how to draw stacked charts of the kind we want.
That post recommends pre-processing the data to get it to work,
but it's much easier to use `gnuplot`'s built in capacities.

```
set datafile separator ","
set terminal png size 900,400
set xdata time
set timefmt "%Y-%m-%d %H:%M:%S"
set format x "%Y-%m-%d"
set xrange ["2011-02-05 16:47:32":"2011-08-22 15:48:04"]
set style fill solid
set grid
plot "dates.csv" using  4:($1+$2+$3) with filledcurves x1 title 'milnor',\
"dates.csv" using 4:($1+$2) with filledcurves x1 title 'betterdecisions',\
"dates.csv" using 4:1 with filledcurves x1 title 'unavoidable'
```

I won't explain much about this `gnuplot` configuration, 
but note that you can use `$1+$2` to get a graph of 
the sum of columns 1 and 2:
this is easier than the pre-processing that the above linked
post suggests.
At least, that's my opinion.
Save something like the above as `gwc.gp` or whatever,
and then call `gnuplot` feeding in this file as input
and telling it where to put the output.
Like so:

```
gnuplot < gwc.gp > gwc.png
```

And that's about all you need to know to create
a stacked chart of change in word count over time.

Sadly, I didn't start my git repo when I started writing,
but only some time later.
So I don't have the gratifying experience of seeing the whole growth of
the thing.
But here's the final product:

{% img /images/thesisplot.png Thesis plot %}

A word of warning:
the bash script is quite slow.
It takes about 30 seconds to do 3 files on 10 commits.
Or 30 seconds to count 30k ish words 10 times.
Now my actual thesis is approaching 70k words and
there are at least 70 commits.
It takes over six minutes to run.
So if you are going to try this,
use the `wc -w` line instead
and make sure to limit the number of commits that
`rev-list` spits out until you're sure it's working
as hoped.

How's that for structured procrastination!
