<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Implementing microservices in Scala and Akka](#implementing-microservices-in-scala-and-akka)
- [Culture of extremes](#culture-of-extremes)
  - [ACID transactions](#acid-transactions)
  - [Everything was eventually consistent](#everything-was-eventually-consistent)
  - [Other extreme: Monolith vs Microservices](#other-extreme-monolith-vs-microservices)
    - [Monolith](#monolith)
    - [Microservice](#microservice)
  - [so how do we define a microservice?](#so-how-do-we-define-a-microservice)
- [What domain driven design offers?](#what-domain-driven-design-offers)
  - [Bounded context](#bounded-context)
  - [Start with bounded context size microservies](#start-with-bounded-context-size-microservies)
  - [Ubiquitous language](#ubiquitous-language)
  - [Microservice owns database](#microservice-owns-database)
  - [Actors](#actors)
    - [DON'T:](#dont)
  - [Rapids](#rapids)
  - [Rivers](#rivers)
  - [Ponds](#ponds)
  - [Channel services](#channel-services)
  - [Features of actor model servies](#features-of-actor-model-servies)
- [How to implement microservices with Scala and Akka](#how-to-implement-microservices-with-scala-and-akka)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Implementing microservices in Scala and Akka

- author of
  - [implementing domain driven
  design](http://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)
  - reactive messaging patterns
  - domain driven design distilled

# Culture of extremes

## ACID transactions
- Does everything actually have to be acid?
- How did business work before acid?
  - it was analog in the beginning, paper etc
  - it was slow
  - transactions were 'long'
- Do we really need transactional integrity around everything?

## Everything was eventually consistent

- Even now everything can be eventually consistent
- Who do we ask?
  - Domain experts: the business
  - And you can show how eventual consistency can be 'good' and otherwise


## Other extreme: Monolith vs Microservices

- either one or another ... no middle ground
- where is the practical balance?

### Monolith

- Big ball of mud.
- Multiple domain models which should be separated are all entangled together. To
  the point you cannot reason about it.
- It's worse than mud

### Microservice

- what is the size?
- how many do you need?
- 'fred george' - self proclaimed to coin in the term 'microservice'
  [vimeo.com/79866979](https://vimeo.com/79866979)

## so how do we define a microservice?

- think infrastructure, you will need it to run your 'microservice'.
- How many of those you will need?

# What domain driven design offers?

## Bounded context

- what is the size?
- is it one entity?
- Ask your ubiquitous language
- linguistic components are cohesive

## Start with bounded context size microservies

- it is bigger than one item
- far smaller than monolith

## Ubiquitous language

- it is greater than entities names
- command messages
  - PlanBacklogItem - what to do
- event messages
  - BacklogItemPlan - what happened

## Microservice owns database

- owns event journal
  - sequential journal of all events: even streams
  - FIFO
- Query model

## Actors

- asynchronous services

### DON'T:

  - request -> entity1 -> request entity2

## Rapids

- everything publishes to the same 'bus'
- example:
  - rest (atom)
  - kafka
  - high preformace

## Rivers

- subscribe to the events
- filter out what they dont care
- convert events to commands if applicable

## Ponds

- get command -> generate event store to jouranl -> back to RAPIDS

## Channel services


## Features of actor model servies

- Responsive
  - order of 10ms
- Resilient
  - parent crash detection, not client
  -  best knows what to do
- client only understands - honored or not
  - can react as retry or show error to the user
- Elastic
- Message driven
  - actors are message driven
  - rapids are message driven

# How to implement microservices with Scala and Akka

1. Command comes in : Create product
2. Emit: product created, discussion requested. That goes to the Rapids
3. Discussion requested goes to Collab microservice
4. Emit: discussion started => RAPIDS
5. Read: Discussion Started in the product Microservice
