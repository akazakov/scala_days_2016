Roll you own shapeless
======================

> Shapeless is a remarkable framework.  It gives us the power to represent
> astonishingly rich constraints and generalize code over very broad structural
> classes, but it isn't magic!  The tools with which shapeless is crafted are
> present in your version of scalac just as much as they are in Miles Sabin's,
> and learning to take advantage of them unlocks a rich palette of expression
> otherwise untapped in the language.  In this talk, we will recreate some of
> the major elements of shapeless, learning how to harness a fully armed and
> operational type system, all while avoiding any hint of macro programming!
> Particular focus will be given to understanding the general patterns and ideas
> involved, and not just the end result.

# Shapeless

- Hlists and coproduct
  - and more
- Tools for library authors
- Idioms for type level programming
- No magic!
- in this talk we are going to do it ourselves!


## Append

- context independedn
  - Strong separation of concerns
- Same result regardless of scope
- Usable in arbitrary position
- Unfortunately: gone in dotty
- Limited to induction by open recursion
- no branching except by recursion point
  - No type equivavalence
- Cannot be paried with value transformations
  - except trivial structural transforms

### TYpe constrcutors are context -independecn
### Type classes are context depdnent

## Type level functions
- Ctx indep is goog
  - but limited
  - lambda at tyhe type level
- ctx depnedec is messy
  - but far more powerful
  - prolog at the type level - and that's what we gonna do

## CTX-dpe
- loose flexibility
  -tied functions declarations
  - structural decom is coupled to operation
- Wegain expession of arbitrary proofs
  - express facts, scaa assembels proof
  - towers of hanoi is pretty easy

# Roadmap

- append
- remove
-
## Hlist#remove

- remove implement via Remover context aware type class
-



