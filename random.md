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
and, e.g.,

```Haskell
λ> genPowers 1
[1]
λ> genPowers 2
[1,1,2,4]
λ> genPowers 3
[1,1,1,2,4,8,3,9,27]
λ> genPowers 4
[1,1,1,1,2,4,8,16,3,9,27,81,4,16,64,256]
λ> genPowers 5
[1,1,1,1,1,2,4,8,16,32,3,9,27,81,243,4,16,64,256,1024,5,25,125,625,3125]
λ> genPowers 6
[1,1,1,1,1,1,2,4,8,16,32,64,3,9,27,81,243,729,4,16,64,256,1024,4096,5,25,125,625,3125,15625,6,36,216,1296,7776,46656]
λ> genPowers 7
[1,1,1,1,1,1,1,2,4,8,16,32,64,128,3,9,27,81,243,729,2187,4,16,64,256,1024,4096,16384,5,25,125,625,3125,15625,78125,6,36,216,1296,7776,46656,279936,7,49,343,2401,16807,117649,823543]
λ> genPowers 8
[1,1,1,1,1,1,1,1,2,4,8,16,32,64,128,256,3,9,27,81,243,729,2187,6561,4,16,64,256,1024,4096,16384,65536,5,25,125,625,3125,15625,78125,390625,6,36,216,1296,7776,46656,279936,1679616,7,49,343,2401,16807,117649,823543,5764801,8,64,512,4096,32768,262144,2097152,16777216]
λ> genPowers 9
[1,1,1,1,1,1,1,1,1,2,4,8,16,32,64,128,256,512,3,9,27,81,243,729,2187,6561,19683,4,16,64,256,1024,4096,16384,65536,262144,5,25,125,625,3125,15625,78125,390625,1953125,6,36,216,1296,7776,46656,279936,1679616,10077696,7,49,343,2401,16807,117649,823543,5764801,40353607,8,64,512,4096,32768,262144,2097152,16777216,134217728,9,81,729,6561,59049,531441,4782969,43046721,387420489]
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

## "Roadmap" for Type-level Haskell

1. Terms types and kinds
2. Type classes and constraints
3. Multiparameter type classes and functional dependencies
4. GADTs and Existential types
5. RankNTypes
6. Impredicative Types
7. Type Families
8. Singletons and Dependent Types
9. Linear Types

## S Pattern

The function type ```((->) r)``` and its various typeclass instances, such as functor, applicative, monad, etc., can
be very confusing when first encountered. It turns out, though, that they're incredibly useful. In particular, the
applicative instances makes ```pure``` and ```<*>``` into the K and S combinators, repsectively. They're even defined
this way in base (```pure``` is defined as ```const```). 

There is a common pattern that appears when you want to compare or otherwise process sequential pieces of data
in a container, such as a list. A good example is day 1 of the 2021 advent of code, where you want to compare
sequential integers in a list of input. An idiomatic Haskell way of doing it would be to use ```zipWith```,
the comparison function, and then the original list and the ```tail``` of the list. But writing it naively uses
the list twice, and therefore isn't point free.

We can make it point free by using S, that is, the ```((->) r)``` instance of ```<*>```:

```Haskell
notPointFree xs = zipWith (<) xs (tail xs)

pointFree = zipWith (<) <*> tail
```
