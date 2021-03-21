---
title: "A Swift language Primer"
weight: 21
---

# A Swift Language Primer

This document serves as a basic overview of the most important features and paradigms behind the Swift programming language. It provides some explanation about how each part of the language works and what syntax to use.

## Variables and constants

Swift differentiates two different types of variables using two different keywords when defining them. A variable or constant can be defined without initialising it, but if it is expected, that the variable will contain no value anytime during runtime, it has to be declared an `optional` using a special `?` syntax. Swift is a strong-typed, type-safe language, which means that each variable or constant has to be given a specific type, which it never can change during runtime. Types can either be inferred by defining the variable with an initial value, or given during definition.

```swift
// Definition of a constant with inferred type of String
let const = "This is a constant"
// Definition of a variable with inferred type of Int
var variable = 100
// Definition of an uninitialized variable with explicit type of Double
var inferred: Double
// Definition of an optional variable with given type of String
var optional: String?
```

Swift doesn’t implement special mutable or immutable collections. They are determined by initialising them as either a variable or constant.

```swift
let immutableArray = [1, 2, 3, 4]
var mutableArray = [1, 2, 3, 4]
```

## Operators

Swift comes with all sorts of operators already build in. A lot of these standard operators can be applied to different kinds of types. This part only covers the basic syntax of each operator. Their special appliances on different types will be covered during the description of the specific type in the next chapter.

### Assignment operator

This operator is used to assign values to variables, constants or properties.

```swift
var myString = „This is a string“
```

### Arithmetic operators
These operators are mostly used to perform arithmetic calculations, but could be applied to non numeric types.
```swift
a + b		// Addition
a - b		// Subtraction
a * b		// Multiplication
a / b		// Division
```

### Compound assignment operators
Just like in other languages, Swift supports compound assignments. These take the value of a variable, perform an arithmetic operation on it and reassign the variable with the result. Compound assignments work with all four arithmetic operators.
```swift
var a = 1
a = a + 1		// Is equivalent to
a += 1
```

### Remainder operator
This operator returns the remainder of a division. It’s better known as the `modulo` operator.
```swift
10 % 3	// Evaluates to 1
```

### Comparison operators
These operators perform a logical comparison between two objects and return a boolean value.
```swift
a == b	// a equals b
a != b	// a unequals b
a < b		// a is smaller then b
a <= b	// a is smaller or equal to b
a > b		// a is greater then b
a >= b	// a is greater or equal to b
```

### Ternary conditional operator
This operator evaluates a boolean value or expression and assigns either a value A or a value B to a variable, based on the boolean	value.
```swift
var numberA = 10
var numberB = 3
var comparison = ((numberA > numberB) ? "A greater then B" : "B greater then A")
``` 

### Logical operators
Swift uses logical operators over keywords. These operators can be used to form any logical expression, following the rules of basic Boolean algebra. Unlike Python, boolean operations can only be performed on type boolean values, not on the integers 0 and 1.
```swift
var t = true
var f = !t		// The NOT operator (Expression evalueates to false)
var a = t && f	// The AND operator (Expression evalueates to false)
var o = t || f	// The OR operator (Expression evalueates to true)
```

### Ranged operators

Ranged operators provide a way of dealing with ranges between multiple objects as they are typically used in iterations or loops. We will deal with these concepts in a later chapter and only look at the basic syntax of different ranges. Ranges in Swift come in one of two kinds. Either a `closed` or a `half-open` range, which determines wether the end point of the range is included or not.
```swift
1...5		// Closed range operator returning the values 1, 2, 3, 4, 5
1..<5		// Half-open range operator returning the values 1, 2, 3, 4
```
