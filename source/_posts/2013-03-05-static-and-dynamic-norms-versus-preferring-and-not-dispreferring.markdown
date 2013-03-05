---
layout: post
title: "Static and dynamic norms versus preferring and not dispreferring"
date: 2013-03-05 16:02
comments: true
categories: bayesianism 
---
I've been thinking about rationality requirements for sequences of choices.
It seems there's a sense in which some synchronic (static) norms
are justified by related diachronic (dynamic) norms.
I recently hit an interesting snag in this picture.

<!-- more -->

So let's think about the package principle.
This is an important part of the Dutch book theorem.
The package principle says that (in effect) if you prefer
bet A to bet B and you prefer bet C to bet D,
then you should prefer the set of A and C to the set of B and D.
Dutch book results work by making nonprobabilistic agents take sets of bets
guaranteed to lose them money.
So agents need to have consistent attitudes to sets of bets to make it work.
As a static principle, it is a little artificial.
This is a point that [Schick](http://philpapers.org/rec/SCHDBA) makes.
The principle seems to be motivated by a *dynamic* principle that says that
if you're offered the bets in sequence,
your preferences among bets shouldn't be sensitive to what bets you've already taken.
This is just avoiding the fallacy of the sunk cost, I guess.

The motivation goes like this:
say you preferred A to B and C to D as before.
Now if I offered you the choice between A and B,
you'd choose A.
It seems that if I now offered you the choice between C or D,
you should still go for C.
That is,
having chosen A shouldn't affect your preferences among bets.

I'll come back to the package principle in a moment,
but let's consider another example of a static principle motivated by dynamic concerns.
Think about arguments against having cyclic preferences.
If you had cyclic preferences, that is $ a \succ b \succ c \succ a$,
then you could be money-pumped.
Let's say the letters stand for Apple, Banana and Carrot.
If you had a carrot, I could offer to exchange your carrot for a banana.
Since you strictly prefer the banana, you would be willing to pay me for the privilege of trading up.
Now I offer you an apple for your banana, likewise, you'd pay to trade up.
But you also prefer carrots to apples, so again you'd pay me to trade up to the carrot.
Now you are back where you started except that you paid me for each exchange.
You have been money-pumped.
Not that the money pump involves offering trades in sequence.
Thus acyclicity -- a static condition on preference --
is motivated by appeal to sequences of choices.

OK, back to the package principle.
Here's a very similar argument to the one dynamic one above,
but the static condition it seems to motivate is unreasonable.
Say you don't disprefer A to B and you don't disprefer C to D.
We're imagining agents who can have incomplete preferences, here.
Say you had imprecise beliefs and the expectation intervals for A and B overlapped.
Now, if you were offered the choice between A and B,
on a reasonable interpretation of what's permissible given incomplete preference
we could say that it's permissible for you to choose A.
Now if you were then offered the choice between C and D,
it should still be permissible for you to choose C.
The static principle that this line of reasoning seems to motivate, however,
is not a good one.
Consider, for example, the "great set of bets" that 
[Adam Elga](http://www.princeton.edu/~adame/papers/sharp/elga-subjective-probabilities-should-be-sharp.pdf)
offers.
He first offers you the lottery "-10 if H, 15 if not-H" then he offers you the lottery "15 if H, -10 if not-H".
If these are A and C respectively (where B and D are both the "status quo"),
then it should be clear that you should never choose to refuse both bets.
Now if you have imprecise credence in the proposition H, 
it may be that you have no preferences between A and B nor between C and D.
Thus it is permissible that you accept B, and also that you accept D.
But in the static choice between AC, A, C and the status quo, you would never
opt for the status quo.
So what has gone wrong?

To recap, it looks like the method for justifying static principles of choice through
dynamic considerations has led us to a static principle we would want to reject.
Does this cast doubt on the method as used in the previous cases?
Or is there something weird about the relation of "not dispreferring" and the
concept of permissibility derived from it that makes the method inapplicable?
I don't really know what to say about this case yet.
Katie Steele and I have been working on a [paper](http://www.seamusbradley.net/Papers/elga.pdf)
on this topic.

