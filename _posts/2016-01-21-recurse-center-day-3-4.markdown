---
published: true
title: Recurse Center, Day 3.4
layout: post
---
I demo'd my 2-D Tetris implementation at the Thursday night talks tonight! Antecedently, I also got enough of it working to do the demo. 

What I said was something like this:

>So I was trying to learn Haskell, but it was making me feel really sad, and it was making me feel really stupid [*inexplicable laughter*]. And so I thought I should take a break and do something that made me feel less sad and less stupid. [*saying all of this while live-playing 2-D Tetris on the projector*] And so I thought, I'll write some dumb thing in the browser with JavaScript. And I thought, I'll write an implementation of Tetris! But then I thought: why not write an implementation of Tetris that has blocks flying in FROM ALL FOUR SIDES?!?!
>
>[*still demo'ing 2-D Tetris live on the projector*] This is all in plain JavaScript, without even jQuery. I'm not even doing this in `canvas`. These are just `div` elements that I'm turning white or black. So I had to write all the logic by hand and write all of these tedious helper functions to do really basic animation tasks. So it was a lot of WORK, but basically zero intellectual work. The exact opposite of Haskell. [*laughter*] And that's exactly what I wanted: 
>
> The one vaguely interesting part turned out to be this: so in normal Tetris, you drop pieces from above, and when they form a solid line, the line clears and everything moves down one. In this version, you try to form a rectangle around this center piece [*showing demo*], and then THAT clears. And in my vague inchoate [*I actually said the word "inchoate" out loud!*] conception of this game, I'd just shift all the cells inward towards the center [*showing sketch of my vague mental conception of how this would work*]. But actually, there's a problem.
>
> So the inner ring of cells around the nucleus–there are nine of them. [*showing picture*]. But the ring of cells around THAT–well, there are fourteen of them. [*showing picture*] So you clear the inner ring of cells, and you want to move these guys inwards–but how do you do that? How do you fit fourteen Tetris blocks into nine empty spaces?
>
> You can't do it. The problem is that the Tetris board is discrete, not continuous. If it were continuous you could just squeeze and smush things. Maybe if Tetris were some game that involved getting a total number of blocks or something, maybe we could average it or something. But Tetris is discrete. The presence or absence of a single block in a single location can make a HUGE difference. 
>
> So there's really no way we can clear the Tetris grid without creating some sort of discontinuity somewhere. Oh well. What I ended up doing was, you flip a coin, and if it's heads, all the pieces move in vertically towards the center, and if it's tails, they all move in horizontally to the center. So either the line of blocks in the horizontal middle gets erased, or the line of blocks in the vertical middle does. We're TEARING the fabric of TETRIS!
>
>[*thunderous, sustained applause*]

This was fun. I really like public speaking, but I've been doing so little of it recently. (I really like *communicating* in general.) It's also something I'm really good at. The more fun you have doing something, the better you get at it; the better you are, the more fun it is. The advice I've given a couple of people about writing in the last year is to HAVE FUN. (This isn't the writing advice I would have given a few years ago.) You don't think you're a good writer? Don't try to be a better writer: try to *enjoy* writing more! Do that, and it'll follow that you'll become a better writer.

Afterwards, in conversation with a few people, we solved my discontinuities problem. So, OK, you can't play 2-D Tetris on a flat plane. BUT WHO SAYS PLANES HAVE TO BE FLAT?!?! What if you played it on a CONE?!? (Or, equivalently, on a polar graph?) The tip of the cone is the accumulation point; pieces start on the wide-open part of the cone, and fall towards the tip. You have one set of longitudinal grid that radiates out from the tip, and a set of latitudinal lines in the other direction. So the cells might get smaller as they get closer to the tip, but they'll always be the same NUMBER of cells. So you can play Tetris much more cleanly.

I like this! I bet the polar graph version wouldn't be too hard to make! I'd have to use something slightly more sophisticated than "lay out a bunch of `div`s in a grid." Maybe I could use D3! D3 is fun.

Today at lunch, lying on the table were two copies of [a book written by the husband of the grad student I TA'd for eight years ago](http://www.dabeaz.com/per.html). (Actually, according to Google, he's now her ex-husband.)