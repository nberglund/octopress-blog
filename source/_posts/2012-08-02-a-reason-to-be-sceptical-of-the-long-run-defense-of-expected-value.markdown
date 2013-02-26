---
layout: post
title: "A reason to be sceptical of the long run defense of expected value"
date: 2012-08-02 16:48
comments: true
categories: philosophy decision-theory
---
Utility is, by definition, the sort of thing we should be trying
to get the most of.
That's what utility is: it's the thing you want to have.
But why should you act to maximise *expected* utility?
One response to this question is to argue that in
the long run, this strategy is best.
I want to suggest that there's a reason to be wary of this argument.

<!-- more -->

"Imagine" says the EU proponent "that the decision is
repeated infinitely often."
OK, there's already some heavy duty weirdness with
infinitely repeated decisions, but that's not really my target
today.
Let's just take this point for granted.
"In the limit, always acting to maximise expected utility
comes out as the best policy."
This is just the 
[Law of Large Numbers](http://en.wikipedia.org/wiki/Law_of_large_numbers)
in action.

"But imagine" responds the recalcitrant anti-EU theorist,
"you have a lottery with a million tickets and the prize is
a million Euros.
The decision is to take the lottery or to take a sure 99 Euro cents."
It will probably be a long time before the EU theorist's superior strategy
takes effect.
The lottery option will have a much higher variance 
(indeed, any lottery will have a higher variance than a constant act).
So that EU theorist will spend at least some time floating around underneath 
the constantly growing wealth of the sure-option-taker.
Both agents' wealth tend to infinity,
but in the limit, the lottery chooser's average gain is higher.
However, the lottery chooser's gain is a lot more varied:
sometimes (most times) nothing, occasionally a big win.

But the claim is that eventually the EU theorist will
come out on top, almost certainly.
I don't think this is a good argument.
Let me show you why.
Consider another lottery where the options are
the two options we had before and a third option:
pay 10 Euro cents and get punched in the face.
This is obviously a terrible idea.
But here's the deal:
there are other policies
that do as well as choosing the lottery in the limit
that are clearly stupid.
Consider the following strategy:
"Choose the lottery, except on the 7th
repetition. 
On repetition 7,
pay to get punched in the face."
In the limit, the lottery choices will
wash out any disutility from
getting punched in the face.
Or consider "Get punched in the face 100 times,
then choose the lottery".
Indeed, any initial segment strategy gets washed out in the long run
provided the long run strategy is to choose the lottery.
Infinity is a funny beast like that.
This seems super weird,
since in practice all we ever accomplish
is some particular initial segment of our infinite strategy;
because, y'know, real agents tend to die.
So the point is that the argument for maximising EU
also justifies these crazy strategies.

The EU fan might respond 
"No, you have to choose the same act each time."
But this isn't a particularly convincing response.
First, why should we rule out acts where we can change what we do?
Second, what counts as an act?
Is "If you haven't been punched in the fact 100 times yet,
do that. Else lottery" an act?
If so, then the objections stands.
If not, why not?

You may have noticed that this objection
relies on the limiting behaviour of the strategy.
But so did the original defense of EU theory,
so I don't take that to be a criticism of the strategy.
That said, EU theory doesn't do all that well
with infinities anyway,
so maybe we should have expected trouble.
There's the famous
[St. Petersburg Paradox](http://plato.stanford.edu/entries/paradox-stpetersburg/)
which shows how EU theory doesn't deal well with infinity.
Then there's Nover and Hájek's 
[Pasadena game](http://scholar.google.co.uk/scholar?hl=en&q=pasadena+game)
and friends.
These are variations on the theme of the St. Petersburg game
that show how bad things can get.

A version of expected utility theory that might be 
immune to the above criticisms is Mark Colyvan's
[Relative Expected Utility](http://philpapers.org/rec/COLRET) theory.
This is a theory expressly developed to deal with the sort
of problems that St. Petersburg and friends bring up.
It also does well at responding to the line of argument
I was suggesting above:
since the lottery strategy
"dominates" the get-punched-then-lottery strategy,
REU prefers the former.
By "dominates" in this context I mean that if you look at each repetition
of the decision,
the difference in utility between the acts
always favours the simple lottery strategy.

But this isn't really the end of the story.
Colyvan defends his REU theory by arguing that it is a conservative extension of
EU theory (meaning that they coincide for finite decisions).
But in the current case, EU is on trial,
so we can't use the REU defense for the infinite case
since that would be circular.
Perhaps we could "kick away the ladder" and try to look
for a first-principles defense of REU.
This doesn't look promising:
if I am sceptical of maximising probability weighted utility,
I am going to be just as sceptical of having my preference
accord with probability weighted utility differences.
Colyvan's theory has some extra limitations too:
it only works for pairs of acts
(and probably leads to cyclic preference in some cases
of more than 2 acts).
It also builds in state independence, 
which is a controversial assumption in standard EU theory.
So I don't think this offers a way out.

Is there a better defense of EU theory?
I can't think of one off the top of my head.
Answers on a postcard.

This post was inspired in part by reading
Lara Buchak's 
[Risk Aversion and Rationality](http://philosophy.berkeley.edu/file/755/Buchak_Risk_Aversion_and_Rationality.pdf).

### Edit

Thinking about this a little more I realised that
there is another argument for expected utility theory.
This is the famous representation theorem.
That, however, is a topic for another time.
(I also fixed some typos and changed the phrasing in a 
couple of places.)
