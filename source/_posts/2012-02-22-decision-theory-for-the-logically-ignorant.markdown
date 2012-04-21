---
layout: post
title: "Bayesianism for the logically ignorant"
date: 2012-02-22 16:39
comments: true
categories: philosophy decision-theory bayesianism
---
This is something that I've been thinking about for a while.
I'm writing it up now because I might talk about it in the
near future, at a job talk.

The basic idea is to wonder what consequences follow
from relaxing the standard assumption that
Bayesian agents are logically omniscient.
<!-- more -->

Bayesian epistemology and decision theory typically
assume that the ideal agents are logically omniscient.
Borrowing a practice from I.J. Good,
I refer to my putative ideal agent as "you".
That is, they assume that if $\phi$ and $\psi$
are logically equivalent, then
you should believe them to the same degree.

This seems to have some normative weight.
What reason could you have for believing equivalent propositions
to different degrees except for some failure of
insight on your part?

But consider "believe all and only the truths".
Likewise, this has some normative force.
The only reason to fail to fully believe a truth
or to fully disbelieve a falsehood,
is some lack of insight or evidence.
So does this mean that we should force you
to have only trivial 0/1 degrees of belief?
Of course not!
Bayesianism is all about how to behave when you can't live
up to the regulative ideal of truth.

I think we need to make the same kind of move in the case
of logical omniscience.
Of course logical omniscience is a kind of
regulative ideal (just like truth is)
but we should think about how to model agents
who fail to live up to this ideal.
So how do you model logical ignorance?
With great difficulty, it turns out.

Let's start with a basic discussion of
simple Bayesianism, and find out
where the assumptions about logical
omniscience creep it.
Here's a first attempt.
The objects of belief are sets of possible worlds.
These sets of possible worlds form an algebra and …
Whoah.
Wait a minute.
If beliefs are about sets of possible worlds,
then we've already baked in logical omniscience!
If $\phi$ and $\psi$ are logically equivalent,
then they will be true in all the same possible
worlds.
So you can't have different beliefs about them.

Here's our first interesting result.
*Logical omniscience is built into
Bayesianism at a very early stage*.
This makes it really quite difficult to 
drop or weaken the assumption.

Let's try to start again in such a way that
it is at least clear where
logical omniscience enters.
So, the objects of beliefs are *sentences in a language*:
syntactic things.
Now $\phi$ and $\psi$ can be different syntactic objects
but still be logically equivalent.
So that's nice.

However, even if there's only one elementary letter in your
language, you now have infinitely many sentences
to have beliefs over!
$a,a\wedge a,a \wedge a \wedge a\dots$
This is awkward, to say the least.
Can we do anything to manage this awkward infinity of 
sentences?
There must be some kinds of things we can do,
since logically omniscient agents managed
to have beliefs over finite algebras.

How to we build in logical omniscience?
We take equivalence classes of sentences
using the logical equivalence relation "$\equiv$".
That is, we identify all the propositions logically equivalent
to $\phi$ and we call this $\overline{\phi}$.
We build up an algebra of equivalence classes of sentences.
This is called the 
"[Lindenbaum algebra](http://en.wikipedia.org/wiki/Lindenbaum%E2%80%93Tarski_algebra)".
*This* is then the thing logically omniscient agents
have beliefs over.

So now we've seen that by taking this 
"[quotient algebra](http://en.wikipedia.org/wiki/Quotient_algebra)"
we can strip down the number of sentences you need
to have beliefs over.
So, are there equivalence relations other than classical logical
equivalence that will give us "well-behaved" quotient algebras
that don't build in logical omniscience?
Yes there are.
What you need is for your relation to be a
"[congruence relation](http://en.wikipedia.org/wiki/Congruence_relation)".
This means basically that it "plays nicely" with the logical structure.

Where does this get us?
Remember we had our norm that said "logically equivalent
sentences should be believed equally strongly".
We might argue that a weaker, but still reasonable norm
would only demand that "sentences *known* to be
logically equivalent should be believed equally strongly".

What can we say about this idea of "known equivalence"?
Well, if you were being a logically omniscient
Bayesian you would say that 
the right relation to use to "quotient up" your space
of sentences is the classical equivalence.
We might instead argue that some other congruence 
which is less stringent is a more reasonable requirement.
We still require that the relation is a congruence,
which is no small requirement.
But it's a start!

In the next post, we'll see that logically ignorant
agents are Dutch-bookable, and then we'll
see why that's not such a problem.

