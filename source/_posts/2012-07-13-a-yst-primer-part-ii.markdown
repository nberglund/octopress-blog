---
layout: post
title: "A Yst Primer: Part II"
date: 2012-07-13 18:31
comments: true
categories: yst-primer tutorial
---
Time for part two of the [`yst` primer](/blog/categories/yst-primer/) I started [here](/blog/2012/07/01/a-yst-primer-part-i/).
This time, we will see the basics of using string templates and 
yaml data to generate some funky lists.
I'm going to use a silly example, 
but it should be clear how to make this work for sensible
applications like keeping a list of publications
or what have you.

<!-- more -->

Before we continue, let's simplify the `layout.html.st` and
the CSS we inherited from the template site.
Here's a simpler `layout.html.st`.

``` html layout.html.st
<!DOCTYPE html>


<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>$sitetitle$ - $pagetitle$</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <link rel="stylesheet" type="text/css" href="$root$css/screen.css" />
  </head>
  <body>
    <div id="wrap">
      <div id="nav">
	$nav$
      </div>
      <div id="main">
	$contents$
      </div>
    </div>
  </body>
</html>
```

Next, let's replace that horrible messy CSS folder with this simpler
file:

``` css screen.css
#main {
width: 45em;
min-height:300px;
float:right;
}

#nav {
min-height: 300px;
margin: 2em;
width: 15em;
float:left;
}

#wrap {
width: 65em;
}

h1 { border-bottom: 1px solid black; }
```

This is very much *like* the earlier messy CSS,
but a lot simpler.
Obviously you'll want to modify this for your own use,
but it should be easier to modify the simple version than it
was the old multi-file mess.

Onto some new stuff now.
First, let's add another page to our site.
Open up `index.yaml` and add a new item:

``` yaml index.yaml
- url: index.html
  title: Home
  template: index.st
  
- url: beatles.html
  title: The Beatles
  template: beatles.st
```

Now let's make `beatles.st`:

``` text beatles.st
# The Beatles

Welcome to my Beatles site.
```

Running `yst` should update the site in the `site` folder.
There should now be a `index.html` and a `beatles.html`.
The navigation panel on the left should work to
move between them nicely.

Now things get interesting.
Let's write some information about the Beatles 
into a yaml file.
Here's a sample:

``` yaml beatles.yaml
- surname: Lennon
  forename: John
  instrument: Guitar

- surname: McCartney
  forename: Paul
  instrument: Guitar
  
- surname: Harrison
  forename: George
  instrument: Bass

- surname: Starr
  forename: Ringo
  realname: George Starkey
  instrument: Drums
```

Now, we want to translate this information
into something we can put on the website.
The first thing we need to do is tell `yst` that we
will want that data for our `beatles.html` page:

``` yaml index.yaml
- url: beatles.html
  title: The Beatles
  requires: 
    - listname.st
  data: 
    thebeatles: FROM beatles.yaml ORDER BY surname
  template: beatles.st
```

Don't worry about the `requires` line just yet.
Take a look at the `data` line.
We read the data from `beatles.yaml` into something
called `thebeatles`.
We read in *and order* the data.
That is, we have ordered the entries by the `surname` attribute,
and that is the order the items will be printed.

Now, when we want to use that data, 
we can use a slightly more complicated version of the things like
`$sitetitle$` and `$nav$` from before.
Let's move back to `beatles.st`:

``` text beatles.st
# The Beatles
Welcome to my Beatles site.
The Beatles were: 

$thebeatles:listname()$

```

What we have here is a template telling `yst` to 
read in the data from `thebeatles`
and then run each entry through the `listname()` function.
We tell `yst` that the page requires the `listname()`
function (that's what that `requires` line was for).
This way, `yst` will know to recreate the `beatles.html` page if
`listname()` changes.
Let's define the `listname()` function now.

``` text listname.st
 
- $it.forename$ $it.surname$ $if(it.realname)$ \($it.realname$ \)$endif$ *$it.instrument$*
```

Note that there's a blank line at the beginning of this file.
That's quite important as we'll see a little later.
So what this function does is tell `yst` how to
format each item.
We want to output this as a list,
so each item of `thebeatles` is going to be a list item.
We achieve this by using markdown syntax for unordered lists,
hence the dash.
(We need the blank line so that each new item appears as a new list item
on a new line.)
`it` is how to refer to the current item.
So `$it.forename$` tells `yst` to print the forename attribute of the first item.
Likewise for `$it.surname$`.

Then comes a clever bit.
We check whether the current item has a `realname` attribute
using the `$if(it.realname)$` part.
Only if this comes out as true is the next bit implemented.
This next bit (up to the `$endif$` prints the
real name.
Neat, huh?
I use this method with my list of papers:
if there is a `url` attribute, the paper title is a link to the file.
Finally we print the `instrument` attribute in italics.
Done.

This seems like an incredibly complicated way of generating
a simple list.
But it is also a *very* powerful way to do so.
We could have had other information on each Beatle
that doesn't show up here but that appears elsewhere.
Or we could use the same information to display things differently.
Let's say we wanted a list of Beatles broken down by 
instrument.
(A more serious case would be to group all your talks with the same title).

Let's go back to the relevant portion of `index.yaml` now.
We are going to extract the information from `beatles.yaml` again,
but instead of sorting by surname, we are going to group by instrument.
(We're also going to require a couple of new files, we'll
get to that in a minute).

```yaml index.yaml
 - url: beatles.html
  title: The Beatles
  requires: 
    - listname.st
    - sortinstrument.st
    - simplename.st
  data: 
    thebeatles: FROM beatles.yaml ORDER BY surname
    beatleinstruments: FROM beatles.yaml GROUP BY instrument
  template: beatles.st
```

You don't actually have to write the words `GROUP BY` in capitals,
but I think it helps keep clear what are the keywords `yst` is looking for.
Now let's add a new list to the `beatles.st` page.

```text beatles.st
# The Beatles
Welcome to my Beatles site.
The Beatles were: 

$thebeatles:listname()$

By instrument:

$beatleinstruments:sortinstrument()$
```

This follows the same pattern as before.
Now we need to look at what sophisticated clever stuff 
is going on in the `sortinstrument()` function.

```text
$if(first(it).instrument)$

- **$first(it).instrument$$endif$** *$it:simplename(); separator = ", "$*
```

Now, I have to admit I'm getting to the edge of my understanding of
what's going on here, so this may be a little bit of
a cargo cult programmer way to do this.
As I understand it, what `GROUP BY` does is
turn `it` from referring to a single entry at a time
into something that refers to a list of entries that
share the property we have grouped by.
So `first(it)` refers to the first item of the list of things sharing the
attribute.
In this case, it would be the first Beatle
having the instrument attribute guitar, say.
The conditional part of this template, then,
does the following:
when we get to a new instrument (when we hit the first
dude with a particular attribute) we add a new list item
and then we write the name of the instrument in bold.
That takes care of getting the instrument names written.
How do we write out the names of the people who have those
instruments?
Like I said, it looks like we have a list of entries
for each possible state of the `instrument` property.
Well, we already know how to get a list to print:
we run each element through a function.
In this case the `simplename()` function.
It looks like this:

```text simplename.st
$it.forename$ $it.surname$
```

So `$it:simplename()$` formats each member of the list `it` 
(remember, `it` is a list now, because of the grouping).
You could actually replace a small part of the `$listname()` function
by a call to `simplename()`. 
I'll leave that as an exercise.

Now let's imagine that you remember
a bunch of other people who you want to add to your list
of Beatles (I'm regretting not choosing an example where
it made sense to add a bunch of new items, but bear with me).

```yaml beatles.yaml
- surname: Lennon
  forename: John
  instrument: Guitar

- surname: McCartney
  forename: Paul
  instrument: Guitar
  
- surname: Harrison
  forename: George
  instrument: Bass

- surname: Starr
  forename: Ringo
  realname: George Starkey
  instrument: Drums

- surname: Orwell
  forename: George
  realname: Eric Blair
  instrument: Dystopian Novel

- surname: Clapton
  forename: Eric
  instrument: Guitar
```

Now all you need to do is run `yst` and the website has 
incorporated these two new secret Beatles.

Working out how all these little pieces fit together can be a little 
brainmelting, and it can seem like overkill.
In fact, in my case, it almost certainly is overkill.
But I hope to have shown you a little bit of the power of this system.
The beauty is that once you've set it up,
you'll only ever really need to add stuff
to the `yaml` files and `yst` will take care of the rest.

I have tarballed up the final version of the `basic` site
which should more or less match what I've described here.
You can get the tarball 
[here](/assets/basic.tar.gz).
