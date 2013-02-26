---
layout: post
title: "Credence, graded possibility and weight of evidence"
date: 2013-01-20 16:21
comments: true
categories: bayesianism philosophy chance epistemology
---
Here's a post that's actually about philosophy.
The basic idea is that there seem to be lots
of different kinds of "measures on events"
that we can think about.
There are credences,
there are chance functions,
and there are others (about which more later).
I just want to try and identify and distinguish some of these.

<!-- more -->

Let's start with a puzzle.
The standard axioms of graded belief
require that $b(\top)=1$ where $\top$ is the tautology.
They will also end up requiring that
contingent truth $X$ also gets $b(X)=1$.
So this notion of belief can't capture the idea that 
$X$ could have been false in a way that $\top$ simply couldn't.
Not all contingent truths are created equal.
Some contingent truths are surprising,
some are not.
If I roll six dice,
I do not expect to get all sixes.
If I were to do so,
my belief that I got six sixes would be one,
but there's still a sense in which that outcome was *unlikely*.
The set of possible worlds where such an event happens
is intuitively small.
Is there some notion of a measure on the set of events
that captures this intuition that some truths are
"more possible" than others?
(I think the idea of chance as "graded possibility" goes back to Leibniz).
I bet we could define some measure $c$ on the set of possible worlds
such that $c$ is a probability measure.
In fact, in another post, I may actually relate a couple of theorems
that would guarantee this (and more!).
Intuitively, $c$ would measure the size of the set of possible worlds
where the event is true.
This measure, unlike credence, would not change in the light of evidence.
It would be
something like the "ur-chances" that Richard Pettigrew talks about
[here](http://dl.dropbox.com/u/9797023/Papers/chancecrednorms.pdf)
for example.
We could define a conditional notion of graded possibility in
terms of the measure restricted to the conditioning event.
This would behave like a conditional probability 
(again, theorems in a later post).

So we have credence, and we have this "graded possiblity" which
is something like chance,
but perhaps a bit different
(such a function won't satisfy 
[Schaffer's](http://bjps.oxfordjournals.org/content/58/2/113.abstract)
requirements for something to play the *chance role*).
I guess they are going to be related notions
(related by something like Lewis' Principal Principle
or one of its close cousins),
but they certainly aren't the same thing.
Here's a third notion:
"weight of evidence".
Again, not unconnected from the other notions,
but arguably distinct.
Here's an example.
I have just rolled six sixes.
The evidence for my having done so is 
about as strong as evidence gets:
direct evidence of my senses.
I still find the fact surprising,
despite having excellent evidence that it is so.
(And my credence in such a thing having happened is one.)
Now my friend tells me he has failed to roll six sixes.
My evidence for such a proposition is weaker –
I have only testimonial evidence –
but the proposition is unsurprising.
So I am inclined to have a high degree of belief in
such an event having occured despite the weakness of the evidence.
What would a formal measure of weight of evidence look like?
Well, Dempster-Shafer belief theory is a better
measure of evidence than it is of belief.
(Shafer's book was called *A Mathematical Theory of Evidence*,
after all).
So maybe that's what it should look like.
But how it should relate to credence seems tricky.
Anyway, others have thought about something like this idea,
like [Jim Joyce](http://www-personal.umich.edu/~jjoyce/papers/hpre.pdf)
and [James Hawthorne](http://mind.oxfordjournals.org/content/114/454/277.abstract).

One might think that the weight of evidence thing
is really just captured by your credences in the following way:
the more your credence can be moved by a particular
piece of evidence,
the less your weight of evidence for that proposition is.
That is, weight of evidence is captured by the *resilience* of your credences.
Maybe.
I'll have to think about that some more.
I guess the main thing I wanted to get across here
is that there's more to belief than *degree of belief*.
That is, there's more to belief than *just* the numbers
the belief function assigns to the events.
For example, there are various kinds of structural fact about your
beliefs that you might take to be important 
(like that two events are independent).
I talk about this a bit in my thesis.
(I'm procrastinating to avoid doing my corrections,
in case you're wondering).
I might talk about another example of this later.

So we have these three notions.
Credence, graded possibility (surprisingness?)
and weight of evidence (or perhaps strength of evidence).
The more surprising a proposition,
the stronger the evidence needs to be to move your credence.
And conversely,
the less surprising a proposition,
the more your credence can be moved by even weak evidence.
I wonder if surprisingness and strength of evidence are enough
to effect a "decomposition" of credence-dynamics.
And if not, what is missing?
