---
published: true
title: Recuse Center, Day 2.4
layout: post
---
I got nothing accomplished today. I wrote no code. That's not good.

For the sake of writing something, though, I will say that I played around a bit more with my Game of Life implementation. I'm a little embarrassed about this, since I feel like having fun with digital/generative art is a phase most people go through as teenagers. On the other hand, it IS cool. I was thinking a lot about the [amazing installation on the underside of the Johnson Museum at Cornell](http://museum.cornell.edu/exhibitions/leo-villareal-cosmos): a lattice of 100x100 LEDs, all programmed to light up in these amazing, beautiful, generative patterns. I mentioned this to D., and he brought up the (equally-amazing) [pixellated light sculpture](http://thebaylights.org/) that's on the side of the new Bay Bridge. (It turns out they're both by [the same artist](http://villareal.net/).)

Though, really all I did to play around was to introduce a randomness parameter into the live/die decision: i.e., regardless of the decision, a cell has a probability *p* of their fate being reversed. One of the immediate results is that patterns don't die out: there's always these background quantum fluctuations of cells popping into and out of existence. The problem with introducing the randomness in this way, though, is that most of the cells die right away. Maybe they pop into existence, but statistically they're almost certainly alone, and living cells with no neighbors die. It would be nice to improve it by, e.g., coding it so that if a cell randomly pops into existence, its neighbors' chances of popping into existence increase a bit.

None of that is very clear. Oh well.

I forced myself to code-review with D., who said he thought it was really well-written JavaScript. I agree with the specific compliment: it *was* good JS! The program is so conceptually straightforward and clear in my mind that I was able to write very clear and well-organized JS. (Just like with writing English!) But in general I don't think I'm a very strong JavaScripter. I never use objects in JS (or rather, JS's weird [object-like system](https://en.wikipedia.org/wiki/Prototype-based_programming)) and don't really know how they work. I guess I should try to find something to write in JS that will FORCE me to be more object-oriented.

Argh. But I don't want to waste my time at RC writing JavaScript. I want to do things that are HARD! things that use RC's human capital and social resources (i.e., all the really cool/smart/knowledgable people I'm around)! things that are harder to motivate myself to do on my own!

While I was waiting in line [for lunch](http://vanessas.com/) I texted Alla:

> haskell is making me so sad. i just want to love and be loved by haskell. i spent a day writing js bc i thought it wd make me feel better and it sorta did but in a guilty sleeping-with-your-loser-ex sort of way. it was PLEASURABLE but asymmetric.

She texted back some sort of witty response. Since my flip phone has almost no space left for incoming texts, I had to delete it as soon as I read it. It was something to the effect of, she'd been writing a lot of JS recently for work and felt similarly.

Anyway. There was ONE thing I wanted to write about today, namely, the ONE vaguely interesting thing/decision I had to make yesterday while writing my Life implementation (which I guess I really need to put on the internet somewhere).

Here's the thing: the Game of Life, in a strict mathematical sense, takes place on an INFINITE plane. Mathematicians are comfortable with infinite planes, philosophers aren't, and computer scientists deny their existence. The ArchaeoBook certainly can't contain an infinite plane within its 512 kilobytes of RAM. Even Google's data centers can't contain an infinite plane. 

So we need to play a version of Life restricted to some finite plane. But which one? During D.'s review of my code, he said that his first instinct would be to just play it on a truncated Euclidean plane: i.e., just declare that everything outside of the computer's viewing window is dead. So he was impressed with what I did: play it on a torus. (I didn't think it was all that impressive. Whatever, I'm desperate for positive feedback; I'll take it.)

Mathematically, it's actually the simplest option: if something tries to go off the TOP of the screen, you make it appear at the bottom! If something tries to fly off the LEFT side, you make it fly in from the RIGHT side! I'd explain it with a diagram, but I'm not sure how to add images in TinyPress, and things involving graphics tend to strain the ArchaeoBook's limits. 

So that's how easy it is to make a torus! And other weird shapes are easy to make, too: just by associating each of the four sides of a rectangle with different sides, you can glue (that's the technical word. no, really, it is!) together a torus, a Klein bottle (a torus with a twist), and a sphere!

I'm not sure if any of that made sense without pictures. ANYWAY, the point is, it's mathematically simple, but implementing it in the logic of a program was a bit trickier. What I did was something like this: so, the program determines whether a cell should live or die by looking at its neighbors. How does it find its neighbors? Well, that's the tricky part. I'm SURE there's some sort of data structure that would make it easy and elegant to do. All you want is the nine immediate neighbors on a grid (up, down, left, right, diagonal). Not knowing of any such data structures, and not thinking it was worthwhile to think too hard, I wrote them all out by hand:

    neighbors = {
    		tl: {x: blahblahblah, y: blahblahblah},
    		tc: {x: blahblahblah, y: blahblahblah},
    		tr: {x: blahblahblah, y: blahblahblah},
    		cl: {x: blahblahblah y: blahblahblah},
    		cr: {x: blahblahblah, y: blahblahblah},
    		bl: {x: blahblahblah, y: blahblahblah},
    		bc: {x: blahblahblah, y: blahblahblah},
    		br: {x: blahblahblah, y: blahblahblah},
    	}

("tl" is "top left," and so on.) But the tricky part is: how do you find the `x` and `y` coordinates? If we were on a normal two-dimensional grid, it'd be easy: just add or subtract `1` or `0`. You're only moving one coordinate away. But we're not on a normal two-dimensional grid. We're on a torus. So when you have a piece that's at the very TOP of the grid, the neighbors "above" it are actually at the BOTTOM of the grid. Same with pieces that are on the bottom edge, the left edge, and the right edge. How do you account for this without getting into some disgusting plebian mess of `if` statements?!??

Here's what I did: I wrote a separate set of functions to get the coordinates. Imagine you've got a cell that's at the very top of the grid, and you're trying to find its neighbors. Some of the neighbors will have the "normal" `y`-coordinate: the neighbors to the left and right will have the cell's own `y`-coordinate, and the neighbors below it will have the cell's `y`-coordinate minus one (since my axes start at the top left corner and move to the bottom right). But what about the `y` coordinate of the neighbor above it? The neighbor "above" it is actually at the bottom of the grid. How do you account for that? So I wrote a function specifically to find the `y`-coordinate of the neighbors above the cell:

    yAbove = function (y) { return 1 <= y ? y - 1 : gridHeight -1 }

It checks to see whether the cell in question is at the top edge of the graph. If it's not, it just returns the normal `y`-coordinate (the cell's own `y`-coordinate plus one); if it is, it returns the `y`-coordinate of the BOTTOM of the graph (minus one, since my numbering system starts at zero). And you have to do this with each weird edge condition (if it's on the left, right, top, or bottom). Here's the full set of functions:

    yAbove = function (y) {return 1 <= y ? y - 1 : gridHeight -1 },
    yBelow = function (y) {return y < gridHeight - 1 ? y + 1 : 0} ,
    xLeft = function (x) {return  1<= x ? x - 1: gridWidth - 1 },
    xRight = function (x) {return x < gridWidth - 1 ? x + 1 : 0}

With these functions brought to life, our full set of coordinates for the neighbor cells is:

    neighbors = {
    		tl: {x: xLeft(x), y: yAbove(y)},
    		tc: {x: x, y: yAbove(y)},
    		tr: {x: xRight(x), y: yAbove(y)},
    		cl: {x: xLeft(x), y: y},
    		cr: {x: xRight(x), y: y},
    		bl: {x: xLeft(x), y: yBelow(y)},
    		bc: {x: x, y: t.yBelow(y)},
    		br: {x: xRight(x), y: yBelow(y)},
    	}

Again, it's kind of ugly, but compared to the monster it COULD have been, it's not THAT bad.

It occured to me, after I had gotten this working, that I could go even further. I had hard-coded the `yAbove` function and its friends to represent the geometry of a torus. Why not just have a SET of functions, one for each of the basic geometries you can make by gluing together sides of a rectangle? So I wrote something like this: 

    var topologies = {
    	torus: {
    		yAbove: function(y) {return 1 <= y ? y - 1 : gridHeight -1 },
    		yBelow: function(y) {return y < gridHeight - 1 ? y + 1 : 0} ,
    		xLeft: function(x) {return  1<= x ? x - 1: gridWidth - 1 },
    		xRight: function(x) {return x < gridWidth - 1 ? x + 1 : 0}
    		},
    	sphere: {
    
    	},	
    	
    	kleinBottle : {
    
    	}
    
    }

So then it's easy to set your topology to be that of a torus by calling:

    var topology = topologies["torus"]

and then all of your functions become sub-functions (not the right word. elements?) of `topology`, e.g.:

    		tl: {x: topology.xLeft(x), y: topology.yAbove(y)}

"I'll fill in the geometry for a sphere and a Klein bottle in the morning!," I thought. "It'll be fun!"

But when I sat down to do it, I realized that it's impossible (or at least really gross and ugly) to just "fill them in" in the way I had structured all the code. See, like a Klein bottle: the sides are glued together like in a torus, but with a TWIST, literally, which means that if you have a cell that's at the top edge, its neighbors "above" will not only be at the bottom of the grid, they'll have a different `x`-coordinate (they'll be horizontally flipped). (This is really easy to show with a picture and maybe a bit more confusing in words.) What that means is that a weirdness in the `y` behavior results in a weirdness in the `x` behavior. But all of the functions above assume that choosing the proper `x` is independent of choosing the proper `y`. The functions I wrote allow weird `y` behavior to result in weird `y` coordinates; they don't allow weird `y` behavior to result in weird `x` coordinates. Damn. 

Spheres have the same problem: you want to associate the top edge of the graph with (e.g.) the right edge, which involves reflecting BOTH the `x` and `y` coordinates. Plus spheres have the added difficulty of, what do you do is the grid isn't a square? The Game of Life is discrete, so you can't just stretch and smush things to fit. Yargh.

I am sure there are really elegant solutions for all of these problems. I am also reasonably pleased with the reasonable elegance of my solution. It's neither horrifically ugly, nor so abstract that it's hard to understand/implement. What's the line from *Hamlet*? *"Neither too particular nor too general a theory be!"*

These ideas about geometry are so easy to fit into pictures and equations–but so much harder to fit into the particular logical structure of basic JavaScript data structures! I really like the process of fitting abstract ideas into concrete forms. Some ideas are better expressed in some languages/media than others. JavaScript, English, watercolors, physics, poetry–each of them better at expressing some ideas rather than others, and none of them really good enough to express the full beauty of ideas in general (i.e., truth).

Excerpt from Plato goes here! Actually, what I really wish I had on hand right now was a copy (well, one of my like three copies) of *A River Runs Through It*. One of the most under-appreciated themes about that (otherwise deservedly-well appreciated!) novella is the difficulty of taking ideas expressed in one medium and expressing them in another. How can Norman Maclean express the beauty of fly-fishing in English? How can Maclean express his love for his brother through fly-fishing?

I really could have explained all of this geometry stuff better if I could have drawn some pictures.