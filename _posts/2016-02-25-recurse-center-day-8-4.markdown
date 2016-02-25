---
published: true
title: Recurse Center, Day 8.4
layout: post
---
I'm writing this to procrastinate.

I find myself weirdly missing Haskell. I'm trying to write a (trivial) implementation of a linked list in JavaScript, which sets (or would set) pointers in the following way: so, as "memory" we have a JavaScript array of length whatever; every time we add a new element to the linked list, we choose its position in "memory" by just generating a random integer less than the length of the JS array. Which is fine, except we run the risk of accidentally overwriting old elements. So my idea is the following: choose a random integer; if there's already something in that position in the array, choose a new random integer; repeat this  say five times (or `n` times); if we still can't find an empty slot in the array, double the length of the array, and repeat. 

In principle this is really simple, and in Haskell it'd be really easy to implement... but for some reason I'm having trouble writing it in JS. It probably has less to do with JS (or any JS/HS comparison) than it does with the fact that I've been completely unable to focus the last day or two (or three). Ugh. 

I spent Monday and Tuesday working some more on Haskell, and then decided that I would spend the rest of the week doing easier stuff in JavaScript, but somehow I've found it hard to focus on JavaScript (it should be EASIER, since I know it better) and I find myself missing Haskell. I guess this is good. I have positive feelings toward Haskell! 

I wrote, on Tuesday, a hacky two-thirds of a symbolic differentiator in Haskell. But it was the easy two thirds, and the code looks really ugly and repetitive.

Anyway, I'll demonstrate it. Suppose you want to differentiate an expression like `sin(5x^7) + 4*(-x)`. You can't throw this into my symbolic differentiator, because it doesn't know how to parse that. But if you, um, hand-parse it, and turn it into a tree of nested parentheses:

    (Add (Sin (Mul (Val 5) (Pow Symbol (Val 7)))) (Mul (Val 4) (Neg Symbol)) )

then my script can differentiate it! (Note that I'm using the keyword `Symbol` to refer to the variable to be differentiated against.) We get:

    diff (Add (Sin (Mul (Val 5) (Pow Symbol (Val 7)))) (Mul (Val 4) (Neg Symbol)) )
    >> Add (Mul (Cos (Mul (Val 5) (Pow Symbol (Val 7)))) (Add (Mul (Val 0) (Pow Symbol (Val 7))) (Mul (Val 5) (Mul (Val 7) (Pow Symbol (Val 6)))))) (Add (Mul (Val 0) (Neg Symbol)) (Mul (Val 4) (Neg (Val 1))))

We can't really read that, so I wrote a function to print it out nicer (it doesn't take order of operations into account, since it's really stupid):

    cos(5*x^7)*0*x^7+5*7*x^6+0*-x+4*-1

Which is correct! I also wrote a function to quickly simplify these expressions with a couple of basic rules (e.g., if you try to multiply an expression by zero, you can just throw the whole expression away). So if we apply that, we get:

    cos(5*x^7)*5*7*x^6+4*-1

Which is correct! It was a lot easier to write, and produced way better output, than my Python implementation. But I think that has less to do with Haskell and more to do with this just being my second time implementing the same algorithm. On the other hand, the code IS way cleaner.  It's really just four separate things.

First, there's the type declaration:

<pre>
data Expr = Val Int
		   | Const [Char] -- :: [Char] -> Expr
		   | Symbol
		   | Neg Expr
           | Add Expr Expr
           | Mul Expr Expr
           | Sub Expr Expr
           | Pow Expr Expr
           | Div Expr Expr
           | Exp Expr
           | Log Expr
           | Sin Expr 
           | Cos Expr
           deriving (Show,Eq)
</pre>

This creates a new type `Expr` that can be any of the following things (separated by those `or` pipes `|`). Note the recursion: an `Expr`ession can be a `Val` (a number), a `Symbol` (the variable we're differentiating against), a `Const` (a non-numeric constant), OR it can be (for example) the ADDITION of two expressions (`Add Expr Expr`), the sine of an expression (`Sin Expr`), and so forth. So this lets us define a type as this nice recurse tree structure.

The differentiation function is just mindless pattern matching (but again with some pretty recursion):

<pre>
diff :: Expr -> Expr
diff (Val _ ) = Val 0
diff (Const _ ) = Val 0
diff (Symbol) = Val 1
diff (Neg x) = Neg (diff x)
diff (Add x y) = Add (diff x) (diff y)
diff (Mul x y) = Add (Mul (diff x) y ) (Mul x (diff y))
diff (Sub x y) = diff (Add x (Neg y))
diff (Pow x (Val n)) = Mul (Val n) (Pow x (Val (n - 1) ) )
diff (Div x y) = diff (Mul x (Pow y (Val (-1)) ) )
diff (Exp x) = Mul (Exp x) (diff x)
diff (Sin x) = Mul (Cos x) (diff x)
diff (Cos x) = Neg (Mul (Sin x) (diff x) )
</pre>

And I could continue, but especially without the syntax highlighting, I shouldn't be just tossing huge blocks of code. Anyway, the `simplify` and `pretty print` functions are similar in style: just huge lists of recursive pattern-matching. 

Actually, I am excited about this. I am going to stop writing and get back to this code. I just thought of like three things I can do really easily.

[Here's the full code on GitHub.](https://github.com/amalex5/RC/blob/master/haskell/symdiff.hs) Gah, this code looks so ugly and repetitive.

-----

EDIT: In three minutes I added the chain rule, using a new type declaration:

    Fxn [Char] Expr

a new differentiation rule:

    diff (Fxn xs y) = Mul (Fxn (xs ++ "\'") y) (diff y)

a pointless new simplify rule (Haskell gets upset if I don't add one. There's got to be a way to make it just pass through by default):

    diff (Fxn xs y) = Mul (Fxn (xs ++ "\'") y) (diff y)

and a new printing rule:

    pprint (Fxn xs y) = xs ++ "(" ++ pprint y ++ ")"

Here's it in action:

<pre>
*Main Prelude> diff (Fxn "f" (Fxn "g" Symbol))
>> Mul (Fxn "f'" (Fxn "g" Symbol)) (Mul (Fxn "g'" Symbol) (Val 1))
*Main Prelude> simplify it
>> Mul (Fxn "f'" (Fxn "g" Symbol)) (Fxn "g'" Symbol)
*Main Prelude> pprint it
>> " f'(g(x))*g'(x) "
</pre>