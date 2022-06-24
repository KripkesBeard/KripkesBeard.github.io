# Random things

This is just a collection of random things, such as code snippets or what have you.


## First n powers of the first n naturals, painfully
I was trying to get an intuition for what the traverse function looks like when f and t are both List,
and after messing around with it I realize that the cardinality of the lists it was returning followed a pattern
relating to powers, so I thought "I bet I could get this to generate every power of each number up to n" and so
I did:

```Haskell
genPowers :: Int -> [Int]
genPowers = liftA2 (>>=) mkFs (\n f -> length . traverse f <$> mkNs n)
  where
    rep :: Int -> a -> [a]
    rep 0 a = []
    rep n a = [a] <> rep (n-1) a

    mkFs :: Int -> [Int -> [Int]]
    mkFs n = fmap (\x y -> rep x 0 <> [y]) [0..n-1]

    mkNs :: Int -> [[Int]]
    mkNs 0 = []
    mkNs n = mkNs (n-1) <> [[1..n]]
```

This is unbelivably inefficient and horribly obfuscated, and as such shouldn't be taken seriously. The idea is that
traverse in a strong sense generates the powerset of a list when given the right inputs, or at least it generates
lists that have the correct cardinality. So, I wanted to make this a function which would take in a number n and
generate the list of all of the powers of each natural number going from 1^1...1^n, 2^1.. and so on up to n^n.
liftA2 is just there to make the function pointfree, since we need to pass n to mkNs and to mkFs. mkFs basically
takes a natural number n and then returns a list of functions which each take a natural number n in and return
a list of numbers from 0 to n. Because of how bind and traverse work, the n gets passed into it twice so the numbers
match up. Basically, its a list of functions that produce sequential lists of numbers, and its parameterized on the
length of the last list. rep is just a hacky way of getting a list of some object and a specified length, I couldn't think
of anything in the standard library that does this. And mkNs makes a list of lists of numbers that also are sequential.
Then we have bind. Bind for lists represents their intuition as nondeterministic computations, if you pass a list of functions
into bind and a function waiting for an f to fmap over a list, you end up with the concatenation of that fmap over the list
for each f in the list of functions. That is, `fs >>= fmapMyXs == fmap f1 xs <> fmap f2 xs <> ...` and so we are fmapping
over the list of lists, but the function we're fmapping is the compositon of length and traverse. Traverse generates the
powerset and then length flattens it to a length, so we end up with the concatenation of all of the powers. Or something like that.
The reason, well one reason that it's horrible inefficient is because it doesn't just generate the numbers and then fmap exponentiation
over them, it's generating all of the lists and then taking their length, and since the numbers grow... well... exponentially, this
takes an obscene amount of time. Very fun, very cool. For ghci, it stops being instant at `genPowers 7`, `genPowers 8` takes about 4 seconds
and `genPowers 9` takes about a minute and a half, with the last number being the length of a list of around 400 million sublists.


This was the original code that I was messing with which gave me the idea

```Haskell
f     c = ""     <> [c]
f'    c = "a"    <> [c]
f''   c = "aa"   <> [c]
f'''  c = "aaa"  <> [c]
f'''' c = "aaaa" <> [c]

fs :: [Char -> [Char]]
fs = [f, f', f'', f''', f'''']

myList :: [Int]
myList = fs >>= (\f -> fmap (length . traverse f) ["a", "aa", "aaa", "aaaa"])
```

I won't lie to you, I still have no intuition for how it works, but it was fun to write and I felt like I knew what
I was doing the whole time because everything kept working the way I felt like it would. Weird experience. The last 
thing I want to do is figure out how to make the lambdas in the genPowers go away for an actual pointfree style.
