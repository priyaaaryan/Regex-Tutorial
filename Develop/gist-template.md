# Regex Tutorial

This is a simple guide on regular expressions (Regex). We will be going over the regex expression for email validation.

## Summary

This tutorial will look at the following regex expression: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Each section goes over a specific part of the above regex expression.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

The regex has both anchors '^' and '$'. The '^' indicates starting of the string and '$' indicates the ending.

### Quantifiers

The expression uses the quantifier + to imply that the expresion before the @ can have one or more characters and the domain, expression between the @ and the ., can have one or more characters. The expression also uses the quantifier {2,6} to signify that the expression after the '.' must have 2 to 6 characters.

### Character Classes

The character class \d is used in this expression to match one digit from 0-9.

### Grouping and Capturing

There are three capturing groups in the regex expression. The first group is ([a-z0-9_\.-]+) which matches the email name. The second group is ([\da-z\.-]+) which matches the email service, such as gmail or hotmail. The third group is ([a-z\.]{2,6}) which matches the expression after the . in the domain, such as .com or .ca

### Bracket Expressions

Bracket Expressions match any of the values within the brackets. The first bracket expression is [a-z0-9_\.-] which matches a character in a to z, 0 to 9, \_, -, and the '.'. The second bracket expression is [\da-z\.-] which matches any character from a-z and any digit from 0 to 9 and the '.' and '-'. The final bracket expression is [a-z\.] which matches any character from a to z and and the character '.'.

### Greedy and Lazy Match

There are a few Greedy matches in this regex. For example, the expression uses '+' in multiple places to imply that it will match one or more characters. The expression also uses the quantifier {2,6} to signify that the expression after the '.' must have 2 to 6 characters.

## Author

This tutorial was created by [Priyaaaryan] (https://github.com/priyaaaryan).
