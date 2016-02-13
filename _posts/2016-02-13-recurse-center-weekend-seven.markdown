---
published: true
title: Recurse Center, Weekend Six!
layout: post
---
I love these multiple choice questions. I never thought I would say that. [0]

But the thing that's the best about [Erik Meijer's functional programming/Haskell EdX MOOC](https://www.edx.org/course/introduction-functional-programming-delftx-fp101x-0) so far (better, even, than Meijer's shirts) is that there are multiple choice questions. And lots of them. Here's an example:

> Which of the following implementations correctly define a function `halve :: [a] -> ([a], [a])` that splits an even-lengthed list into two halves? Choose all correct implementations!

Following the question are a dozen or so possible answers, some of which are valid and some of which aren't. And it's fantastic, because the answers show all the different ways you can (and can't) express the same meaning. You can express this `halve` function by pattern-matching (the preferred Haskell way)! Or you can use guards! Or you can use some embedded `if`/`then` statement! Or you can use some random embedded anonymous function! Or you can use the cool `cons` notation! And all of the answers that aren't correct–the way in which they're wrong is instructive! They give counter-examples to misunderstandings. 

Way too often in math/CS/physical sciences, we're so eager to talk about the truth that we forget to talk about the NOT-truth. We make the mistake of defining things only in terms of what they ARE, without defining them also in contrast to what they are NOT. From a logical perspective, that's fine; from a psychological perspective, it's terrible. We learn through contrasts! 

I'm getting drinks with B. and E. tonight, which will be fun not only because a) they're awesome and b) I haven't seen either of them in several YEARS, but also because c) they've somehow met and become good friends with each other! Which was unexpected, since B. is an Ithacan and E. is a Chicago kid.

-----
[0] At least not for a not-bad reason. The bad reason to like multiple-choice questions, and one I'm often guilty of, is that (as usually implemented) they're easy: the AP US History exam asks you what treaty settled the current southern border of the US in Texas, and even though you'd never be able to come up with the answer on your own, you know it's not the "Louisiana Purchase" or the "Treaty of Ghent," and so it must be the Spanish-sounding "Treaty of Cahuenga" or the "Treaty of Guadalupe Hidalgo," and the latter sounds more familiar, so you choose it, and get the right answer.