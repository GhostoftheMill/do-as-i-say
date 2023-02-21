# Tutorial on Regex for Matching a URL

Regex is short for regular expression. Regular expressions are a sequence of symbols and characters that define a search pattern to locate, match, and manage content within a text.

## Summary

The regular expression<br>


>/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

is used to match a URL within a text. Instead of a large volume of code, this relatively short expression creates flexibility to locate a variety of different URL structures. 


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Other Concepts](#other-concepts)

## Regex Components


### Anchors
Strange to start with anchors but here we are. Anchors do not match any specific character. Anchors are used to match a position before, after, or between characters. <br>
The two anchors located in our string are "^" & "$".<br>
- ^: Matches a position at the beginning of a string.
- $: Matches a position at the end of a string.
<br>

Seen highlighted below<br>
>/`^`(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?`$`/<br>

"^" is used before the first capture group (more on that later). It says to look for (http?:\/\/) at the beginning of the text.<br>
"$" is used after "/?". This says to look for either 0 or 1 instance of "/" at the end of the text.<br>

### Quantifiers
Quantifiers are used to specify how many of a particular criteria must be present to match. In our expression we seen many different quantifiers.<br>
- *: 0 or more
- +: 1 or more
- ?: 0 or 1
- {}: a specific range
<br>
In our example<br>
>/^(https`?`:\/\/)`?`([\da-z\.-]`+`)\.([a-z\.]`{2,6}`)([\/\w \.-]`*`)`*`\/`?`$/<br>

1. Our first "?" is used after the "s" in https because not all URL have HTTPS some use HTTP instead.<br>
2. Likewise our second "?" is found after the first capture group (still coming) because some URL omit the HTTP/HTTPS entirely.<br>
3. We find a "+" after the range "\da-z\.-" which means search for any digit (\d), letter a through z, period, or dash grouped 1 or more times.<br>
4. The next quantifier is "{2,6}" which denotes a specifc range of between 2 & 6 on the range "a-z\.", such as .com or .edu.<br>
5. "*" is used inside and outside of the capture group & range for "\/\w \.-". The range says to look for 1 or more of any word (\w), space, forward slash, period, or dash, and then to look for any occurance of those criteria as a whole 1 or more times.<br>
6. Finally, as mentioned in the previous section "/?" is saying to look for either 0 or 1 instance of "/" at the end of the string.<br>

### Greedy and Lazy Match
Continuing with the concept of quantifiers we have the terms "greedy" and "lazy". <br>
Quite simply:<br>
 - greedy: match as much as they can such as "*" & "+". Quantifiers by default are greedy.
 - lazy: match as few occurances as possible. We can add the "?" after any quantifier to make it lazy.

### OR Operator
The OR operator is denoted by "|". This is used to say look for this or that. For example cat|dog would locate either cat or dog. There is no OR operator in our example but it is still important to understand.<br>

### Character Classes
There are many shorthand ways to specify a range of specific sets, these are called character classes. <br>
- \d: any digit [0-9]
- \w: any word
- \s: white space
<br>
are some of the more common examples. They also have opposites which can be used by capitalizing the letter.<br>
- \D: Not a digit
- \W: Not a word
- \S: Not white space
<br>
There are other character classes but we only use two of the above in our expression.<br>
>/^(https?:\/\/)?([`\d`a-z\.-]+)\.([a-z\.]{2,6})([\/`\w` \.-]*)*\/?$/<br>

 "\d" is used within a range inside the second capture group (not yet) to look for any digit, & "w" is used inside a range in the fourth capture group (keep waiting) to match any word.

### Flags
Regular expression flags are placed after the regular expression to modify the default characteristics of regex queries.<br>
In our code we don't find any flags but the six flags are:
- i: case-`i`nsensitive, searches will match regardless of lowercase or uppercase characters
- g: `g`lobal, searches will locate all matches. Without the "g" flag the search stops at the first instance.
- m: `m`ultiline, allows for matches at the beginning and end of a string on each line as opposed to just at the beginning and end of the entire string.
- s: dotall, "s" because reasons. "." (Period) is used for any character except new line characters. Using the "s" flag alls "." to also match new line characters. 
- u: `u`nicode, allows matching of unicode text
- y: stick`y`, looks for a match at a specific position

### Grouping and Capturing
Finally, can explain capture groups. By using parentheses we can group parts of our expression to control the flow similar to in arthimetic, (1+2)*3 = 9 vs. 1+2*3=7.<br>

>/^`(https?:\/\/)`?`([\da-z\.-]+)`\.`([a-z\.]{2,6})``([\/\w \.-]*)`*\/?$/<br>

We have four different capture groups in our expression:
1. (https?\/\/): Looks for either http// or https//
2. ([\da-z\.-]+): Looks for any digit (\d), letters a through z, period, or dash & does so greedily.
3. ([a-z\.]{2,6}): Looks for a period or letter a through z in a range of 2 to 6 such as .com or .edu
4. ([\/\w \.-]*): Looks for a forward slash, word, space, period, or dash 0 or more times to match any sort of extensions after the domain such as /butterfly

### Bracket Expressions
Brackets are used to denote a range.<br>

>/^(https?:\/\/)?(`[\da-z\.-]`+)\.(`[a-z\.]`{2,6})(`[\/\w \.-]`*)*\/?$/<br>

We have three bracketed expressions as seen above. Their contents are explained in "Grouping and Capturing"

### Other Concepts
- Boundaries: Just that, boundaries, denoted by "\b", an anchor that can be used to define a position before, after, or between characters
- Back-references: Used to reference previous capture groups for reuse within the expression. A backslash and a number denoting which group is used.

## Author
This regex tutorial was created by Kevin White.<br>
[Kevin White's GitHub (GhostoftheMill)](https://github.com/GhostoftheMill)<br>
[Send me an email](mailto:kevinmichaelwhite@gmail.com)
