# Coming in 2016

- scala 2.12
- Dot and dotty
- scala center
- scala native

## Scala 2.12

- Optimized for Java 8
- 33 new features
- Programming in scala third ed updated for 2.12

## Beyond 2.12

- focus on libraries
- study ways to revamp the collections
  - strawman proposals under study
  - collect ideas and prototype solution
  - give nicer apis
- better modularization: current binary is a big blob
- thinking about split:
  scala stdlib -> scala core and scala platform
- scala core: minimal
- scala platform: a bigger than current stdlib

## Other things coming in 2016
- Scala.js -> 0.6.9
- SCalaNative, more details later.
- DOT and dotty

## Dot: Dependent object tracking

Finally have proven foundation for scala. DOT calculus talks about a minimal
lungauge subset that:

- can prove formally
- can encode the rest of the language with it
- this concludes 8 year effort

Opens the door to language work with much better confidence in the future.

#### Why? Type Soundness:

- if a term t has type T, and eval terminates: the result will
   be a blue v of T.

## Dotty:  a working name for the new scala compiler

- builds on DOT
- generics are expressed as type members
- supports an evolution of the scala
- first dev preview coming soon
- targeted at contributors and experimenters
- wont be prod ready for a while, but welcome if you want experiment
- ~45kloc (compared to current compiler 75kloc)
- 2x faster than current (nsc) compiler

### Why dotty improtant?

- cleaner compiler gives a way to move forward faster
- evolve language more confidently
- already invested 3 years
- Martins goal: make Scala "best" programming language I know how to make

### What is the scala "character"

- Scala Concepts:
  - functions
  - classes and objects
  - strict eval
  - local type inference
  - implicits
    - other languages move in the same space: example ocaml just added implicits
    - kotlin, switf also add similar features

### Goals of the further scala improvements

1. Deepen the sythetis of functional and modular programming
2. Improve the connection of Scala with its theoretical foundations
3. Improve the guarantees of the type system
4. But stays simple and approachable

### Dotty: Dropped features

- PRocedure syntax
- DelayedInit
- Macros: current implementation is based on java reflection and it sucks.
- Early initializers: class C extends { val = e } with D
- Existential types: C[U] forSome { type U }
- General type projection
  - T # X
  - showd to be unsound
  - projection C#X from class types C still available

### Dotty: new fatures

- Intersection types: replaces "T with U"
  - T & U
  - is commutative (!!!)
- Union types: T | U
  - avoid exploiding huge lubs
- Function arity adaptation
  - paris.map((x,u) => x + u)
- trait params (make them more like classes)
- static methods and fields
  - @static (uses some underlying JVM magic for statics and may be more
    performant than normal object methods)
- multiverasl Equality
  - type-safe ==, !=
- named type params
  - trait Map[type Key, type Value]
  - allows partial parametrization: specify some types
  - Map [Key = Int]
- non-blocking lazy vals

### Improvements in details

- Type system
  - influenced by DOT
  - better integration of type reinforcments
- Type inference
  - subtyping constraint solver
  - infrence is simple to specify
- Implicit search
  - faster search algo
  - better behaved for contr
- Value classes

### ADvances in tooling

- SBT  - basic integration
- REPL - works
- Jetbrains are working on the plugin
- Doc integration
- Linker
  - whole program analyzer
  - Uses TASTY for serialization
  make specialization better

## FUTURE!

### Planned future

- scala.meta
  - new meta programming
  - inline for inlining, meta for meta programming
  - run by interpreter, no reflection
  - meta uses quasi quotes for matching an construction
  - blackbox and annotation macros
  - WHY?
    - sipler
    - feweer depndences
    - safer: sandbox
    - restrict synctactic freedom
- Implicit Function TYpes

  ```
     type ctxs =  implicit context => s
      def f(x:T): ctxs = {
        ... implicitly [Context]  ...
        }
  ```

  - why?
    - allows abstraction over implicit parmas
    - eliminaties boiler plate
- Effect system
  - implicit capabilities
  - new arrows:
    - A => B impure function
    - A -> B pure
  - WHY?
    - effects checking is very much in demand
  - can do better than monads
  - implicits are a natural fit
- Nullable types as union types
  - T? = T  | Null
  - types dont have null by default
  - values coming from java get ? automatically: System.out: PrintStream?
  - null dereferecning is an 'effect'
  - System.out.println is ok in impure code
  - Why?
    - null poses unsoundness problems
    - null-safety is conceptually easy once you have union types and effects
- Generic programming
  - scrap your boilerplate
  - product of sum interpreetation
  - Tuples are HLists, but implemented more more efficiently
    - (S, T, U) = (S, (T, U))
- Better records
  - analogue of tuples but with lables

## What about the guardrails

- Scala premise: trust devs to do the right thing
- What if they dont?
- Can we agree on what the right thing is?

## Read this

- Strategic scala style: Principle of least power
  - use the least powerful language feature to achieve the thing

- Make implicit conversion (from A to B) a style error if:
  - not defined in package containing A or B
  - is public

### Flexibility: blessing or a curse?

ie: xs.map(f) or xs map f
Proposal: @infix annotation to indicate that operator is supposed to be used
infix to let compiler warn you

### Add alpanum for Symbolic operators

 -  @infix("append") def += (elem: T)
