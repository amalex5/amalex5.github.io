---
published: true
title: Recurse Center, Day 7.1
layout: post
---
This isn't particularly profound, but there's a syntactic thing in Haskell that I've fallen in love with. Namely: Haskell has an operator to *change the precedence of operations*. What does that mean? So, I often find myself (in LOTS of situations) trying to type into a calculator something like

    5 + 7

only to realize that I then want to divide the whole thing by `2`, but of course you can't just type in `/ 2`:

    5 + 7 / 2

because what I really mean is 

    (5 + 7) / 2

but of course then I have to GO BACK and type in an opening parenthesis and it's such a pain!

But in Haskell, you can just type in a dollar sign, and Haskell treats everything that comes before it as having been surrounded by parentheses:

    5 + 7 $ / 2

Woo! In fancy terminology the way to describe `$` is that it changes the "operator precedence" or something. Or that it has higher precedence than anything else. And I guess "precedence" in the context of language parsing is a fancier way of saying "order of operations."

BTW, giant caveat, none of this is actually true. Meaning, my examples aren't actually valid Haskell. So I almost scrapped this post, but I really wanted to show off `$` in the simplest context possible. And actually, I'm not totally clear why. I played around a lot. Maybe my understanding is completely off (and so this post is wrong not only in the specific example but the general point). Oh well. 

For the sake of SOME honesty, here's an example of using it in valid-but-boring Haskell: so we could write a nested function call with a bunch of parentheses:

   f ( g x)

Note that function application in Haskell doesn't use parentheses: so instead of writing `f(x)`, we write `f x`.) Anyway, we could do that, but that requires all those parentheses, and it requires that we properly balance them, etc., so instead we could equivalently write:

    f $ g x

No parentheses!
