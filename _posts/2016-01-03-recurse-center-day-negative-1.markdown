---
published: true
title: Recurse Center, Day Negative 1
layout: post
---
I got Haskell running on my archaeological MacBook! (Or, to be more specific, I got [GHC](https://en.wikipedia.org/wiki/Glasgow_Haskell_Compiler), the main compiler for Haskell, running.)

I am delinquent: I promised myself in my last blog post that I'd do it on Friday. Instead I did it today, Saturday, though technically I didn't get it running until 1 AM Sunday (approximate time right now), and in any case I was only trying to install it as a way of procrastinating packing and cleaning. But it's working! I typed `ghci` into the command line, and poof! interactive Haskell! 

    GHCi, version 7.10.3: http://www.haskell.org/ghc/  :? for help
    Prelude>

It correctly told me that `5+7` (my favorite one-digit numbers) is `12`. I left some tabs with chapters from [Learn You A Haskell For Great Good](http://learnyouahaskell.com/) open, so maybe tomorrow on the bus to New York I'll fool around some more.

More likely I will just sleep, though. I need to: between travel to Portland and prepping for RC, I've been running a bit of a sleep deficit the past week.

Fun details: I installed the [Haskell Platform](https://www.haskell.org/platform/), which is "Haskell with batteries included," which in un-clichéd language means that it's GHC, a debugger, a bunch of useful packages, and a build system. To install the Haskell Platform I had to install Xcode (Apple's developer/Unix tools), or rather "Xcode Developer Tools," which is a subset containing (I guess) gcc, make, git, and some other basic unix/command line utilities. I'm running 10.6.8 on the ArchaeoBook, so I had to find an old version, and ended up downloading the released-in-2010 [Xcode 3.2.2 Developer Tools](http://adcdownload.apple.com/Developer_Tools/xcode_3.2.2_developer_tools_beta_20728/xcode322_2148_developerdvd.dmg) (free registration required).

Off to New York tomorrow! M. is letting me stay with him in his palace in outer Queens ("but I'm slammed with this book project, so I might not get to see you all that much.") Earlier today I was re-reading the action-packed chapter of the *Bros. K.* where Ivan, fed up and frustrated, finally storms out of his father's house:

>He greeted his father affably and even inquired especially about his health, and then, without waiting for his father to finish his reply, at once announced that he was leaving for Moscow in an hour, for good, and asked that the horses be sent for.

Daddy Karamazov asks Ivan to stop at a nearby town on his way to re-negotiate the harvest of some timberland he owns. He blabs on about the best way to bargain with the locals. Ivan dithers back and forth. Dad forces him to agree to do it. As Ivan is hopping into the carriage, one of his father's servants, Smerdyakov, comes up. Smerdyakov was born without any apparent father to a mentally-disabled, destitute local peasant ("Stinking Lizaveta"), in a sort of creepy reversal of the immaculate conception. It's not that immaculate. Everyone in town knows that it's Daddy Karamazov who probably raped Stinking Lizaveta. So Smerdyakov is not only his servant but his illegitimate child (and Ivan's half-brother).

Anyway, at this point, Smerdyakov has already told Ivan–implicitly, at least–that he'll kill Daddy Karamazov as soon as Ivan leaves. 

> "So it's true what they say, that it's always interesting to talk with an intelligent man," Smerdyakov replied firmly, giving Ivan Fyodorovich a penetrating look.

In the carriage Ivan changes his mind about renegotiating the stupid timberland contract. He redirects his coachman to take him straight to the train station. 

>At seven o'clock in the evening Ivan Fyodorovich boarded the train and flew towards Moscow. "Away with all the past, I'm through with the old world forever, and may I never hear another word or echo from it; to the new world, to new places, and no looking back!" But instead of delight, such darkness suddenly descended on his soul, and such grief gnawed at his heart, as he had never known before in the whole of his life. He sat thinking all night; the train flew on, and only at daybreak, entering Moscow, did he suddenly come to, as it were.
>
>"I am a scoundrel," he whispered to himself.

(pages 277, 279 and 280 in the FSG paperback of Pevear and Volokhonsky.)