---
published: true
title: Recurse Center, Day 7.2
layout: post
---
Yesterday I wrote about how much I loved Erik Meijer's multiple choice questions in his [EdX Haskell course](https://www.edx.org/course/introduction-functional-programming-delftx-fp101x-0). But I wrote in the abstract. Today, I'll write concretely, and give an example!

Here's a good one. One of the questions in the problem set I did this morning was to select all the valid definitions of the function `all`, which maps over a list and returns `True` if every element of the list satisfies some given predicate. (Javascript has this as `Array.every()`; [Python has it as `all(iterable)`](https://docs.python.org/2/library/functions.html#all).) Here are the possibilities, and my comments:

- `all p xs = and (map p xs)` (yes! and this how I would do it.)
- `all p xs = map p (and xs)` (nope! wrong order. thanks to Haskell's type-checking, it won't even compile: `and` takes a list of booleans and returns a single boolean, which means that it'll pipe to `map` a single element, instead of the list that GHC expects.
- `all p = and . map p` (this works! the `.` composes functions without needless parentheses. note this example doesn't even need to include the object of `and`!)
- `all p = not . any (not . p)` (instructively verbose, but works! I guess this is basically a Haskell example of [De Morgan's laws](https://en.wikipedia.org/wiki/De_Morgan%27s_laws) or one of those other boolean algebra distribution laws.)
- `all p = map p . and` (nope! this doesn't work because... uh, because `and` returns a singleton, not a list. out of order.)
- `all p xs = foldl (&&) True (map p xs)` (yes!!! and I am really excited to talk about `fold`ing in a moment.)

Actually, no, let me talk about `fold` right now. `fold` is awesome! It's like a generalization of `map` (and `filter`, and `reduce`, and all those other functional/iterable tools!). So the idea is that if you have a list (or, more generally, some recursive data structure), and you want to apply a function over that list, and you have some initial value... and, um, well, I can't explain this very well, which means I must not understand it very well, but the point is, it's like the logical grandparent of `map` and `filter` and `reduce`!

Definitions aren't explanations, but here you go. So say you have some function `f`, some initial return value `z`, and some list. We'll define it in the normal, piecewise Haskell way. 

If the list is empty, we define `foldr` to be just our initial return value `z` (the recursive base case):

    foldr f z [] = z

If not, we define `foldr` as: we apply `f` to the first element of the list, and call `foldr` again on all the remaining elements of the list, together with our accumulated accumulator:

    foldr f z (x:xs) = f x (foldr f z xs)

Uhh, let's do an example. Actually, we should have STARTED with an example. But if I try to EDIT these posts and make them nice, I won't actually get them finished.

Anyway, as an example, let's show how we can define the `sum` function using `fold`! So `sum` will take a list of numbers and add them all up, and we can define it like so:

    sum x  = foldr (+) 0 x

It's so easy! So, um, let's demonstrate by calling this on the list `[1,2,3,4]`:

    foldr (+) 0 [1,2,3,4]

So, by our definition of `foldr`, this is equal to:

    + 1 ( foldr 0 [2,3,4] )

which is:


    + 1 ( + 2  ( foldr 0 [3,4] )  )

By the way, note that this is addition in [Polish notation](https://en.wikipedia.org/wiki/Polish_notation), so like `+ 2 3` is `5` (the operator sign comes first rather than being in between (*prefix* rather than *infix*)). Anyway, continuing to expand the recursion:

    + 1 ( + 2  ( + 3 (foldr [4]) )  )

    + 1 ( + 2  ( + 3 (+ 4 (foldr []) ) )  )

And now we can finally use our base-case definition of `foldr` (i.e., that `foldr f z [] = z`):

    + 1 ( + 2  ( + 3 (+ 4 0 ) )  )

And of course in normal notation this just works out to be `1+2+3+4+0`, or `10`. Anyway! That's `foldr`! (BTW, if you Google that definition of `sum`, you get lots of people whining about how it's not tail-recursive and if you try to sum sufficiently long lists you'll get a stack overflow. Whine, whine.)

Folding is awesome! Here's [Wikipedia's definition](https://en.wikipedia.org/wiki/Fold_(higher-order_function))

> In functional programming, `fold` – also known variously as `reduce`, `accumulate`, `aggregate`, `compress`, or `inject` – refers to a family of higher-order functions that analyze a recursive data structure and through use of a given combining operation, recombine the results of recursively processing its constituent parts, building up a return value. Typically, a `fold` is presented with a combining function, a top node of a data structure, and possibly some default values to be used under certain conditions. The fold then proceeds to combine elements of the data structure's hierarchy, using the function in a systematic way.

Anyway, on to the next few possible answers to this multiple choice question (which was, remember, about defining `every`. Here's another possibility:

- `all p xs = foldr (&&) False (map p xs)` (Nope! This will never work, because if `false` is our base value, there's nothing we can `&&`/conjunct to it to make it `True`! (The boolean equivalent of multiplying by zero!)

- `all p = foldr (&&) True . map p` (This works! And it's a very nice example of using `fold` and the `.` composition operator!)

--------

Somewhat related to all the above: As an impulsive exercise tonight I wrote a quick implementation of a (pseudo) hash table class in JavaScript, which, to my surprise a) was completely painless, and b) WORKED ON THE FIRST TRY. Ordinarily I wouldn't even TRY to make something work on the first try; it was just that I was writing it offline and only bothered to actually run it once I had finished writing it. But it worked flawlessly! It was ~30 lines long, which is about 25 more than the number of lines of code I've had work successfully on the first try in the past.

Anyway, i was explaining how it worked to K., and my (quick, hacky) hash function involved both `map` and `reduce`, which she hadn't seen before. "Oh! Oh! Awesome! Yes! I can explain that to you! `map` and `reduce` are the best!" And in a JavaScript console I gave a quick, example-driven introduction, that was surprisingly good, despite the extemporaneity!

I should do that as a five-minute presentation on Thursday: introduction to basic functional tools! I'm probably not going to have anything to demo. I feel a *little* bad doing presentations so often, but there's always tons of extra time (why? presenting is FUN! why don't more people do it?). I already know what I'll title it: "NEVER WRITE A FOR LOOP AGAIN."