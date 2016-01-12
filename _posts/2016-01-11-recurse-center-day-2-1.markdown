---
published: true
title: Recurse Center, Day 2.1
layout: post
---
(I wanted to label this as "Day 2-1," meaning week two, day one, but using a "-" in post titles crashes TinyPress... which I should know already, since this happened when I tried to write my entry for "Day -3". I hate to use a decimal point, since that implies it's base-10, but oh well.)

I was going to write something more philosophical, involving an extended analogy to both marathon training and capital allocation, but am absolutely bankrupt of energy. So instead I will write more factually. I sat down with J. to discuss my failure to solve problem #7 of the [99 Problems in Haskell](https://wiki.haskell.org/99_questions/1_to_10) (which, by the way is REALLY FRUSTRATING, since on a conceptual/algorithmic level, it’s not at all challenging, and I could write the solution to the problem in Python USING ONE OF THOSE MORSE CODE TELEGRAPH TAP-TAP-TAPPERS). J. doesn’t really know Haskell (despite being European. All the European coders I know seem to be fluent in Haskell), but he’s pretty good in Scala, which is also functional, and so somehow after half an hour of effort we managed to get my solution working. I still have no idea how. I mean, I know how it works, I just… it felt more like a case of blindly making some keystrokes that happened to compile. What on earth did I do differently today that I didn’t do in the last several days of struggling off and on with this problem?

Here is the (god, so embarrassingly short) code:

    data NestedList a = Elem a | List [NestedList a]
    flatten :: NestedList a -> [a]
    flatten (Elem x) = [x]
    flatten (List []) = []
    flatten (List xs) = foldr (\x acc -> (flatten x) ++ acc) [] xs

Haskell requires that lists have all elements be of the same type, so even something as simple as a nested list requires a special construction. E.g., `[1,2,3]` is a valid list in Haskell, but even `[1,2,[3,4],5]` isn't–it contains as elements both numbers (`1`,`2`,`5`) and lists (the list `[3,4]`). Note how we define our custom `NestedList` type recursively (i.e., a `NestedList` is something whose elements are either elements of type `a`, or lists of other `NestedList`s). 

One of the many difficult things about Haskell is that it’s “strongly typed,” i.e., you have to tell Haskell what kind of variable every variable is (is it a string? is in an integer?). That by itself isn’t so bad, but this obsession with ALL THE TYPES MUST BE PERFECTLY CLEAR ALL THE TIME goes pretty deep. Every time you make a function, you have to tell Haskell what kinds of variables it takes as inputs and what kinds it takes as outputs, and even though you can get a bit generic (i.e., “this function takes as input variables of type `x` and returns a list of `x`s”), the effect is like putting on what you think looks like a raincoat but is in fact a straitjacket.

In theory it doesn't sound bad at all. How hard can it be to just be diligent and orderly about your types? In practice...

On the plus side: I’ve basically never made syntax errors in Haskell! In fact, of all the errors I frequently make in Python or Javascript, all but one of them I never make in Haskell! On the minus side: EVERYTHING IS A TYPE ERROR, ALL THE TIME.

Here is an example error message from `ghc` (the Haskell compiler), lightly edited for readability:

>“You’re telling me that I’m supposed to check whether `x>y`–well, how do I know that I can do that? What if it turns out that when you finally fill the variables in, `x` and `y` are my children, and by `x>y` you’re asking whether I love `x` greater than `y`? Don’t you realize the position you’d be potentially putting me in? You’d be forcing me to say that I loved one of my kids more than the other! So no, I won’t tell you whether `x>y` unless you assure me that `x` and `y` are things I’m okay comparing (and that I’m comparing them in a way that I’m OK with). Like if `x` and `y` are numbers, and `>` is normal integer comparison. I’m OK with that. But you have to promise me that that’s all you’re asking for.”

[Philip Guo](http://www.pgbovine.net/) gave a talk at RC today, about his research (as a CS prof at Rochester) on creating online learning environments for coding. I’ve read his blog off and on for a while–it’s so humane–and it turns out he’s an RC alumnus, having taken three months off his postdoc to attend.

I walked out to the Hudson to watch the sun set. The sunset was beautiful–even more beautiful than sunsets usually are–but what was REALLY beautiful, and quite a bit more unexpected, was the westernmost building on Canal Street. Block after block of generic Lower Manhattan streetscape, and then all of a sudden this GIANT WINDOWLESS CONCRETE GEOMETRIC PRISM, lit up (LIKE A TEMPLE) from below. [Apparently it’s a storage building for the NYC Department of Transportation’s road salt](http://www.nytimes.com/2015/09/17/nyregion/a-building-that-resembles-what-it-stores-salt-for-new-york-citys-roads.html). The building itself is supposed to resemble a giant cube of salt. It’s GORGEOUS. I love concrete buildings, and this is just… amazing. None of the pictures on the internet really do it justice. At night–the way it was lit up–I’ll have to bring my camera by and take my own picture.