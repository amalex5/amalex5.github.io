---
published: true
title: Recurse Center, Day 4.4
layout: post
---
I got a working implementation of Tetris-on-polar-coordinates running this morning! Sort of, at least. You can't actually *play* Tetris. But you can watch as the computer randomly drops Tetris blocks one-by-one, and watch as they fall down and accumulate at the pole of the graph!

The demo was (to my surprise) really popular. I didn't officially demo it; I just had the auto-Tetris open on my screen and running in a loop while I was pondering what to do, and people kept asking what it was and saying how pretty it looked. I think it looks mildly cool, but I'm genuinely surprised how much people seemed to like it. Maybe it's because it's a tangible (visible) thing, and so much of what people are working on either have intangible results (or results that are less visually exciting), or they're so far away from having any sort of tangible thing that my silly/simple Tetris implementation is exciting. I'm not sure.

Speaking of which: tonight's presentations were really cool! There's an hour on Thursday nights at RC set aside for five-minute presentations: demos of what you've been working on, explanations of some cool topic, etc. The last few weeks there haven't been many presenters. But tonight there were a bunch! Mostly people's demos! S. has been writing an operating system (!), and explained some weird data structure that she had to figure out in order to allocate memory. J. and F. have been trying to program RC's resident Commodore 64 (!), from assembly (I guess?), which is so rudimentary that they need to take the mechanics of the CRT screen into account (i.e., how it scans line-by-line and left-to-right). But they somehow got it to display a bitmap image of the RC logo, accompanied by awful 8-bit 1980s electronic music. H. is writing her own shell, and talked about process threading. 

Not everything is so technically intimidating: L. has been creating a rainfall API! NASA apparently has daily satellite imagery of the entire globe dating back three decades that, somehow, can be used to measure precipitation (not clear whether this was the point of all the imagery, or whether it just turned out that way), and so L. (who is like a genetics PhD, and two years younger than me, and British) scraped all of the imagery, processed it, stuffed it into a database, and turned it into a public API with a nice accompanying website. So a good project for dipping a little bit into lots of different common web technologies! 

S. (a different S. [1]) attempted to explain [monads](https://en.wikipedia.org/wiki/Monad_(functional_programming)) in five minutes. He even wrote out really nice slides. But it immediately devolved into an (unintentional but welcome by all) standup routine. I can't even try to describe it. The room was in stitches. His attempt to explain some sort of algebraic property of monads went like this:

>*So, um, `maybe` is a monad. Like. Like if I say I might have a coin in my hand. Right? Which means there might be a coin in my hand, or there might not be a coin in my hand. And if I say I might have a box in which there might be a coin in my hand, that just means I might have a coin in my hand. But if I say I might not have a coin in my hand, then I've said nothing.*

I guess you had to be there.

---------------
[0] It wasn't in S.'s presentation, but S. is writing their OS in [Nim](https://en.wikipedia.org/wiki/Nim_(programming_language)), which I've never heard of, and which has resulted in S. having a second clock on her menu bar set to GMT+0100, so that S. can know what time it is in Berlin and thus whether Nim's creator is likely to be on IRC and able to answer S.'s many questions.

[1] I don't know what to do about first initials. Too many people I know have the same first initial! Sometimes I've just made up initials when they've resulted in ambiguous text; other times, I've silently chosen the last initial. Argh. I wonder what the distribution of first (last) initials is among people I know. I wonder how hard it would be to pull that data off the Facebook API. 