# Regex Hex Value Tutorial

## Introduction

You are invited to the regex tutorial. The regular phrase /#?([a-f0-9]6|[a-f0-9]3)$/, which is used to match a hex value, will be discussed in this tutorial. We will dissect each part of the regular expression and describe how it works. You will have a thorough understanding of how this regex operates and how it may be applied in JavaScript by the end of this course.

## Summary

The regular expression /#?([a-f0-9]6|[a-f0-9]A valid hex color value is represented by a string beginning with an optional # character, followed by either a 6-character or 3-character sequence made up of lowercase letters a-f and digits 0-9. The string "3" is intended to match this value.

## Table of Contents

- [Anchors](#anchors)
- [Optional Character](#optional-character)
- [Character Class](#character-class)
- [Quantifiers](#quantifiers)
- [Grouping and Alternation](#grouping-and-alternation)
- [Anchors (End)](#anchors-end)
- [Example](#example)
- [Author](#author)

## Regex Components

### Anchors

1. Anchors <a name="anchors"></a>
The regex starts with the ^ character, often known as a caret or anchor. It denotes where the input string begins. In this instance, it makes sure that the string's first character matches the hex value.

Example:

const regex = /^#?([a-f0-9]{6}|[a-f0-9]{3})$/;

console.log(regex.test("#FF0000")); // true
console.log(regex.test("FF0000")); // false


### Optional Character

2. Optional Character <a name="optional-character"></a>
The character #?, which denotes that the character is optional, comes after the anchor. The quantifier "?" indicates either 0 or 1 instances of the previous character or group. It permits the hex value in this instance to begin with # or without.

Example:

const regex = /^#?([a-f0-9]{6}|[a-f0-9]{3})$/;

console.log(regex.test("#FF0000")); // true
console.log(regex.test("FF0000")); // true
console.log(regex.test("#123ABC")); // true
console.log(regex.test("123ABC")); // true


### Character Class

3. Character Class <a name="character-class"></a>
There are two numbers inside the parentheses: '[a-f0-9]{6}|[a-f0-9]{3}'. This character class corresponds to a certain set of characters. It consists of two options, divided by the pipe (|) sign.
* '[a-f0-9]{6}' matches a string of exactly 6 characters, which can be any digit from '0' to '9' or any lowercase letter from 'a' to 'f'. This illustrates the situation where the hex value has six characters.
* '[a-f0-9]{3}' matches an exact 3-character sequence that follows the same pattern as above. This illustrates the situation where the hex value has three characters.

Example:

const regex = /^#?([a-f0-9]{6}|[a-f0-9]{3})$/;

console.log(regex.test("#FF0000")); // true
console.log(regex.test("#F00")); // true
console.log(regex.test("#123ABC")); // false
console.log(regex.test("#ABC")); // false


### Quantifiers

4. Quantifiers <a name="quantifiers"></a>
The quantifiers '{6}' and '{3}' indicate the precise number of times the previous character or group occurs. In this instance, depending on the hex value format, they make sure that the character class matches either 6 or 3 characters.

Example:

const regex = /^#?([a-f0-9]{6}|[a-f0-9]{3})$/;

console.log(regex.test("#FF0000")); // true
console.log(regex.test("#F00")); // true
console.log(regex.test("#123ABC")); // false
console.log(regex.test("#ABC")); // false


### Grouping and Alternation

5. Grouping and Alternation <a name="grouping-and-alternation"></a>
Within parenthesis (), the character class '[a-f0-9]{6}|[a-f0-9]{3}' is enclosed. As a result, we can use the '|' alternation operator to match either the 6-character or 3-character hex value format and produce a capturing group.

Example:

const regex = /^#?([a-f0-9]{6}|[a-f0-9]{3})$/;

const input = "#FF0000";
const match = regex.exec(input);

console.log(match[1]); // FF0000


### Anchors (End)

6. Anchors (End) <a name="anchors-end"></a>
The '$' character, another anchor, marks the conclusion of the regex. It indicates that the input string has ended. In this instance, it ensures that the hex value is matched all the way through the string and forbids the inclusion of any more characters.

Example:

const regex = /^#?([a-f0-9]{6}|[a-f0-9]{3})$/;

console.log(regex.test("#FF0000")); // true
console.log(regex.test("#F00")); // true
console.log(regex.test("#1234567")); // false
console.log(regex.test("00FF00")); // false


### Example

7. Example <a name="example"></a>
Let's take a look at an example to illustrate how this regex works:

const regex = /^#?([a-f0-9]{6}|[a-f0-9]{3})$/;

console.log(regex.test("#FF0000")); // true
console.log(regex.test("#F00")); // true
console.log(regex.test("#1234567")); // false
console.log(regex.test("00FF00")); // false

In the last example, we created a regex object using the notation /.../ and used the test() method to test different strings against it. The outcomes show whether or not the tested string corresponds to the hex value pattern.

## Author

8. Author <a name="author"></a>
The author of this tutorial is Andrew Breytenbach. More of my work is available on GitHub: https://github.com/andrewbreytenbach.

Congratulations! You have mastered the knowledge of the many parts of the regex '/#?([a-f0-9]{6}|[a-f0-9]{3})$/' used for matching a hex value. In JavaScript, regular expressions are effective tools for pattern matching and validation. With this understanding, you can use regex in your web development projects for a variety of circumstances.
