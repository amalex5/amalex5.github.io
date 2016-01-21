---
published: true
title: Recurse Center, Day 3.3
layout: post
---
I was hoping to finish this stupid two-dimensional Tetris implementation today. Well, that didn't happen. I spent an hour or two in the morning writing the "clear a solid layer of cells" functions that I wrote about yesterday. Then I spent the afternoon chasing down bugs. Whack-a-bug. Ugh. The code is now long enough that it's beginning to collapse in on itself.

At least most of the bugs have been easy to find (even if their solutions have required annoying rewrites). But there's this one bug that's been cropping up off and on today that I'm going to have to fix tomorrow. Namely: one of the Tetris blocks won't move. The game is basically working, modulo one or two tiny things I haven't written yet. But there's this one particular block–the block that's just a solid rectangle, with no weird angles or things sticking out–and for some reason, whenever the program tries to "drop" it, it immediately freezes. Somehow it's triggering the same block of code that prevents blocks from flying off the screen or into each other. I have no idea why. 

None of the other blocks are creating the same problem. The ONLY difference is that this is the only block that doesn't have any blank spaces. Meaning, the L-shaped Tetris block, for example, I'm storing in an array or arrays that looks like this:

    [ [1,0,0,0], [1,1,1,1] ]

So the top row has one filled-in pixel at the top left, followed by three white pixels, and the bottom row has four filled-in pixels. The rectangular block that's causing the problem, though, is stored like this:

    [ [1,1,1,1] ]

It's only a single row, and it's all filled-in. But that's the ONLY difference. And, moreover, it USED to work! The program was dropping the rectangular blocks JUST FINE yesterday!

Argh. File this one under "problems that are neither inherently interesting nor teleologically useful."

The thing is, too, it's the PERFECT kind of problem to ask someone else for help with! This is EXACTLY what the social environment of RC is useful for–and what it's DESIGNED for. (Speaking of teleology...)

I went to a house show in Harlem tonight. It was full of Israelis.