# Regex Tutorial

This is a simple guide on regular expressions (Regex). We will be going over the regex expression for email validation.

## Summary

This tutorial will look at the following regex expression: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Each section goes over a specific part of the above regex expression.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

The regex has both anchors '^' and '$'. The '^' indicates starting of the string and '$' indicates the ending.

### Quantifiers

The expression uses the quantifier + to imply that the expresion before the @ can have one or more characters and the domain, expression between the @ and the ., can have one or more characters. The expression also uses the quantifier {2,6} to signify that the expression after the '.' must have 2 to 6 characters.

### OR Operator

| Acts like a boolean logic operator. It can be used like this "|" operator (logical OR) to match characters or expression of either the left or right of the | operator.

### Character Classes

A character class allows you to match any symbol from a certain character set. A character class is also called a character set.

The character class \d is used in this expression to match one digit from 0-9.
https://www.javascripttutorial.net/javascript-character-classes/

### Flags

A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behavior of a regular expression. It makes a regex search in a different way. A flag is denoted using a single lowercase alphabetic character.

n JavaScript regex, we have a total of 6 flags, each serving a different purpose.

Flag Name Modification
i Ignore Casing Makes the expression search case-insensitively.
g Global Makes the expression search for all occurrences.
s Dot All Makes the wild character . match newlines as well.
m Multiline Makes the boundary characters ^ and $ match the beginning and ending of every single line instead of the beginning and ending of the whole string.
y Sticky Makes the expression start its searching from the index indicated in its lastIndex property.
u Unicode Makes the expression assume individual characters as code points, not code units, and thus match 32-bit characters as well.

For example, if we were to give the flag i to the regex /a/, we'd write /a/i. And similarly in the case of new RegExp('a'), we'd write new RegExp('a', 'i')

To give multiple flags to a regex, we write them one after another (without any spaces or other delimiters).

### Grouping and Capturing

There are three capturing groups in the regex expression. The first group is ([a-z0-9_\.-]+) which matches the email name. The second group is ([\da-z\.-]+) which matches the email service, such as gmail or hotmail. The third group is ([a-z\.]{2,6}) which matches the expression after the . in the domain, such as .com or .ca

### Bracket Expressions

Bracket Expressions match any of the values within the brackets. The first bracket expression is [a-z0-9_\.-] which matches a character in a to z, 0 to 9, \_, -, and the '.'. The second bracket expression is [\da-z\.-] which matches any character from a-z and any digit from 0 to 9 and the '.' and '-'. The final bracket expression is [a-z\.] which matches any character from a to z and and the character '.'.

### Greedy and Lazy Match

There are a few Greedy matches in this regex. For example, the expression uses '+' in multiple places to imply that it will match one or more characters. The expression also uses the quantifier {2,6} to signify that the expression after the '.' must have 2 to 6 characters.

### Boundaries

The metacharacter \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.

There are three different positions that qualify as word boundaries:

1. Before the first character in the string, if the first
   character is a word character.
2. After the last character in the string, if the last  
   character is a word character.
3. Between two characters in the string, where one is a
   word character and the other is not a word character.

Simply put: \b allows you to perform a “whole words only” search using a regular expression in the form of \bword\b. A “word character” is a character that can be used to form words. All characters that are not “word characters” are “non-word characters”.

Exactly which characters are word characters depends on the regex flavor you’re working with. In most flavors, characters that are matched by the short-hand character class \w are the characters that are treated as word characters by word boundaries. Java is an exception. Java supports Unicode for \b but not for \w.

Most flavors, except the ones discussed below, have only one metacharacter that matches both before a word and after a word. This is because any position between characters can never be both at the start and at the end of a word. Using only one operator makes things easier for you.

Since digits are considered to be word characters, \b4\b can be used to match a 4 that is not part of a larger number. This regex does not match 44 sheets of a4. So saying “\b matches before and after an alphanumeric sequence” is more exact than saying “before and after a word”.

\B is the negated version of \b. \B matches at every position where \b does not. Effectively, \B matches at any position between two word characters as well as at any position between two non-word characters.

### Back-references

Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag. Here’s how: <([A-Z][a-z0-9]_)\b[^>]_>._?</\1>. This regex contains only one pair of parentheses, which capture the string matched by [A-Z][a-z0-9]_. This is the opening HTML tag. (Since HTML tags are case insensitive, this regex requires case insensitive matching.) The backreference \1 (backslash one) references the first capturing group. \1 matches the exact same text that was matched by the first capturing group. The / before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.

To figure out the number of a particular backreference, scan the regular expression from left to right. Count the opening parentheses of all the numbered capturing groups. The first parenthesis starts backreference number one, the second number two, etc. Skip parentheses that are part of other syntax such as non-capturing groups. This means that non-capturing parentheses have another benefit: you can insert them into a regular expression without changing the numbers assigned to the backreferences. This can be very useful when modifying a complex regular expression.

You can reuse the same backreference more than once. ([a-c])x\1x\1 matches axaxa, bxbxb and cxcxc.

Most regex flavors support up to 99 capturing groups and double-digit backreferences. So \99 is a valid backreference if your regex has 99 capturing groups.

### Look-ahead and Look-behind

Lookahead and lookbehind, collectively called “lookaround”, are zero-length assertions just like the start and end of line, and start and end of word anchors explained earlier in this tutorial. The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match. That is why they are called “assertions”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

Negative lookahead is indispensable if you want to match something not followed by something else. When explaining character classes, this tutorial explained why you cannot use a negated character class to match a q not followed by a u. Negative lookahead provides the solution: q(?!u). The negative lookahead construct is the pair of parentheses, with the opening parenthesis followed by a question mark and an exclamation point. Inside the lookahead, we have the trivial regex u.

Positive lookahead works just the same. q(?=u) matches a q that is followed by a u, without making the u part of the match. The positive lookahead construct is a pair of parentheses, with the opening parenthesis followed by a question mark and an equals sign.

You can use any regular expression inside the lookahead (but not lookbehind, as explained below). Any valid regular expression can be used inside the lookahead. If it contains capturing groups then those groups will capture as normal and backreferences to them will work normally, even outside the lookahead. (The only exception is Tcl, which treats all groups inside lookahead as non-capturing.) The lookahead itself is not a capturing group. It is not included in the count towards numbering the backreferences. If you want to store the match of the regex inside a lookahead, you have to put capturing parentheses around the regex inside the lookahead, like this: (?=(regex)). The other way around will not work, because the lookahead will already have discarded the regex match by the time the capturing group is to store its match.

Lookbehind has the same effect, but works backwards. It tells the regex engine to temporarily step backwards in the string, to check if the text inside the lookbehind can be matched there. (?<!a)b matches a “b” that is not preceded by an “a”, using negative lookbehind. It doesn’t match cab, but matches the b (and only the b) in bed or debt. (?<=a)b (positive lookbehind) matches the b (and only the b) in cab, but does not match bed or debt.

The construct for positive lookbehind is (?<=text): a pair of parentheses, with the opening parenthesis followed by a question mark, “less than” symbol, and an equals sign. Negative lookbehind is written as (?<!text), using an exclamation point instead of an equals sign.

## Author

This tutorial was created by [Priyaaaryan] (https://github.com/priyaaaryan).
