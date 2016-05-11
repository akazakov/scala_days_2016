<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Domain driven design](#domain-driven-design)
- [What is DD?](#what-is-dd)
  - [Ubiquitous language (UL)](#ubiquitous-language-ul)
    - [Case study: how to cook an egg: Language](#case-study-how-to-cook-an-egg-language)
  - [Bounded contexts](#bounded-contexts)
    - [Case study](#case-study)
  - [Domain building blocks](#domain-building-blocks)
    - [Case study](#case-study-1)
  - [Traditional layered arch](#traditional-layered-arch)
- [Onion Architecture](#onion-architecture)
  - [API](#api)
    - [Case study](#case-study-2)
- [Tiny types: wrappers](#tiny-types-wrappers)
- [Aggregate root features](#aggregate-root-features)
  - [Case study: aggregate root](#case-study-aggregate-root)
  - [Case study: frying pan](#case-study-frying-pan)
  - [Thin cake pattern](#thin-cake-pattern)
- [Conclusions](#conclusions)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Domain driven design

[github.com/WadeWaldron/scaladays2016](https://github.com/WadeWaldron/scaladays2016)

[blog
post](http://boldradius.com/blog-post/VCRYijIAAHhescgX/domain-driven-design-through-onion-architecture)

Usually associated with:

- CQRS
- Even sourcing
- Onion Architecture

But not required

We'll focus on the Domain driven design itself and Onion arch.

"How to fry an egg with domain driven design and onion architecture"


# What is DD?

- Doaain: spere of knoewledge
- DDD: software that focuses on the primary domain
- DDD benefit is that it is less likely to change if you focus on the core
  domain.
- There can be multiple implementations of the Core Domain: Software, doc etc.
- DDD requires a strong communication between domain experts and product team.
- Experts inform us about the core domain

## Ubiquitous language (UL)

- A Commmon language that can be used by the domain experts and the tech
  experts.
- Reflected in the software model

### Case study: how to cook an egg: Language

- nouns
  - cook
  - egg, sunny side up, scrambled...
- ...

## [Bounded contexts](http://martinfowler.com/bliki/BoundedContext.html)

- The setting or context where ideas from the UL apply
- There can be multiple
- In different contexts the language may be the same, but `concept` is different

### Case study

  - Food preparation
  - Grocery shopping
  - Washing dishes

## Domain building blocks

[blog](https://blog.lelonek.me/ddd-building-blocks-for-ruby-developers-cdc6c25a80d2#.2aelchdvj)

- Value Objects
- Entity
- Aggregate
- Service
- Repository
- Factory

### Case study

  - Cook, CookFactory, CookRepository
  - Egg, EggFactory
  ...

## Traditional layered arch

- Presentation
- Domain
- Data access

# Onion Architecture

- app is build around the domain
- outer layer depend and coupled to the inner lyers
- Inner layers are dceoupled from the outer
- Inner layers define interfaces that may be implemented in the outer layers

Q: how is it different from layered architecture? :)

- Dependencies are pushed to the outside, so infrastructure lives on the outside

## API

 - decoupling the domain
 - provide a single consistend code interface
 - Domain can be restructured

### Case study

```
fry(egg): Fried egg
```

This is pretty bad, as it does not represent how it actually happens.

Lets improve

```
prepareEgg(style: EggStyle): Future[CookedEgg]
```

# Tiny types: wrappers

- use AnyVal to avoid memory explosion

```
case class CookId(value: string) extends AnyVal
```


# Aggregate root features

- What is a valid aggregation?
- Who/what you will be interacting the most?

- Aggregates other entities
- Controls access to their entities
- Other entities are forbidden from accessing the child entities without going
  through the root.

## Case study: aggregate root

- Cook?
- we go through the cook to do anything

## Case study: frying pan

- use types to represent full and empty frying pans!
- now you have compile time checking of the domain model!


## Thin cake pattern

- Adam Worsky
[blog post](http://www.warski.org/blog/2014/02/using-scala-traits-as-modules-or-the-thin-cake-pattern/)

# Conclusions

- DDD is evolutionary
- DDD makes it very portable
- DDD friendly to refactoring
