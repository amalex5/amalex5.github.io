---
published: true
title: Recurse Center, Day 9.5
layout: post
---
I finished [Erik Meijer's wonderful Haskell MOOC](https://www.edx.org/course/introduction-functional-programming-delftx-fp101x-0)!!! There were a few things I skipped through towards the end, but basically, I did all of it. And it was wonderful! And I'm so much more excited and confident about/in Haskell! 

The last problem set was really fun: we defined a "[Rose tree](https://en.wikipedia.org/wiki/Rose_tree)", which is a tree data structure which, at each node, has a value, and an arbitrary number of subtrees. Then we made it into a [functor](https://en.wikipedia.org/wiki/Functor#Computer_implementations), which in this context basically means something that can be [folded](https://en.wikipedia.org/wiki/Fold_(higher-order_function)) over. Then we did some stuff with---wait a minute---is that you, [monoid](https://en.wikipedia.org/wiki/Monoid)?? I haven't seen you since algebra in 2009! Back then, you were a set coupled with an associative binary operation, and you had a strong sense of your own identity. And now you're more or less the same thing, except you're a fundamental type class in Haskell.

Anyway, I'm not explaining this well, but the clear implicit purpose of the problem set was to show how to attach things to Haskell's high-level type classes to get really powerful functionality really easily. E.g., we know how to map over lists, but more generally we have this type class `Functor` that consists of stuff that is "mappable," and so is we define a new data type, we can link it up to `Functor` and then get all of that ability. Yeah, I'm not explaining this very well, but the more I think about this problem set (and the ideas behind it) the more I like it. I guess I'll return to it in a future blog post!

Here's a question (or the preamble to one) from the problem set:

> It might be the case that we have a foldable data structure storing elements of type `a` that do not yet form a `Monoid`, but where we do have a function of type `Monoid m => a -> m` that transforms them into one. To this end it would be convenient to have a function `foldMap :: Monoid m => (a -> m) -> f a -> m` that first transforms all the elements of the foldable into a `Monoid` and then folds them into a single monoidal value.

Enough! I am so excited about Haskell---almost as excited as I am for this party at A.'s apartment that I'm leaving for right now.