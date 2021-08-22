Hello! I am Peter, welcome to my website.

I am a logician at heart. I study symbolic logic and its application to the fields of philosophy, mathematics, computer science, and linguistics. I am especially interested in 
the study of languages, both artificial and natural, and their formal semantics. 

In the realm of computer science, the primary programming languages I use are Haskell, Scheme, Prolog, and C and I work with embedded domain specific 
languages, metalinguistic abstraction, interpreters, compilers, and the foundations of programming language theory.



Below you can find some of my work:

# Books

### [Lambdas Within Lambdas]()

A tutorial walkthrough of implementing both an interpreter and a compiler for multiple languages. It starts
off with the untyped lambda calculus, eventually introducing S-expression notation and ending with R5RS Scheme.
Then the simply typed lambda calculus is implemented and a series of stronger type systems are added until we 
end with a polymorphic Haskell-esque language. The metalanguage used in the book is Haskell. The compilers all
target abstract computational machines, such as the SECD machine and the STG machine. A final chapter focuses 
on the topic of compiling those types of machine languages to C (or LLVM). Each interpreter and compiler
has a full implementation on github.

### [Programming for Philosophers]()

This is a textbook meant to introduce philosophers, linguists, and foundationally inclined mathematicians
to functional and logic programming with applications to their fields. First Prolog is introduced, culminating with
a modal tableaux theorem prover. Next, Scheme is introduced, with applications aimed towards understanding referntial transparency
quotation, self reference, the halting problem, and fixed points. Finally, Haskell is introduced and used as a metalanguage
to embed fragments of English so as to execute a computational formal semantics system. Each project has a full implementation
on github.



# Haskell


#### [Lambdas](https://github.com/KripkesBeard/lambda.io) 

A website hosting a series of lambda calculus interpreters written in Haskell compiled into WebAssembly for fast interpretation. 


#### [Scheme Compiler]()

A fully compliant R5RS Scheme compiler written in CPS style (? virtual machines*) which compiles to C or LLVM. 


#### [Unlambda Compiler]()

A compiler for the Unlambda programming language, mostly a proof of concept that it *is* a coherent idea to compile the language.


#### [ASMPL]()

ASMPL (A String Manipulation Programming Language) is a logic programming language implementation of Raymond Smullyan's Elementary Formal Systems. Partly inspired by the logic 
programming language in Mel Fitting's book *Computability Theory, Semantics, and Logic Programming*.


#### [Formal Semantics]()

Implementations of various fragments of English as typed lambda calculi.



# Scheme

#### [Monadic Do Notation]()

A Scheme monad library, which uses call/cc to implement a do notation which lets you 'roll your own monads', based off work by Wadler and others showing that the continuation 
monad is universal over all monads.


#### [Monadic Parser Combinators]()

A monadic parser combinator library based off of the Haskell library Parsec, allowing for parser generation in Scheme using the powerful abstractions of monads and combinators.


#### [Moxen]()

A profunctor optics library for Scheme, similar to Haskell's lens and optics libraries. 



# Prolog

#### [Modal Tableux Solver]()

A propositional modal logic tableaux proof system.


#### [Lambda for Semantics]()

A typed lambda calculus implementation which is fit for formal semantics. 



# Notes and So On

#### [Logic Runs Through It](https://github.com/KripkesBeard/Logic-Runs-Through-It)

A collection of notes and worked solutions to various textbooks on mathematical logic and theoretical computer science.


#### [Lambdas, Types, and Registers](https://github.com/KripkesBeard/Lambdas-Types-and-Registers)

A collection of notes and worked solutions to various textbooks on my favorite programming languages, compiler theory, and eventually Knuth's The Art of Programming



## Some (Not Very) FAQs

### The Name

[Saul Kripke](https://en.wikipedia.org/wiki/Saul_Kripke) is a legendary philosopher and logician. His work, across all these fields, is hard to miss and is some of the main 
inspirations behind my interest in these subjects. So, why his beard? There is a very old philosophical problem which was given the nick name 
["Plato's Beard"](https://en.wikipedia.org/wiki/Plato%27s_beard) by Quine. I believe one of the problems Kripke raised in the philosophy of language (for those who know, the 
argument from "A Puzzle About Belief" that propositional attitudes are just as much an issue for the descriptivist's theory) is equally as vexing as Plato's.


### Contact

kripkesbeard @ gmail . com

