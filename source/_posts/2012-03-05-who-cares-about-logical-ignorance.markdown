---
layout: post
title: "Who cares about logical ignorance?"
date: 2012-03-05 11:04
comments: true
categories: philosophy decision-theory bayesianism
---
So far, I have
[wondered how to model logical ignorance](/blog/2012/02/22/decision-theory-for-the-logically-ignorant)
and I have shown how to 
[Dutch book the logically ignorant](/blog/2012/02/28/dutch-booking-the-logically-ignorant).
But who *cares* about logical ignorance?
Surely logical omniscience is a norm of rational belief:
what possible reason could you have for believing logically equivalent propositions to
different degrees?
So in this post I want to step back a bit and wonder about why modelling logical
ignorance is important.

<!-- more -->

First, let's consider the argument I hinted at above:
"why would you believe logically equivalent propositions
to different degrees except through some failing
of your reasoning capacity?"
Is this a good argument?
I think it is exactly as good as the following argument:
"Why would you have any degree of belief less than full belief
in a truth, except through some failing of your evidence?"
Now the obvious outcome of taking this second argument too seriously 
is to have no non-trivial degrees of belief:
you must fully believe all and only the truths.

We don't take this norm seriously because of the
"ought implies can" principle.
We simply *can't* fully believe all and only the truths:
we don't always know which sentences are the truths.
Since we can't conform to this ideal,
it can't be something we *ought* to do.
This idea is still a kind of *regulative ideal* on
belief, but it certainly isn't a *norm*.
Failing to live up to the ideal of believing all
and only the truths doesn't impugn your rationality;
you aren't irrational for having failed to fully believe a truth.
But you still consider it better to believe more truths
more strongly.

I want to make the same case for logical omniscience:
it is obviously a regulative ideal of belief,
but it is not a norm.
Rational agents can fail to believe logically
equivalent propositions to the same degree
(because of some lack of reasoning capacity)
but they aren't thereby irrational.

Bayesianism starts from the idea that 
there is something interesting
to say about rational belief
even if you fail to fully believe all and only the truths.
That is, there are rational ways to partially believe.
In the same way, I want to say that there are rational ways
to have logically ignorant beliefs.

Now, I don't really know what more to say about
logically ignorant belief for now.
Dutch book arguments don't really get us very far.
It's all but impossible to rule out the possibility of
being Dutch booked.
I'm going to write about that in a later post.

We certainly want to demand that sentences known to be logically equivalent
ought to be believed to the same degree.
So there are some rationality constraints of
logically ignorant belief.
But I'm not sure how to fully articulate them.
If you'll indulge some highly speculative vague suggestions,
I think it would be interesting to see what happens
when you throw ideas like proof complexity, or 
costs of computation into the mix.
Being Dutch booked for failing to spot a really easy proof
seems worse than failing to, say, find a proof of 
[Goldbach's conjecture](http://en.wikipedia.org/wiki/Goldbach%27s_conjecture).

The major difficulty with this sort of idea is that
any relation of known entailment based on 
complexity of proof is not going to give you 
a transitive "entailment" relation,
thus it won't be an equivalence relation
in the sense of defining equivalence classes.
So all the nice quotient algebra stuff I discussed previously flies out the window!

To finish, let me situate this even more broadly within my interests.
Any formal theory of rational belief or decision is going to
be, to some extent, idealised.
Bayesianism is no exception.
It is interesting and worthwhile to see what
happens when these idealisations are relaxed.
This process of "de-idealising" is something
that might be familiar from discussions of
idealisations in science.
We "idealise away" air resistance when considering cannon ball
trajectories.
Why?
*Because we don't think it has a big effect*.
We don't think adding it back in (de-idealising)
will substantially affect the results we obtain.
This is why the idealisation is legitimate:
the decrease in computational cost far outweighs
the distortion in the results thereby obtained.
(Those familiar with this discussion may find this
a caricature of the debate, but it is 
good enough for my purposes).

So I think we should think about the same sort of
de-idealising process in formal theories of belief
and decision.
Instead of "what happens when we add back in air resistance?"
we should be wondering "what happens when we remove logical
omniscience?"
And we have an extra important purpose in the case of 
de-idealising theories of belief:
we are not ideal agents, so it's useful to see what 
norms non-ideal agents such as ourselves should conform to.

As we've seen, it's not trivial to excise logical omniscience:
it's built into the framework at quite a low level.
And indeed, even when we don't build it in,
it emerges as a norm.
Or at least, that's one way of reading the Dutch book result from
my previous post.

Next time, I'll try to summarise some work I've done with
more permissive Dutch book frameworks.
