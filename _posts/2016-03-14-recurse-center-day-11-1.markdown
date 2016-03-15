---
published: true
title: Recurse Center, Day 11.1
layout: post
---
Well! Having felt almost vaguely comfortable in Haskell for all of a week, I've apparently decided to descend back into the depths of intellectual darkness and misery. All I wanted to do was write a parser. All I wanted to do was add some code to my symbolic differentiator so that it could take in mathematical expressions written in the usual human form, and turn them into a nice pretty syntax tree. And I knew that would be kind of tricky, but AAAAAGH. It's difficult AND kind of beautiful at the same time, and I am deeply confused and have no idea what I'm doing, and I'm not sure whether I enjoy it or not.

I've written silly parsers before a handful of times, and they've always been disastrous, barely-working-and-not-for-very-long messes of `if`-`then` conditionals (with recursion tossed in here and there just to make things even more confusing). They're the coding equivalent of [serac fields](https://en.wikipedia.org/wiki/Serac). The seracs are standing, sort of, but you never know when one of them will randomly topple and bring all the rest of them down!

But there's actually a lot of theory behind the idea of *[formal languages](https://en.wikipedia.org/wiki/Formal_language)*. It's all very interesting or very boring. I can't figure out which. My gut is towards the "boring" side of things, but I suspect that I'm negatively biased due to coming at it from a utilitarian perspective (i.e., wanting to get my d*mn parser to work). Oh well. But anyway, the way that REAL parsers actually work is through this idea of a "*[parser combinator](https://en.wikipedia.org/wiki/Parser_combinator)*." Meaning, rather than try to construct a teetering mess of `if`-`then` seracs, you just compose simple parsers into larger and more complex parsers. So it's very functional, and a lot easier to understand, and a lot easier to write! 

Or so I'm told. Honestly, if I were approaching this in a purer context (i.e., taking a formal languages class) I'd probably be learning a lot more and having more fun; since I'm trying to achieve a single very specific task, I'm falling into the trap (one I frequently fall into) of trying to understand *just enough* to achieve my objective... but since this is all a


On a completely unrelated note, I want to listen to Roman numerals. On Friday I wrote a short script in JavaScript to turn decimal numbers into Roman numerals; to test it, I had it print all the Roman numerals from 1 to 1000. Scrolling through the output, it was immediately obvious that Roman numerals create these amazing waveforms! I don't want to paste a really long example in here, but [if you click "run" and scroll through the output](https://repl.it/BvYt/2), you can see what I mean. I probably wouldn't have noticed had it not been in a monospaced font. 

But what's going on is something like this. Here are the Roman numerals between 1 and 10 (inclusive), except that instead of writing out the numerals, I've written an "X" instead of each character, to emphasize the LENGTH of each number:

<pre>
X
XX
XXX
XX
X
XX
XXX
XXXX
XX
X
</pre>

See that? The length of the Roman numeral representation increases from 1 to 3 (inclusive), then it shortens down to 5, then it lengthens back up to 8, then it shortens back down to 10. *And this pattern repeats over every order of magnitude.* Roman numerals split up in this nice linear way: the Roman numeral representation of 384 is just (the representation of 300) ++ (the representation of 80) ++ (the representation of 4). So there's this fundamental "Roman numeral waveform" that's repeated with a period of 10, a period of 100, a period of 1000, and so forth.

Anyway, I've probably got half of that language ("waveform," "harmonics," etc.) wrong, and it's not a particularly fundamentally interesting thing; I was just really excited to discover this pattern. I'm going to ask some of the more sonically- and musically-inclined people here how I can listen to it. 

I went to E.'s 26th birthday party on Saturday night. On Sunday K. and I rode the Staten Island Ferry: hardly the [Wenatchee](https://en.wikipedia.org/wiki/MV_Wenatchee) or the [Tacoma](https://en.wikipedia.org/wiki/MV_Tacoma), but free, and with a view of the Statue of Liberty. [I want to get North Korean food in Flushing](http://gothamist.com/2015/01/17/north_korean_food_nyc.php)