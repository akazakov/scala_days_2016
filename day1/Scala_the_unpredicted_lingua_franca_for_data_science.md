Scala: The Unpredicted Lingua Franca for Data Science
=====================================================

Distributed data science and how it became to be
-------------

- IS the new interpretation of big data

## Why distributed computing became big data?

- Big data is the visible part of the iceberg.
- Big data is "business"
- Google: is big data. The wanted to process and aggregate everything
- Why did they invent all the HPC stuff?
- Well the did not :)
- So what Google did?
  - They 'harmonized' they way you worked with HPC
  - made it simple
  - make it resilient

### Then Hadoop

- implemented Google MapReduce
- open source & based on JVM
- JVM is crucial
  - Enterprise was familiar
- Drawbacks:
  - API is clunky
  - Programmers don't like it

### Then spark

- added speed (who cares ?:)
- added simplicity! - which is awesome
  - easy to install
  - REPL
  - simple API (for example word count is two lines)
  - familiar API to the normal programmers of python, ruby etc.

## Okay, now we can do data scinece easily and fast


## Why scala for DataScience?

See speaker spark notebook here [github.com/data-fellas/scala-for-data-science](https://github.com/data-fellas/scala-for-data-science)
Play it with
[https://github.com/andypetrella/spark-notebook](https://github.com/andypetrella/spark-notebook)

### Barriers for adoption of scala distributed data science

- Complexity
  - A lot of tools, serialization etc
  - UI: DataScience people are used to a certain UI, like python notebook
  - Language: they are used to R and Python

### Why scala is a good choice?

- Focus on the team productivity
  - JVM

### What is a big data team?

- A mix of IT and data scientists
- The data is changing fast these days, so data scientist need to produce
  "services" for other applications to use the BigData platform.
- So the team needs to be agile

### PySpark, SparkR, DataFrame

- May provide somewhat compatability between different languages
- But those are not great because they are only layers on top of actual
  implementation which is in scala
- not ready for enterprise
- since its a layer latest features come late
- things break
- performance suffer
- and you are limited by the 'features' of those framework

### What is missing in Scala/JVM?

- Tooling
  - easy install, configure etc
- port models
  - Need to provide an easy way to port existing python stuff etc.
- and invent new models for the platforms it will run on
  - keep in mind distributed nature
  - streaming etc

### Initiatives

  - DL4J
  - OptiML
  - Streaming clustering: G-Stream, Mean-Shift-LSH, SOM-MR
  - MLlib - heck spark-packages.org
  - Spark Notebook
  - Figaro - graph computing and ML

