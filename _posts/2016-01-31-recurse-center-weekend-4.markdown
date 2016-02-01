---
published: true
title: Recurse Center, Weekend #4!
layout: post
---
I went into RC yesterday and today, briefly, and got a number of small but uninteresting tasks done, few of which involved writing code and most of which completely peripheral to RC. But that's OK. Last week was absolutely the most fun of any week at RC so far, even though it wasn't my most productive, and even though I think the reason I didn't write anything in this log [0] on Monday or Tuesday was because I was feeling really sad and discouraged. But then I had so much success rewriting my Tetris-on-polar-coordinates implementation! (A little bit TOO MUCH success, since now it's so purely functional that I'm totally stumped as to how to deal with user interaction, but we'll deal with that this week.) G. came to RC on Thursday and we got to hang out and code and talk! [R. came and spoke](https://mobile.twitter.com/recursecenter/status/693264816971079680) (to a packed audience) on Friday! I had really interesting conversations with people from OpenDoor and Simple! My practice coding interview (with the alumna volunteer from OpenDoor) went super well! [1][2] Etc.! Etc.!

ANWYAY, I do want to write something specific today. In particular, I'm still agonizing over my continued fear of agonizing over Haskell, and one of the things I've been thinking about has been whether I should just abandon ship [3] and send out a distress signal to the [SS Clojure](https://en.wikipedia.org/wiki/Clojure) to rescue me. Meaning: in preparing for RC, I knew I wanted to really immerse myself in a functional language, and I thought a lot about WHICH. And it basically came down to Clojure or Haskell. G. suggested I go with Clojure. ([Here's an interesting Hacker News thread about "Clojure vs Haskell for a first functional programming language"](https://news.ycombinator.com/item?id=4122764)). My gut was (and is) to go with Haskell, basically because what I was hearing was "Haskell is harder but more worth it."

Blah blah blah, temptations and dalliances, etc., and so today and yesterday I've been playing with Clojure (in a [console](https://en.wikipedia.org/wiki/Read–eval–print_loop)! take that, Haskell!), and it's SO MUCH FUN. What finally made me try it out was stumbling across this essay, "[Clojure is for Type B personalities](https://gist.github.com/oakes/c82cd08821ce444be6bf)", and while I certainly don't want to endorse pseudo-psychobabble, I have to quote from it. Here's the start:

>The other day, I was wondering why Clojure fits my brain so well. I think I was relaxing on my old couch, drinking cheap beer, eating a gas station pastry, and drawing doodles on a stack of overdue bills I forgot to pay. Little did I realize, these things are all connected.

God, what an enticing image! Except for the forgetting-to-pay-bills part. Sounds like my life in Phx.

>... Type A people prefer a "top down" methodology, modeling everything in types and planning out the architecture before any functionality is implemented. You see this in the "API first" approach in object-oriented languages like Java. You also see it in ML family languages like Haskell, where you are often advised to follow type-driven development (writing type signatures before implementing anything). ... 
Type B people prefer a "bottom up" methodology, immediately implementing functionality and interactively building on previous work until a larger structure emerges organically. You see this in the Lisp community, where REPL-driven development is the norm.
>
> ...
>
>A top-down approach seems ideal for well-understood problems where correctness is the most important attribute. If you're making accounting software, or the avionics software for a plane, you're not necessarily blazing any trails. You have a list of requirements, and you need to satisfy them with minimal defects -- especially if money and lives are on the line.
>
>A bottom-up approach works well for projects with a lot of unknowns, like artificial intelligence or anything artistic. Paul Simon didn't come up with *The Sound of Silence* from a list of requirements. He sat in his bathroom with the lights off and riffed on his guitar until genius poured out. It's no accident that there are Clojure projects like Overtone and Quil. A REPL session is the programmer's guitar riff.

God, what an endorsement! The Clojure style is how I program anyway: I just randomly type things into the JavaScript/Python console until they work, and then I paste them into a text file!

On the other hand, one of the appeals of learning Haskell is exactly THAT it's so different–not just in its syntax and style, but the very mental process of "planning things out beforehand" (as the author of the above essay puts it). How can you really learn if you're not trying to do things that AREN'T what you'd naturally do? Real learning and growth requires getting away from [gradient descent](https://en.wikipedia.org/wiki/Gradient_descent)–letting the entropy shake you off the local maxima, and trudging through the snow in the perpetual search for the global maximum.

Uhhh my brain just flashed a METAPHOR COLLISION ERROR. I see my profundity is getting more and more banal, too. Probably time to stop writing.

On Saturday morning I took the train out to Long Island to watch N. be ordained as a deacon in the Episcopal church. I'm still not totally clear on what a deacon is, but N. (who was a math major at the U of C) said that the diaconate is a superset of the priesthood, and sometime this summer he'll get an ontological promotion (that's my phrase) and become a priest. 

Tomorrow I get to (need to) renew my monthly MetroCard!

-----
[0] referring to this as a "log" in the sense of a "captain's log" or something–a deliberate, regular, daily record. (And I know that there's an obvious etymological connection to "blog," but I think "blog" doesn't have the same connotations as a [logbook](https://en.wikipedia.org/wiki/Logbook) does.)

[1] Not that RC is a coding bootcamp, and not that I'm here to to go trade school... heaven forbid I be so vulgar. But it would be nice if the numbers in my bank account moved in the other direction. (*I think you mean "necessary," Andrew.*)

[2] The alumna interviewer explained her career trajectory: she majored in CS at Williams, graduated in '99, worked in i-banking for a few years, hated it, was a ski bum for like a decade; finally, a few years ago, decided she should probably get a real job again, went to RC, re-learned coding, and eventually got hired at OpenDoor. So jealous of the "ski bum" part. Every winter for the past five years I've wanted to be a ski bum. (*So why haven't you?*)

[3] not a dead metaphor! continuing the nautical imagery.