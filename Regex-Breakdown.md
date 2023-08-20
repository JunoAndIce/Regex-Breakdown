# REGEX's Explained (Hex-Values)

This document will explain the syntax of a regex, and how each part of it works to allow us to check if strings match our specified parameters.

## Summary

The Regex we will be exploring today is the Hex Value Regex: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`'

A normal hex value has this syntax: `#ff0099`.

Hex values can also be written with three characters: `#f09`

This hex value gives us hot pink.

In our regular expression, regex for short, we have one group seperated by an or oeprator `|`.

`[a-f0-9]{3}` - This constraint only looks for strings following these specific rules. Only a character of that is lowercase between `[a-f]` and only integers between `0-9` will be matched. The string must also be a maximum of six characters denoted by the `{6}` at the end of the group.

`[a-f0-9]{3}` - This is the same as the above. The only difference is the `{3}` in this case. The string will only match with a maximum of three.

Together these constraints create our group within the parenthesis.

Before this group, we see `/^#?`. This part of the regex defines the beginning of the string. The `/` begins the regex. A regex must start and end with a `/`. After that, the first character we're checking for is `#`. The `^`anchor means that the string must start with that character that it's next to. In this case: `#`. The `?` after `#` means that the regex is only checking for zero or one of the character.

At the end of that group, we're shown a `$` anchor. This `$` anchor means that the string must end with what is defined. In this case, before that anchor, we're given our group of `([a-f0-9]{6}|[a-f0-9]{3})`. A string matching this group of characters must come after our `#` character in order to return a match.

Below is an explanation of each individual part, and how it functions together to create our regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

Anchors do not match any character, but rather, they match a position before or after characters. The two main anchors that you will see are `^` and `$`.

`^` - Represents the start. Characters that follow this will denote the beginning of the regex.\
`$` - Represents the end of an anchor

Regex are case sensitive. This means that if you set a regex command to find "Hello", using `/^hello$/`, "Hello" will not be returned. (Captial H)

In the case of hex values, the anchor `^` refers to the `#` character. Since all Hex Values begin with a `#`, the regex specifies that by using the `^`. 

The `$` anchor matches characters at the end of the string. In the case of the Hex Value regex, the `$` anchor is preceded by `([a-f0-9]{6}|[a-f0-9]{3})` which means that the hex value should end with six OR three characters between `a-f` and `0-9` these parts will be explained below.

### Quantifiers

Quantifiers in regex are characters that specify the how many times the characters that precede it can occur. In our regex we have `[a-f0-9]{6}` and `[a-f0-9]{3}`. The `6` and `3` here are the quantifiers for the `[a-f0-9]`.

An easy way to understand it is in a simple regex like: `E{5}`, the character `E` must be repeated 5 times in order to return a match. `EEEEE`.

In our Hex Value regex, the `{6}` in this case refers to the `[a-f0-9]`. Our regex will only match with hex values that contain 6 characters that include all characters from `a-f` and integers from `0-9`. After the Or Operator `|` the same rule is applied but this time only checking for `3` characters followed by the `$` anchor. 

`?` - Matches 0 or one occurrence of a preceding character or group. 
`{n}` - Matches exactly "n" occurrences of the preceding character or group.\
`{n,m}` - Matches between n and m occurrences of the preceding character or group.


### OR Operator

The OR operator is represented by the `|` symbol in the regex. The OR operator allows you to look for two different strings, and have both be returned in the matching process.

For example, A regex like, `/Today|Birthday` will return both `Today` and `Birthday` from a string like 'Today is my birthday'. This is because of the `|` operator working to seperate the two clauses. 

### Character Classes

Character classes are enclosed in square brackets `[]`, and allow you define a group of characters that you want to match without having to list each character individually. In this case, our character classes are `[a-f]` and `[0-9]`.

Below are how character classes can be written to encapsulate all types of characters both upper and lowercase.

[a-z] - Matches any lowercase letter.\
[A-Z] - Matches any upper case letter.\
[A-Za-z] - Matches any uppercase or lowercase letter.\
[0-9] - Matches any single digit.

### Flags

Flags are added after the closing delimiter of the regular expression. Flags control various aspects of pattern matching and behavior. The most common flags are 

`i` - Case-Insensitive Search: The regex will ignore case..\
`g` - Global Search: The regex will check for all possible matches beyond the first.\
`m` - Multi-line search: a multi-line input string should be treated as multiple lines.\

### Grouping and Capturing

A way to treat multiple characters as a single unit, and are created by placing the characters to be grouped inside a set of parenthesis.

Considering the regex defined earlier, our group contains two bracket expressions followed by our `$` anchor. 


### Bracket Expressions

Bracket expressions are regex parameters that will match a specific pattern of characters (alphabetic, numeric, special characters, symbols etc..) defined within brackets. 

Bracket expressions and Character Classes go hand in hand.

For our Hex Value regex, our bracket expressions are `[a-f]` and `[0-9]`. This means that we will only be checking for lowercase `a-f` characters and integers `0-9`. 

### Greedy and Lazy Match

Regex are greedy by default. This means is that they try to match as many occurances of the specific character/string as possible. 

Lazy matching is the opposite, where it tries to match as little text as possible, while still allowing the rest of the pattern to match. Lazy matches will need a `?`.

In our regex, the `?` after our `#` character means that the regex will only match with zero or one `#` characters. Essential for Hex Values.


## Author

Ediubong Ekwere | JunoAndIce\
With help from:
Joey Lee | Rockoejoe2

https://github.com/JunoAndIce | ekwere.edi@gmail.com\
https://github.com/Rockojoe2