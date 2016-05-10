<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Master scala with IntelliJ IDEA](#master-scala-with-intellij-idea)
- [General tips](#general-tips)
  - [Activator template for quick creation of the projects](#activator-template-for-quick-creation-of-the-projects)
  - [Do not use mouse! 'Find action' action](#do-not-use-mouse-find-action-action)
  - [Presentation assistant plugin](#presentation-assistant-plugin)
  - [Distractrion free mode](#distractrion-free-mode)
    - [Run Configurations: can also be invoked on demand](#run-configurations-can-also-be-invoked-on-demand)
    - [Tool windows on demand as well](#tool-windows-on-demand-as-well)
    - [Structure view on dmand](#structure-view-on-dmand)
    - [Other tool vindows can be opened with numbers (cmd + 1 etc)](#other-tool-vindows-can-be-opened-with-numbers-cmd--1-etc)
    - [For ones that cannot be opened with numbers you can open them via recent files](#for-ones-that-cannot-be-opened-with-numbers-you-can-open-them-via-recent-files)
    - [Navigation bar can be invoked on demand](#navigation-bar-can-be-invoked-on-demand)
  - [Search everywhere](#search-everywhere)
    - [Use Camel Humps to split the words](#use-camel-humps-to-split-the-words)
  - [Navigating Tabs](#navigating-tabs)
- [Scala specific](#scala-specific)
  - [Use postfix methods like .not](#use-postfix-methods-like-not)
  - [Use Inspect code for a problem](#use-inspect-code-for-a-problem)
  - [Use intentions: small refactorings](#use-intentions-small-refactorings)
  - [Explain scala code](#explain-scala-code)
  - [Macro annotationsa: @Cached to see what happens with your macros](#macro-annotationsa-@cached-to-see-what-happens-with-your-macros)
  - [Smart completion](#smart-completion)
  - [Debugging:  Mark object](#debugging--mark-object)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Master scala with IntelliJ IDEA
===============================

- Very few people are masters of the tool 80/20 rule
- this is one of the main reasons for this talk

# General tips

## Activator template for quick creation of the projects

## Do not use mouse! 'Find action' action

- find action action to find other actions from the keyboard

## Presentation assistant plugin

- shows shortcusts on the screen as they are bing typed

## Distractrion free mode

- see more code esp on the small screen
- requires to know shortcuts

### Run Configurations: can also be invoked on demand

### Tool windows on demand as well
- you can use speed search there and camelhumps

### Structure view on dmand

### Other tool vindows can be opened with numbers (cmd + 1 etc)

### For ones that cannot be opened with numbers you can open them via recent files

### Navigation bar can be invoked on demand

## Search everywhere

- 'double shift'
- looks everywhere, classes, symbols, files etc..
- which may be toom much

### Use Camel Humps to split the words

## Navigating Tabs

- Use recent files instead
- where you can use camel humps

# Scala specific

- IntelliJ can help to make your corde more 'readable'

## Use postfix methods like .not

- for example `isEmpty.not` IntelliJ will convert automatically

## Use Inspect code for a problem

- Can fix your code for you and the whole project

## Use intentions: small refactorings

- Light bulb in the IntelliJ will show some optimizations, press alt-enter to
  choose from different options of what can be done

## Explain scala code

- Desugaring and you can see what actually happens
- Only available in nightly builds, will be released soon

## Macro annotationsa: @Cached to see what happens with your macros

- Add '-Y ... ' to the build to generate AST as part fo teh compilation

## Smart completion

- Add imports automatically
- Can add Some automatically when needed, based on type

## Debugging:  Mark object

- When debugging can mark some object and observe it at some other breakpoint
- you can add some expression on it to watches

