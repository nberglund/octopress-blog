---
layout: post
title: "Dutch booking the logically ignorant"
date: 2012-02-28 11:15
comments: true
categories: philosophy decision-theory bayesianism
---
[Last time](/blog/2012/02/22/decision-theory-for-the-logically-ignorant), 
we saw that logical omniscience is difficult to get rid of. 
We saw that once you "go syntactic" it becomes difficult to
stop your set of beliefs being infinite. 
We used a quotient algebra like what the Lindenbaum algebra
does for the standard account to keep things manageable. 
This time round, we're going to abstract from these details. 
All we assume now is that there is some structure of the beliefs.
That is, the beliefs have at least some logical structure 
and that these beliefs inform betting odds. 
What I want to demonstrate is that a logically ignorant agent
can be Dutch booked. 

<!-- more -->

So, I assume there are sentences $\phi$ and $\psi$ that express the same proposition, 
but that are believed to different degrees. 
This means that the odds you would offer on one are different from the odds on the other. 
Since in the standard Dutch book setting, the opponent is
allowed to choose the "direction" of the bet, 
she can choose to bet *against* the one with the longer odds and
*on* the one with the shorter odds. 
In either case exactly one bet wins. 
If she arranges her bets such that they would win the same, 
then her outlay will be less than her winnings:
she will have Dutch booked you! 

Consider bets of the following form:

 - Win $S (1-q)$ if $\phi$, lose $S q$ otherwise.
 - Win $T (1-p)$ if $\psi$, lose $T p$ otherwise.
 
The $S$ is the stake, and the $q$ is the betting quotient.
Likewise for $T$ and $p$.
The idea behind the Dutch book argument is that if
your opponent can set the size of $S$ and decide whether it is positive or 
negative, then unless your $q$s have the structure of a probability measure,
you are guaranteed to lose money: you will be "Dutch booked".
What I want to show here is that a logically ignorant punter
can be Dutch booked.
That is, if $q \neq p$ then an agent who knows that
the two propositions are logically equivalent can
guarantee herself a profit.

We have stipulated that $\phi$ and $\psi$ are logically equivalent.
Importantly, this means that they are always true or false together.
So there are two possibilities: both are true or both are false.

Now, the clever punter will set $T = -S$ .
If $\phi$ (and hence $\psi$) is true, then the two bets together win:

$$
S(1-q) + T(1-p) = S(p - q)
$$

If the proposition is false then the outcome for our agent is:

$$
-S q -T p = S(p - q)
$$

So in either case the punter's wealth changes the same amount.
Now here's the thing:
as in the standard Dutch book argument, we are allowing
the opponent to decide the value of $S$.
So depending on whether $q$ or $p$ is bigger,
the opponent can set $S$ such that our agent loses money!

The only way to avoid this is to set $q = p$.
But that is simply to say that the agent should be logically
omniscient!

Next time, I'm going to look at what can be done about this
state of affairs.
