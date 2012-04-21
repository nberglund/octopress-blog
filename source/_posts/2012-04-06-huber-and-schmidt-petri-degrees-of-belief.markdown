---
layout: post
title: "Huber and Schmidt-Petri: Degrees of Belief"
date: 2012-04-06 18:23
comments: true
categories: philosophy, epistemology, degrees-of-belief-book
---
This is the first in what I hope to be a series of posts on the book
[_Degrees of Belief_](http://www.springer.com/philosophy/book/978-1-4020-9197-1)
edited by Franz Huber and Cristoph Schmidt-Petri.
There are some really interesting papers in there
so this should be fun.
In fact, this is the first in what I hope to be a series of series
of posts on books I am reading.
Indeed, I hope to make a habit of writing about books I'm reading.
This seems like a good way of actually making this blog work for me,
rather than it just being an exercise in procrastination.

<!-- more -->

Anyway, the book is about degrees of belief.
The clue is in the title.
The book is split into three parts.
The first part is on the relationship between degrees of
belief and categorical, or full belief.
The second part is on formal models of degrees of belief:
probability theory and friends.
And the third part is on "logical approaches".
I haven't read that section, so I don't really know what
that means yet.

This post is really just to introduce the series of posts,
which will start next week when I get back from my holiday.
So in this post I'll restrict myself 
to a couple of comments on the introductory chapter
by Franz Huber.

Huber basically sets out to survey the material that will
be covered by the other contributors to the book.
Along the way, he makes one or two interesting comments
I'd like to pick up on.

On page 10, Huber introduces Dempster-Shafer belief theory
by saying that 
{% blockquote %}
The theory of Dempster-Shafer belief functions …
rejects the claim that degrees of belief 
can be measured by the epistemic agent's
betting behaviour.
{% endblockquote %}

This is a slightly odd claim to make.
I don't know whether Dempster or Shafer make this claim.
As I understand it, DS belief theory was designed as
a theory to amalgamate different sources of evidence.
Hence all the "Dempster's rule of combination" stuff.
Decision making, and thus betting, doesn't come into it.
So might that be what Huber means?

I guess what Huber is driving at is that 
adopting any kind of non-probabilistic model
of belief requires getting around the Dutch book argument.
Now, _one way_ of doing that is to simply deny that
belief can be measured by betting behaviour.
But this isn't the only way.
Indeed, for a suitably modified betting scenario,
DS beliefs are measured by betting behaviour
as I showed in 
[_Dutch book arguments and imprecise probabilities_](http://www.seamusbradley.net/Papers/dba-ip.pdf) [PDF].

Well, that's a minor point.
And one that I only really brought up so I could mention my own paper.

Huber makes an interesting point a little later on, 
when discussing how to interpret the DS belief and plausibility
functions $\operatorname{Bel}$ and $\operatorname{Plaus}$.
He suggests that $\operatorname{Bel}(A)$ measures the degree
to which the evidence you have supports $A$.
And $\operatorname{Plaus}(A)$ measures the degree to which
the evidence _doesn't_ support $\neg A$.
So far, so conventional.
Now, the interesting point that I'd not seen mentioned before is this:
on this understanding, probabilism is just the claim that all
evidence supports either $A$ or $\neg A$.

If we understand probabilism as the claim that
degrees of belief ought to be probabilities,
and we notice that probability functions are a special case of
DS functions where $\operatorname{Bel}(A) = \operatorname{Plaus}(A)$ 
for all $A$, then probabilism just is the claim
that all evidence that does not speak for $A$ speaks against $A$.
I think this is a really nice way of understanding something of the relationship
between the frameworks.
DS theory (and similar frameworks) allow an agent to
suspend judgement in a way that a probabilist simply cannot.
I especially like this, because it fits perfectly
with something I've been writing in my thesis about 
the Objective Bayesian norm of Equivocation, 
and how wrong it is.
But I'll save that for another time.

Huber then goes on to discuss some other similar
formal models of belief: possibility theory, ranking theory.
I can't say I fully understand what advantages these have over,
say DS theory, but I'll save my gripes until I've read the contributions
that properly cover those models.

Huber's paper ends with a discussion of
belief revision and non-monotonic logic.
Again, I will have more to say about those topics when we get to the 
full sections on them.

So, there you have it:
a not entirely satisfactory summary of a summary
of a book.
Tune in next time for some discussion of the Lockean thesis 
and full belief!
