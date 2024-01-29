# SimTalk 2.0 Style Guide

- [1 Introduction](#s1-introduction)
- [2 SimTalk Language Rules](#s2-simtalk-language-rules)

* [2.1 Default Parameter Values](#s2.1-default-parameter-values)
* [2.2 Referenced Parameters](#s2.1-referenced-parameters)

- [3 SimTalk Style Rules](#s2-simtalk-style-rules)

<a id="s1-introduction"></a>

## Introduction

SimTalk is a programing language by Siemens AG used to extend functionality of Tecnomatix Plant Simulation.
It is to mention that this document is neither connected to Siemens AG in any way nor an official release.
The guide is oriented on the official docs and example models provided by Siemens AG.
With the release of SimTalk 2.0 a lot of changes in the were made, which can be found [here](https://docs.sw.siemens.com/de-DE/doc/297028302/PL20230511801658226.PlantSimulation/SimTalk_20_and_SimTalk_10_Compared).
SimTalk 2.0 enables easier formatting and less code. That’s why this style guide refers to version 2.0.

<a id="s2-simtalk-language-rules"></a>

## 2 SimTalk Language Rules

<a id="s2.1-default-parameter-values"></a>

### 2.1 Default Parameter Values

It's permissible to specify values for variables at the end of a function's parameter list.

```python
param x: string, y:integer := 4
```

If the method is invoked with a single argument, y will be assigned the value of 4. If it's called with two arguments, y takes on the value of the second argument.

<a id="s2.1-referenced-parameters"></a>

### 2.1 Referenced Parameters

As outlined, utilizing ["byref"](https://docs.sw.siemens.com/de-DE/doc/297028302/PL20230511801658226.PlantSimulation/id56084) allows for passing parameters by reference, enabling direct access to these parameters, which can potentially affect the calling method. It's advisable to exercise caution when using referenced parameters due to their complexity in identification and readability. In the absence of programmatically available classes in SimTalk, consider its application only when a custom class instance would be returned in a higher programming language to maintain clarity and coherence.

<a id="s2-simtalk-style-rules"></a>

## 3 SimTalk Style Rules
