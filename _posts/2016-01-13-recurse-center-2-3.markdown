---
published: true
title: Recurse Center, 2-3
layout: post
---
I did something today! SOMETHING! I mean, not much, but something!

Somehow I managed to get myself to start writing a silly Javascript implementation of [the Game of Life](https://en.wikipedia.org/wiki/The_Game_of_Life). This is hardly original, and I'm sure that had I not prevented myself from Googling it I would have found a hundred far better implementations. But that's okay! I figured that it was something that's not only conceptually simply (i.e., the game of life algorithm), but also requires tools that I know how to use (i.e., I'm perfectly comfortable in HTML/CSS/JS and using the DOM). It took several hours, but it was just *work*–no actual thinking. Which was perfect. 

I had lots of ideas for how to make it visually more attractive and cooler than a normal game of life implementation, although I didn't have the time. The one thing I did do that's a bit nonstandard is have the live cells be white, and the dead cells be black. This makes more sense: light is life, and death is darkness! ("O dark dark dark. They all go into the dark. The vacant interstellar spaces, the vacant into the vacant ... And cold the sense and lost the motive of action." ([East Coker](http://oedipa.tripod.com/eliot-2.html))

The interface controls are really rudimentary. Oh well. I wish you could drag to kill/resurrect the cells, but I'm not sure how dragging events work in HTML5, and it's already almost 10. It's also DREADFULLY SLOW on the ArchaeoBook; I think this is less a function of the ArchaeoBook and more a function of my inefficient algorithms and the general slowness of [DOM](https://en.wikipedia.org/wiki/Document_Object_Model) traversal. I can't get it to render much faster than about 2,000 cells per second (and that's with everything else closed, and the ArchaeoBook's fan spinning like a centrifuge).  Oh well. I sort of feel bad that it's written in such an imperative style: I mean, it's easier to write, but all those `for` loops are ugly, and I just want to write more functionally all the time!!! 

Hmm. There doesn't seem to be an easy way to upload it from the ArchaeoBook. The usual FTP client I use is crashing. 

C. led an impromptu seminar on topological data analysis tonight (in particular, on persistent homology and barcodes). He was able to talk about it for a long time, and he showed us some stuff he had been playing around with. There were four or five of us in the room, and both M. and D. had really good questions. I listened passively (and without a lot of concentration). There's a TDA package for R, apparently... which is written in Haskell. Meanwhile, there's a whole group of kids who have coalesced to try to simultaneously learn Haskell and write a library to do [automatic differentiation](https://en.wikipedia.org/wiki/Automatic_differentiation), which is this really cool process that's sort of halfway in between numeric differentiation and symbolic differentiation. It sounds so cool and they seem so interesting and passionate and focused.

Several people have told me I should talk to B. about Haskell ("he loves teaching it! he spent like three hours walking me through such-and-such when I was getting started!"), and today I overheard him enthusiastically (and clearly) explaining some rudimentary aspect of Haskell to someone who was sitting near me.

I really wish I were better at asking for help.