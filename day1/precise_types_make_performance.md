Precise types
=============

- [https://github.com/darkdimius](https://github.com/darkdimius)

## Source of slowdown

- libraries
  - written ineffeciently or users use them in stupid ways
- user code

## SCala tersness and type agnostic can be slow

- average example is 20x time slower than Java

```
val arr = (1 to 1000000).toArray
arr.reduce(_ + _).double / arr.length
```


## Costs (!!!)

- single boxing (alloc)
- 5 dynamic dipatch
- 15 static dipatch
- 20 additions

## JVM does not support most fo the Scala higher level features.

- hirhet order type
- generic methods
- multiple inheritance


## Gnerics

- Generics are erased!!

```
def plus[T](a: T, b:T)
```
is very slow!

## What do do?

- you can of course overload all of them
- total 10times
- if you have n params 10^n specializations :(
- not practical

## You dont need to specialize all

- you can add annotation for stuff that is speicalized `@specialized`
- can specify what types to be used
- no inheritance :(


## @Miboxed

- 3^n instead of 3^n
- preformance hit
- has provlmes with arrays

## @Specialize/miniboxing breaks modularity

- since you have to guess as an author of the library


## Lookup

- ScalaBlitx
