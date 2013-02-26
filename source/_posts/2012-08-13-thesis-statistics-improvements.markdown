---
layout: post
title: "Thesis Statistics: Improvements"
date: 2012-08-13 19:07
comments: true
categories: thesis linux
---
[Last time](blog/2012/07/24/thesis-statistics-take-1/)
I wrote a simple script to draw a graph of thesis word count
over time using TeXcount and a git repo.
Here I'm just going to point out a few obvious improvements that
I've added to the code in the last couple of weeks.

<!-- more-->
One awkward thing about the previous version of the code was that the
dates for the graph were hard-coded.
It would be better just to use the current date as the end date.
We can get the current date in bash as follows:

```bash
TODAY="$(date +%Y-%m-%d\ %H:%M:%s)"
```

So how can we build a bash script to do what we accomplished with
the `gwc.gp` file and the line `gnuplot < gwc.gp > gwc.png`?
Well, I learned some neat tricks from 
[over here](http://www.techanswerguy.com/2007/08/scripted-gnuplot-graphs.html)
which helped me put together the following:

```bash
#! /bin/bash

TODAY="$(date +%Y-%m-%d\ %H:%M:%s)"

gnuplot <<-finis


set datafile separator ","
set terminal png size 900,400
set xdata time
set timefmt "%Y-%m-%d %H:%M:%S"
set format x "%Y-%m"
set xrange ["2011-12-03 15:08:00":"$TODAY"]
set style fill solid
set key outside right
set grid
set output "gwc-plot.png"
plot "dates.csv" using  8:(\$1+\$2+\$3+\$4+\$5+\$6+\$7) with filledcurves x1 title 'Climate',\
"dates.csv" using  8:(\$1+\$2+\$3+\$4+\$5+\$6) with filledcurves x1 title 'Decision',\
"dates.csv" using  8:(\$1+\$2+\$3+\$4+\$5) with filledcurves x1 title 'Imprecise',\
"dates.csv" using  8:(\$1+\$2+\$3+\$4) with filledcurves x1 title 'Probabilism',\
"dates.csv" using  8:(\$1+\$2+\$3) with filledcurves x1 title 'Framework',\
"dates.csv" using  8:(\$1+\$2) with filledcurves x1 title 'Uncertainty',\
"dates.csv" using  8:(\$1) with filledcurves x1 title 'Introduction'
finis
```

As far as I can tell, `gnuplot <<- finis` basically throws everything
until `finis` at `gnuplot`.
Using `set output` we can specify where we want our output to be.
Note I've had to escape all the dollar signs.
There might be an easier way to do this,
but I just find/replaced the dollar sign.
This is pretty much the same settings as before except that
the output is set as an option
and I've used the `$TODAY` variable to make the date range keep up to date.

What about improvements to the word counting script?
Well, it's pretty crazy that all the commits are word-counted
every time the script is run.
We store most of that information in the `dates.csv` file,
so can't we check there for what the last commit we've counted
was, and then move on from there?

Yes.
We can.
We used `git rev list` to list commits to
iterate our word count command over.
So we can use `git rev list --since="…"` to only list
the commits since the most recent date in `dates.csv`.
We can get the last date out of `dates.csv` easily enough:
they're in reverse chronological order, so we need
the date on the top row, which is in positions `$8` and `$9` 
if we use `awk` to extract it.
So adding in those improvements,
the new git word count file looks like this:

```bash
#! /bin/bash

FILES="introduction.tex
uncertainty.tex
framework.tex
probabilism.tex
imprecise-probabilities.tex
decision.tex
climate-decisions.tex"

LASTGIT="$(awk 'NR==1 {print $8,$9}' dates.csv)"
for commit in	$(git rev-list --since="$LASTGIT" development)
do
	for FILE in $FILES
	do
	    printf "$(git show -s --oneline $commit:$FILE 2>/dev/null |texcount -q -template={SUM} -nosub - ), "
	    # printf "$(git show -s --oneline $commit:$FILE 2>/dev/null |wc -w ), "
	    2>/dev/null
	done
	printf "$(git log -1  --date=iso --pretty=format:%ad $commit) \n"
done
```

Now we need to work out how to get this new word count list to
prepend the new word counts to the top of `dates.csv`.
The following script shows how to do this.
The trick is to output the new dates to a temporary file,
and then append the contents of the old `dates.csv` file
to the end of it.
Then we move the temporary file to `dates.csv`.

```bash
#! /bin/bash

./gwc-git.sh > /tmp/dates.tmp && cat dates.csv >> /tmp/dates.tmp && mv /tmp/dates.tmp dates.csv &&
./gwc-doplot.sh
```

So that's a better word count script.

{% img /images/thesisplot-2.png Thesis plot %}
