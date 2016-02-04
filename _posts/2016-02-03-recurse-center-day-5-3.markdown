---
published: true
title: Recurse Center, Day 5.3
layout: post
---
Yipes. Week five?!? That's terrifying. I should remind myself that this isn't the U of C, and the relevant unit isn't the ten-week quarter but RC's twelve-week batch. Still. Eeep. 

I wrote code today! This really SHOULDN'T be something to be pleased about, but, goodness. I started off the day still trying to poke around in Clojure, and feeling less intimidated than Haskell (it's hard to get intimidated by a language whose only syntax is parentheses!), but still not really able to just DIVE IN and start writing and PLAYING AROUND. I'm still set (wrongly?) on this idea that I should write a symbolic differentiator as a "fun and easy first functional programming project." I have a rough sketch of how they work (parse! pattern match! recur! [0] un-parse!), but it's just a sketch, not a finished mental painting. So I am/was faced with the difficulty of 1) implementing an algorithm I don't fully understand 2) in a language I don't fully understand. (Or rather, in a language I don't understand well enough to play around in.)

So, in an attempt to write SOME CODE, I started writing it in Python. I know Python well enough to sketch! And I spent a couple hours trying to implement a parser. I eventually got it to more-or-less turn input like `a+b*c` into an [S-expression](https://en.wikipedia.org/wiki/S-expression) like `(+ a (* b c)` (or the Python equivalent, in a nested list), but what a disaster. God. I've written parsers once or twice before, and... it always seems like it should be so straightforward. And yet it always becomes such a disaster so quickly. Lost in a nightmare forest of `if`-`then` statements ([this kind of forest](http://fusion.net/story/252500/japan-suicide-forest-sea-of-trees-aokigahara-mt-fuji/))). Ugh. 

Maybe I should have asked someone what a fun and easy first functional programming project might be. Someone who actually knows what they're talking about. Oh well. 

With the goal still in mind of "FOR GOD'S SAKE ANDREW JUST WRITE SOME CODE", I decided it'd be better to just try to write the FUN parts of the symbolic differentiator, i.e., the pattern matching and the recursion! And after a couple hours of slightly messy but moderately fun and reasonably straightforward work, I had a working prototype! So I was able to take a high-school-math function like this:

    ax^5 + x*sin(2x)

at least in its hand-parsed form:

    [ '+', ['*', 'a', ['^','x','5'] ] , ['*', 'x', ['sin',['*','2','x']] ] ]

and "calculate" (too strong of a word; all I'm doing is dumb pattern-matching) its derivative:

    ['+', ['+', ['*', 'a', '5x^4'], ['*', 0, ['^', 'x', '5']]], ['+', ['*', 'x', ['*', ['cos', ['*', '2', 'x']], ['+', ['*', '2', 1], ['*', 0, 'x']]]], ['*', 1, ['sin', ['*', '2', 'x']]]]]

and then un-parse into something ugly but readable:

    (((a*5x^4)+(0*(x^5)))+((x*(cos(2*x)*((2*1)+(0*x))))+(1*sin(2*x))))

(Of course un-parsing it takes like two lines of code, whereas parsing it takes... a zillion. Not exactly P vs. NP, but still, talk about directional asymmetry.)

Hooray! I guess! I mean, I feel deeply guilty for using Python, because even if I (hopefully? maybe? wishing?) write a Clojure (or Haskell? please?) version, I'm terrified I'll be corrupted for already having written it in Python, and will fall into the fallacy of trying to write Python with Clojure syntax! Which is obviously very differently than actually THINKING in Clojure (or Haskell) and solving the problem in the way Clojure wants me to solve it. (If you literally translate a poem from Persian into English, you haven't translated it: you've preserved the literal meaning and lost the music.)

Anyway, I didn't write it out particularly extensively; I only implemented a handful of functions, just to get a sort of smallest-possible-prototype working. The core is the recursivey pattern-matching: it recursively trawls through this tree, differentiating branches until it can't anymore, which looks something like this:

    bigDictionaryOfOperations = {
        ... blah blah blah
        '*' : lambda (a,b): return [ '+', ['*',a,differentiate(b)], ['*',differentiate(a),b] ]
        .... that was the product rule, blah blah blah ...
        }

And then we actually do the diff:

    def differentiate(expression):
        fxn = bigDictionaryOfOperations[expression[0]]
        argument1, argument 2 = expression[1], expression[2]
        return fxn(argument1,argument2)

Where the input expression is something like this (possibly arbitrarily nested):

    expression = ["*", "5", "x"]


It's probably not tail-call optimized, blah blah blah, whatever; I barely know what that means anyway. And I guess you can't do that at all in Python. Er, that probably comes off sounding a bit apathetic; I've just been minorly annoyed, off and on, at struggling to come up with solutions to problems, only to be told by Europeans (who seem to all learn functional programming at the age at which American children learn BASIC)(is that racist? that's probably racist.) that such-and-such isn't a very efficient solution. Well, I don't care if it's an efficient solution! I just want ANY solution, and I'll worry later about making it more efficient! (I should use [bit diddling](https://en.wikipedia.org/wiki/Bit_manipulation)? I'll diddle YOUR bits!)

Anyway, I toyed with the idea of implementing as few differentiation rules as possible (so that, e.g., it would try to evaluate `x^45` by applying the product rule over and over and over), and I might still do that for fun, but as it is I hard-coded a few endpoints. The differentiation function stops when it sees a string rather than a list (not shown above), so, e.g., the power rule pattern-matcher returns:

    '^': lambda (a,b): return str(b) + str(a) + "^" + str(int(b) -1)

I guess I'll need to fix that at some point to support arbitrarily-exponentiated expressions.

L. and I had [beer and brownies](http://westendhall.com/) on the UWS tonight. On Monday A. and I had lunch at [Charles' Pan-Fried Chicken](http://www.newyorker.com/culture/culture-desk/fried-chicken-king-harlem) in Harlem, which despite having a New Yorker review is still an invisible hole-in-the-wall [1], had amazing fried chicken, and THE COLLARD GREENS. Oh my goodness, the COLLARD GREENS. I have no idea what they put in them. I HAVE NEVER HAD SUCH GOOD COLLARD GREENS IN MY LIFE.

Yesterday I went to the MoMA's Picasso sculpture show, which was just as amazing as everyone LINK says LINK it is. So many of the sculptures are so amazingly cubist! Like, they look EXACTLY like what you would expect three-dimensional versions of his painting would be! A lot of the later stuff (e.g., this awesome gorilla) are made partly or entirely out of found objects: Picasso was the original junk sculptor!! He did a plaster bas relief of a head that looks almost exactly like a Roman/Greek artifact, except that the head isn't ENTIRELY in profile. The other eye and the nose are sort of pulled around to the front. They're not pulled around enough so that it's obviously some weird cubist thing, but enough to make you take a second look–subtle, but not TOO subtle, like Picasso is genuinely trying to imitate these classical works, but is pathologically incapable of being flat. 

I found myself particularly struck by a [sculpture of a duck](https://news.artnet.com/wp-content/news-upload/2015/09/bird-2.jpg). Objectively speaking it wasn't particularly interesting aesthetically or technically: it was just a piece of wood, cut out into the 2D profile of a duck in flight, painted, and with a screw eyelet for an eye and forks for legs (which are stuck out as if it's walking), yet I couldn't stop looking at it. Maybe it's because I was already in a wistful mood, but eventually I looked in the catalog and saw that it's in private hands, and I was even more entranced. I'll probably never see this duck again. 

Tim Ferriss, on an [unusually good episode](http://fourhourworkweek.com/2015/12/14/derek-sivers-on-developing-confidence-finding-happiness-and-saying-no-to-millions/) of his (surprisingly) good podcast (which I'm still embarrassed to admit I listen to), remarked: "Most people overestimate how much they can get done in a day, but underestimate how much they can get done in a year."

---
[0] It's still not clear to me what the verb form of "recursive" should be. Some people use "recurse," but that's [back-formy](www.nytimes.com/2006/01/29/opinion/29iht-edsafire.html‎); other people use "recur," which seems more grammatical, except... I really like the sound of the "s" in "recursive." The "s" and the "v" together. :/

[1] Yipes, metaphor clash. What I meant was, it seems to have this incredible reputation online (Yelp! the N'Yorker!), and yet I missed it the first time I walked by it: it's tiny, dirty, unremarkable, and looks exactly like every other tiny take-out place in a poor neighborhood. And vacant: A. and I were the only people there, at like noon.