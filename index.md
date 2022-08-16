Hello! My name is Peter, welcome to my website.

On this page you can find my programming work, focusing mainly on functional programming, interpreters, and compilers. 
You can click the summary below each project title to find out more about each one. You can also find out more about 
me [here](https://kripkesbeard.github.io/about), and contact me at kripkesbeard@gmail.com

## Books <a name="Books"></a>

### [Lambdas Within Lambdas]()
<details>
    <summary><b> A tutorial for implementing the lambda calculus </b></summary>
    
    <br>
  A tutorial walkthrough of implementing both an interpreter and a compiler for multiple languages. It starts
  off with the untyped lambda calculus, eventually introducing S-expression notation and ending with R5RS Scheme.
  Then the simply typed lambda calculus is implemented and a series of stronger type systems are added until we 
  end with a polymorphic Haskell-esque language. The metalanguage used in the book is Haskell. The compilers all
  target abstract computational machines, such as the SECD machine and the STG machine. A final chapter focuses 
  on the topic of compiling those types of machine languages to C (or LLVM). Each interpreter and compiler
  has a full implementation on github.
    
</details>
<br>


### [Programming for Philosophers](https://github.com/KripkesBeard/programming-for-philosophers)

<details>
    <summary><b> A tutorial for philosophers to gain programming skills applicable to their field </b></summary>

<br>
This is a textbook meant to introduce philosophers, linguists, and foundationally inclined mathematicians to functional and logic programming with applications to 
their fields. First Prolog is introduced, culminating with a nonmonotonic theorem prover used to represent formalized epistemic reasoning. Next, Scheme is introduced, 
with 
applications aimed 
towards understanding referential transparency, quotation and quasiquotation, self reference, the halting problem, and fixed points. Finally, Haskell is introduced and 
used as a 
metalanguage to embed fragments of English in order to execute a computational formal semantic system. Each project has a full implementation on github.
        
</details>
<br>
  
### [A Logician's Toolkit]()
<details>
    <summary><b> A reference for anyone who needs to apply the tools of formal logic </b></summary>
    
<br>

This book is a collection of tools and formal methods used by logicians. It is inspired by 
[Partee, ter Meulen, and Wall](https://www.springer.com/gp/book/9789027722447) and serves a similar function of being a reference for anyone in the fields of mathematics, 
philosophy, linguistics, computer science, cognitive science, or any other field which makes use of the common tools used by logicians. The subjects included are 

1. Set Theory
2. Classical Logic
3. Algebraic Structures
4. Intuitionistic & Modal Logic
5. Discrete Structures
6. Formal Languages, Grammars, & Automata
7. Turing Machines & The Lambda Calculus
8. Typed Lambda Calculi, Functional Programming, & Categorial Grammar
9. Category Theory
10. Topoi vs. Sets

The scope of the book is much greater than Partee Et al., and thus welcomes a wider range of disciplines whose practitioners will find it useful.

</details>
<br>
<br>

## Haskell <a name="Haskell"></a>

### [Fragments]()

<details>
  <summary><b> A computational system for formal semantics via functional programming </b></summary>
    
<br>
  
Two developments of formal semantics for natural languages done with Haskell as the metalanguage. One takes the indirect representation route, associating
a logical representation to each English sentence before deriving its semantic interpretation. The other uses direct representation without an intermediate logical
form. Additionally there are libraries implementing the fragments developed in 
[Jacobson](https://global.oup.com/academic/product/compositional-semantics-9780199677153), [Coppock & Champollion](https://eecoppock.info/teaching.html), 
[Heim & Kratzer](https://philpapers.org/rec/HEISIG), and [von Fintel & Heim](https://github.com/fintelkai/fintel-heim-intensional-notes). Additionally it 
contains libraries which explore the use of monads and continuations in semantics as described in e.g. 
[Asudeh & Giorgolo](https://global.oup.com/academic/product/enriched-meanings-9780198847861) and 
[Barker & Shan](https://global.oup.com/academic/product/continuations-and-natural-language-9780199575022).

</details>
<br>

### [Spinner]()

<details>
  <summary><b> A Scheme Compiler </b></summary>
    
<br>
  
An R7RS Scheme compiler and REPL interpreter.

</details>
<br>

### [Plus C]()

<details>
  <summary> <b> A C compiler </b> </summary>
    
<br>

A C compiler with a debugging/interpretation system.

</details>
<br>

### [Relambda]()

<details>
  <summary> <b> An Unlambda compiler </b> </summary>
    
<br>

A compiler for the Unlambda programming language, mostly a proof of concept that it *is* a coherent idea to compile the language 
(c.f. [this](http://www.madore.org/~david/programs/unlambda/#impl_comp)). The larger logico-philosophical issues surrounding why the answer to the question is yes
are explicated via a presentation of formal operation and denotational semantics of the language. Based mainly on graph *re*duction.

</details>
<br>

### [ASMPL]()

<details>
  <summary> <b> A string rewriting logic programming language </b> </summary>
    
<br>
  
ASMPL (A String Manipulation Programming Language) is a logic programming language implementation of 
[Raymond Smullyan's Elementary Formal Systems](https://philpapers.org/rec/SMUTOF). Partly inspired by the logic 
programming language in Mel Fitting's book [*Computability Theory, Semantics, and Logic Programming*](https://philpapers.org/rec/SHEFMC). Smullyan's model of 
computation is astonishingly elegant, and has *a very simple* set theoretic string rewriting interpretation that lends itself to a very coherent implementation as a 
logic programming language. 

</details>
<br>

### [Harmonia]()

<details>
    <summary> <b>A harmony and chord analysis tool </b> </summary>
    
<br>

A tool which functions as an expert system for questions about music including chords, harmony, and scale analysis.
    
</details>
<br>


<br>


## Scheme <a name="Scheme"></a>

### [Do Over Lambda]()

<details>
  <summary> <b> An implementation of monadic do notation</b> </summary>
    
<br>

A Scheme monad library, which uses call/cc to implement a do notation in order to let you 'roll your own monads', conceptually based off of work by 
[Wadler](https://jgbm.github.io/eecs762f19/papers/wadler-monads.pdf) and others showing that the continuation monad is universal over all monads.

</details>
<br>

### [Mutatus]() 

<details>
  <summary> <b> A monad transformers library </b> </summary>
    
<br>

A library for composing monadic code using the [monad transformer abstraction model](https://en.wikipedia.org/wiki/Monad_transformer). 

</details>
<br>

### [Pars]()

<details>
  <summary> <b> A monadic parser combinators library </b> </summary>
    
<br>

A monadic parser combinator library influenced by the Haskell library [parsec](https://hackage.haskell.org/package/parsec), allowing for parser generation in Scheme 
using the powerful abstractions of monads and combinators.

</details>
<br>

### [Moxen]()

<details>
  <summary> <b> An optics library</b> </summary>
    
<br>

An optics library for Scheme, similar to Haskell's [lens](https://hackage.haskell.org/package/lens) and [optics](https://hackage.haskell.org/package/optics) libraries. 

</details>
<br>

### [Morpheme]()

<details>
    <summary> <b>A Recursion Schemes library </b> </summary>
    
<br>

A library containing common forms of recursion abstracted out into higher order functions, heavily based on ideas from category theory.
    
</details>
<br>


<br>



## Prolog <a name="Prolog"></a>

#### [Modal Tableux Solver]()

<details>
  <summary><b> A modal tableaux solver </b></summary>
    
<br>

A propositional modal logic tableaux proof system.

</details>
<br>
<br>

    
## Other Projects <a name="Other"></a>
<br>
<br>




## Notes and So On <a name="Notes"></a>

#### [Logic Runs Through It](https://github.com/KripkesBeard/Logic-Runs-Through-It)

A collection of notes and worked solutions to various textbooks on mathematical logic and theoretical computer science.
<br>

#### [Lambdas, Types, and Registers](https://github.com/KripkesBeard/Lambdas-Types-and-Registers)

A collection of notes and worked solutions to various textbooks on my favorite programming languages, compiler theory, and eventually Knuth's The Art of Programming
<br>

#### [SICP in Context]()
    
<details>
  <summary><b> Explanations and contextualizations of the key ideas in SICP </b></summary>
    
<br>

*Structure and Interpretation of Computer Programms* by Abelson, Sussman & Sussman is one of the greatest books ever written, and this fact is well known. My biggest
criticism of the book is that it can be hard to place the ideas it teaches into context. Many of the ideas the book discusses are ideas you would learn under
different names or less technically in a more traditional introduction to programming. This project is my attempt to place each section/chapter of the book into
more traditional jargon and to have it act as a reference guide for anyone trying to work through SICP. Importantly, this is not a distillation of or substitute for the book;
my goal is to outline sign posts of the main ideas and to put them into the context of every day programming terminology. One quick example: Despite having an entire
section, comprising five chapters, on the topic of abstract data representation, the book does not use the phrase "abstract data type" once (it does appear in the
title of a paper in the bibliography). Surely this can be a cause for confusion (it was for me personally at the start of my CS career), "are these data abstractions 
the same as the abstract data types I'm learning about everywhere else?" Of course they are, but the book does not say so. One goal of SICP in Context is to clear up these 
types of confusions.

</details>
