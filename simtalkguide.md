# SimTalk 2.0 Style Guide

- [1 Introduction](#s1-introduction)
- [2 SimTalk Language Rules](#s2-simtalk-language-rules)

* [2.1 Default Parameter Values](#s2.1-default-parameter-values)
* [2.2 Referenced Parameters](#s2.2-referenced-parameters)
* [2.3 True/False Evaluations](#s2.3-true-false-evaluations)
* [2.4 Strings](#s2.4-strings)
* [2.5 Parentheses](#s2.5-parentheses)
* [2.6 Error Handling](#s2.6-error-handling)

- [3 SimTalk Style Rules](#s2-simtalk-style-rules)

* [3.1 Semicolons](#s3.1-semicolons)
* [3.2 Line Length](#s3.2-line-length)
* [3.3 Indentation](#s3.3-indentation)
* [3.4 Blank Lines](#s3.4-blank-lines)
* [3.5 Whitespace](#s3.5-whitespace)
* [3.6 Naming](#s3.6-naming)
* [3.7 Method Length](#s3.7-method-length)
* [3.8 Type Annotations](#s3.8-type-annotations)
* [3.9 Parameters](#s3.9-parameters)
* [3.10 Default Parameter Values](#s3.10-default-parameter-values)
* [3.11 Return Value Type](#s3.11-return-value-type)
* [3.12 Comments and Docstrings](#s3.12-comments-and-docstrings)

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

```
param x: string, y:integer := 4
```

If the method is invoked with a single argument, y will be assigned the value of 4. If it's called with two arguments, y takes on the value of the second argument.

<a id="s2.2-referenced-parameters"></a>

### 2.2 Referenced Parameters

As outlined, utilizing ["byref"](https://docs.sw.siemens.com/de-DE/doc/297028302/PL20230511801658226.PlantSimulation/id56084) allows for passing parameters by reference, enabling direct access to these parameters, which can potentially affect the calling method. It's advisable to exercise caution when using referenced parameters due to their complexity in identification and readability. In the absence of programmatically available classes in SimTalk, consider its application only when a custom class instance would be returned in a higher programming language to maintain clarity and coherence.

<a id="s2.3-true-false-evaluations"></a>

### 2.3 True/False Evaluations

Prefer to use worded Boolean comparisons for enhanced readability and clarity in your code. Instead of relying solely on symbols like "=" or "/=", consider using their worded equivalents such as "not". This practice makes the code more understandable, especially for those who may not be familiar with symbolic representations.

```
Yes:
if not isObject(truck)
    return false
elseif isObject(truck)
    return true
end
```

```
No:
if isObject(truck) = false
    return false
elseif isObject(truck) = true
    return true
end
```

<a id="s2.4-strings"></a>

### 2.4 Strings

Utilize the `to_str()` method for string formatting, even when all parameters are strings. Concatenating two strings with the + operator is permissible. Avoid exceeding this method of string concatenation.

```
Yes:
x = to_str(“root.”, objectName, “.stats”)
x = object + “.stats”
```

```
No:
x = “root.” + objectName + “.stats”
```

<a id="s2.5-parentheses"></a>

### 2.5 Parentheses

In SimTalk, parentheses aren't mandatory for method calls when no parameters are passed. However, they should be employed for methods that don't function like attributes. Even if the method executes code, it's treated as an attribute when used in this manner.

```
Yes:
truck.getColor
truck.driveToHome()
```

```
No:
truck.getColor()
truck.driveToHomePosition
```

<a id="s2.6-error-handling"></a>

### 2.6 Error Handling

<a id="s2-simtalk-style-rules"></a>

## 3 SimTalk Style Rules

<a id="s3.1-semicolons"></a>

### 3.1 Semicolons

With SimTalk 2.0 it is not required to terminate lines with semicolons. So don't do it.

<a id="s3.2-line-length"></a>

### 3.2 Line length

<a id="s3.3-indentation"></a>

### 3.3 Indentation

When structuring code, it's recommended to indent code blocks using either a tabulator or four spaces. Consistent indentation enhances code readability and maintains uniformity across projects. This practice also aids in debugging and understanding code structure more effectively. Indent code blocks with tabulator or 4 spaces.

```
Yes:
if x > 4
    x += 1
end
```

```
No:
if x > 4
x + = 1
end
```

<a id="s3.4-blank-lines"></a>

### 3.4 Blank Lines

Ensure one blank space between top-level definitions, including docstrings or parameters, for clarity and organization. Avoid using blank lines after default operators like if-statements or loop definitions to maintain a clean structure. Utilize single blank lines judiciously within functions to enhance readability and separate logical sections as needed.

<a id="s3.5-whitespace"></a>

### 3.5 Whitespace

Adhere to standard typographic rules regarding the use of spaces around punctuation marks. Ensure there is no whitespace inside parentheses, brackets, or braces to maintain consistency and readability in code formatting.

```
Yes:
truck.returnHome(lastStations[1], [Station1, Station2])
```

```
No:
truck.returnHome(lastStations[ 1 ], [ Station1, Station2 ])
```

No whitespace before a comma, semicolon, or colon. Do use whitespace after a comma, or colon, except at the end of the line.

```
Yes:
if x > 4:
    print(to_str(x, y))
end
```

```
No:
if x > 4:
    print( to_str( x , y))
end
```

No whitespace before the open parentheses / bracket that starts an argument list or indexing.

```
Yes:
truck.returnHome(4)
```

```
No:
truck.returnHome( 4 )
```

Surround operators of each kind with a single space on either side of the assignment

```
Yes:
x := 4
x > y
x += 10
x: integer := 4
```

```
No:
x:=4
x>y
x+=10
x : integer:=4
```

<a id="s3.6-naming"></a>

### 3.6 Naming

`methodName`, `AttributeName`, `InstanceName`, `localVariableName`, `CONSTANT_NAME`

When naming methods and variables, prioritize descriptive names over abbreviations. Avoid ambiguous or unfamiliar abbreviations that may confuse readers outside your project. Additionally, refrain from abbreviating words by deleting letters within them to ensure clarity and understanding throughout your codebase.

In case a method returns a Boolean, tend to name the method “is…”. For example: isFree.

<a id="s3.7-method-length"></a>

### 3.7 Method Length

It's advisable to favor small, focused methods for improved code maintainability and readability. While this approach may seem tedious in SimTalk due to the requirement of each callable method having its own Method object instance, it offers long-term benefits. Although there's no strict limit, methods exceeding 40 lines should be evaluated for potential splitting to enhance clarity and manageability.

<a id="s3.8-type-annotations"></a>

### 3.8 Type Annotations

With SimTalk, type annotations are essential, and there should be no whitespace before the colon following the variable name. After a whitespace, the type annotation should be placed. For variables with default values, ensure adherence to the whitespace rules for operators to maintain consistency and readability in your code.

```
Yes:
var variableName:integer
var variableName:integer := 4
```

```
No:
var variableName : integer:=4
```

<a id="s3.9-parameters"></a>

### 3.9 Parameters

Position parameter definitions immediately after the docstring without inserting a blank line in between. While it's feasible to write parameters of the same type without individual type annotations, it's not advisable. Opt for a type annotation for each parameter separately to enhance clarity and maintain consistency in your code.

```
Yes:
param x:integer, y:integer, truck:object
```

```
No:
param: x, y:integer, truck : object
```

<a id="s3.10-default-parameter-values"></a>

### 3.10 Default Parameter Values

```
Yes:
param x:integer := 4, y:integer := 0
```

```
No:
param x:integer:=4, y:integer:=0
```

<a id="s3.11-return-value-type"></a>

### 3.11 Return Value Type

Specify the type of the return value immediately after the parameter list if applicable, or directly after the docstring if no parameters are required. This ensures clear documentation and comprehension of the function's behavior and output.

```
Yes:
-> boolean
OR:
param x:integer := 4, y:integer := 0 -> boolean
```

```
No:
->boolean
```

<a id="s3.12-comments-and-docstrings"></a>

### 3.12 Comments and Docstrings

<a id="s3.12.1-block-and-inline-comments"></a>

### 3.12.1 Block and Inline Comments

Comments should be used in tricky parts of code. Do not use the ´--´ operator for comments, instead use ´//´.

```
// This section calculates the minimum distance
var distance:length := 4 // Minimal distance is 4

distance += (truck.speed / 10) * (truck.speed / 10) // Basic formula for braking distance
```

<a id="s3.12.2-docstrings"></a>

### 3.12.2 Docstrings

For every method featuring non-obvious logic or significant size, include a docstring at the top of the source code. This docstring should offer adequate information to call the method without the need to delve into its source code. The docstring format comprises a trailing blank comment line followed by a concise description of the method's purpose, concluding with a trailing dot.

The only mandatory part is the method description. Judge if the rest is required.

```
//
// Calculates the minimal distance required between two trucks and humans.
//
// Parameters:
// x: the current distance to another truck.
// y: the current distance to the closest human.
// truck: the current truck.
//
// Returns:
// Returns the minimal distance required between two trucks and humans.
//
// Raises:
// RuntimeError: No truck is given.
```

<a id="s3.12.2-todo-comments"></a>

### 3.12.3 TODO Comments

Employ TODO comments to denote sections of code that are temporary, short-term solutions, or deemed "good-enough" but not perfect. This practice helps identify areas needing improvement or future attention while maintaining code clarity and progress.

```
// TODO: Calculate track length instead of estimating
```
