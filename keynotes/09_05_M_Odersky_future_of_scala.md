<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Coming in 2016](#coming-in-2016)
  - [Scala 2.12](#scala-212)
  - [Beyond 2.12](#beyond-212)
  - [Other things coming in 2016](#other-things-coming-in-2016)
  - [Dot: Dependent object tracking](#dot-dependent-object-tracking)
      - [Why? Type Soundness:](#why-type-soundness)
  - [Dotty:  a working name for the new scala compiler](#dotty--a-working-name-for-the-new-scala-compiler)
    - [Why dotty important?](#why-dotty-important)
    - [What is the scala "character"](#what-is-the-scala-character)
    - [Goals of the further scala improvements](#goals-of-the-further-scala-improvements)
    - [Dotty: Dropped features](#dotty-dropped-features)
    - [Dotty: new fatures](#dotty-new-fatures)
    - [Improvements in details](#improvements-in-details)
    - [ADvances in tooling](#advances-in-tooling)
  - [FUTURE!](#future)
    - [Planned future](#planned-future)
  - [What about the guardrails](#what-about-the-guardrails)
  - [Read this](#read-this)
    - [Flexibility: blessing or a curse?](#flexibility-blessing-or-a-curse)
    - [Add alphanumeric for Symbolic operators](#add-alphanumeric-for-symbolic-operators)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Coming in 2016

- scala 2.12
- Dot and dotty
- scala center
- scala native

## Scala 2.12

- Optimized for Java 8
- 33 new features
- Programming in Scala third ed updated for 2.12

## Beyond 2.12

- focus on libraries
- study ways to revamp the collections
  - straw-man proposals under study
  - collect ideas and prototype solution
  - give nicer APIs
- better modularization: current binary is a big blob
- thinking about split:
  scala stdlib -> scala core and scala platform
- scala core: minimal
- Scala platform: a bigger than current stdlib

## Other things coming in 2016
- Scala.js -> 0.6.9
- SCalaNative, more details later.
- DOT and dotty

## Dot: Dependent object types

[Read Martin's blog about
DOT](http://www.scala-lang.org/blog/2016/02/03/essence-of-scala.html)

Finally have proven foundation for Scala. DOT calculus talks about a minimal
language subset that:

- can prove formally
- can encode the rest of the language with it
- this concludes 8 year effort

Opens the door to language work with much better confidence in the future.

#### Why? Type Soundness:

> if a term t has type T, and eval terminates: the result will
>   be a blue v of T.

## Dotty:  a working name for the new scala compiler

- builds on DOT
- generics are expressed as type members
- supports an evolution of the scala
- first dev preview coming soon
- targeted at contributors and experimenters
- wont be prod ready for a while, but welcome if you want experiment
- ~45kloc (compared to current compiler 75kloc)
- 2x faster than current (nsc) compiler

### Why dotty important?

- cleaner compiler gives a way to move forward faster
- evolve language more confidently
- already invested 3 years
- Martins goal: make Scala "best" programming language I know how to make

### What is the scala "character"

- Scala's Concepts:
  - functions
  - classes and objects
  - strict eval
  - local type inference
  - implicits
    - other languages move in the same space: example ocaml just added implicits
    - kotlin, swift also add similar features

### Goals of the further scala improvements

1. Deepen the synthesis of functional and modular programming
2. Improve the connection of Scala with its theoretical foundations
3. Improve the guarantees of the type system
4. But stays simple and approachable

### Dotty: Dropped features

- Procedure syntax
- DelayedInit
- Macros: current implementation is based on java reflection and it sucks.
- Early initializers: class C extends `{ val = e } with D`
- Existential types: `C[U] forSome { type U }`
- General type projection
  - `T # X`
  - showed to be unsound
  - projection `C # X` from class types C still available

### Dotty: new fatures

- Intersection types:`T & U`
  - replaces `T with U`
  - is commutative (!!!)
- Union types: `T | U`
  - avoid exploding huge lubs
- Function arity adaptation
  - `pairs.map((x,u) => x + u)` instead of have to type 'case' in some cases.
- trait params (make them more like classes)
- static methods and fields
  - `@static` (uses some underlying JVM magic for statics and may be more
    performant than normal object methods)
- multiversal Equality
  - type-safe ==, !=
- named type params
  - trait Map[type Key, type Value]
  - allows partial parametrization: specify some types
  - Map [Key = Int]
- non-blocking lazy vals

### Improvements in details

- Type system
  - influenced by DOT
  - better integration of type reinforcements
- Type inference
  - sub typing constraint solver
  - inference is simple to specify
- Implicit search
  - faster search algo
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
    - simpler
    - fewer dependences
    - safer: sandbox
    - restrict syntactic freedom
- Implicit Function Types

  ```
     type ctxs =  implicit context => s
      def f(x:T): ctxs = {
        ... implicitly [Context]  ...
        }
  ```

  - why?
    - allows abstraction over implicit parmas
    - eliminates boiler plate
- Effect system
  - implicit capabilities
  - new arrows:
    - `A => B` impure function
    - `A -> B` pure
  - WHY?
    - effects checking is very much in demand
  - can do better than monads
  - implicits are a natural fit
- Nullable types as union types
  - `T? = T  | Null`
  - types don't have null by default
  - values coming from Java get ? Automatically: `System.out: PrintStream?`
  - null dereferencing is an 'effect'
  - `System.out.println` is OK in impure code
  - Why?
    - null poses unsoundness problems
    - null-safety is conceptually easy once you have union types and effects
- Generic programming
  - scrap your boilerplate
  - product of sum interpretation
  - Tuples are HLists, but implemented more more efficiently
    - (S, T, U) = (S, (T, U))
- Better records
  - analogue of tuples but with labels

## What about the guardrails

- Scala premise: trust devs to do the right thing
- What if they don't?
- Can we agree on what the right thing is?

### Scala style

- Strategic scala style: [Principle of least power](http://www.lihaoyi.com/post/StrategicScalaStylePrincipleofLeastPower.html)

  > use the least powerful language feature to achieve the thing

- Make implicit conversion (from A to B) a style error if:
  - not defined in package containing A or B
  - is public

### Flexibility: blessing or a curse?

i.e.: `xs.map(f)` or `xs map f`
Proposal: `@infix` annotation to indicate that operator is supposed to be used
infix to let compiler warn you

### Add alphanumeric for Symbolic operators

 -  `@infix("append") def += (elem: T)`
