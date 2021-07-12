# RegEx for JavaScript

This tutorial explains regex patterns, methods and constructors that can be used in JavaScript to validate user input data.

## Summary of an example used in this [homework](https://github.com/vilmaq/readme-generator/blob/master/utils/questions.js)

### URL validation in JavaScript

To validate a URL input from a user, the following function can be used:

```
 validate: function validURL(str) {
      const pattern = new RegExp(
        "^(https?:\\/\\/)?" + // protocol
          "((([a-z\\d]([a-z\\d-]*[a-z\\d])*)\\.)+[a-z]{2,}|" + // domain name
          "((\\d{1,3}\\.){3}\\d{1,3}))" + // OR ip (v4) address
          "(\\:\\d+)?(\\/[-a-z\\d%_.~+]*)*" + // port and path
          "(\\?[;&a-z\\d%_.~+=-]*)?" + // query string
          "(\\#[-a-z\\d_]*)?$",
        "i"
      ); // fragment locator
      return !!pattern.test(str);
}
```

### Constructor Function

A way to create regular expressions in JavaScript is by using a constructor. This method takes in regular expressions as a string argument.
It is advisable to use the constructor function when creating regular expressions whose pattern will change during runtime. For instance, when validating user input or performing iterations. The syntax to create JavaScript regular expressions with constructor function is shown in the code above as follows:

```
      const pattern = new RegExp(
        "^(https?:\\/\\/)?" + // protocol
          "((([a-z\\d]([a-z\\d-]*[a-z\\d])*)\\.)+[a-z]{2,}|" + // domain name
          "((\\d{1,3}\\.){3}\\d{1,3}))" + // OR ip (v4) address
          "(\\:\\d+)?(\\/[-a-z\\d%_.~+]*)*" + // port and path
          "(\\?[;&a-z\\d%_.~+=-]*)?" + // query string
          "(\\#[-a-z\\d_]*)?$",
      );
```

### Flag

In this case flag "i" is used to ignore the case of the input entered from the user.

### Pattern explained

<table class="mtable2 tab">
<tbody><tr>
<th>Character</th>
<th>What does it do?</th>
<th>Regex</th>
<th>Matches</th>
</tr>
<tr class="tcw">
<td class="bld ce">^</td>
<td>Matches everything that starts with the continuing string</td>
<td>^https</td>
<td>https://, https://www</td>
</tr>
<tr class="tcw">
<td class="bld ce">?</td>
<td>Matches the character before the ? zero or one times. Also, used as a non-greedy match</td>
<td>https?:
</td>
<td>https://, www.</td>
</tr>
<tr class="tcw">
<td class="bld ce">\</td>
<td>Escape the character after the backslash or create an escape sequence</a>.</td>
<td>https:\\/\\/</td>
<td>https://</td>
</tr>
<tr class="tcw">
<td class="bld ce">+</td>
<td>Matches character before + one or more times AND/OR in case of a constructor it concatenates regex literals </td>
<td>a+c</td>
<td>ac, aac, aaac,</td>
</tr>
<tr class="tcw">
<td class="bld ce">(...)</td>
<td><a href="/jargon/c/capture.htm">Capture</a> anything matched</td>
<td>(a)b(c)</td>
<td>Captures 'a' and 'c'</td>
</tr>
<tr class="tcw">
<td class="bld ce">(?:...)</td>
<td>Non-capturing group</td>
<td>(a)b(?:c)</td>
<td>Captures 'a' but only groups 'c'</td>
</tr>
<tr class="tcw">
<td class="bld ce">[...]</td>
<td>Matches anything contained in <a href="/jargon/b/bracket.htm">brackets</a></td>
<td>[abc]</td>
<td>a,b, or c</td>
</tr>
<tr class="tcw">
<td class="bld ce">[^...]</td>
<td>Matches anything not contained in brackets</td>
<td>[^abc]</td>
<td>xyz, 123, 1de</td>
</tr>
<tr class="tcw">
<td class="bld ce">[a-z]</td>
<td>Matches any characters between 'a' and 'z'</td>
<td>[b-z]</td>
<td>bc, mind, xyz</td>
</tr>
<tr class="tcw">
<td class="bld ce">{x}</td>
<td>The exact 'x' amount of times to match</td>
<td>(abc){2}</td>
<td>abcabc</td>
</tr>
<tr class="tcw">
<td class="bld ce">{x,}</td>
<td>Match 'x' amount of times or more</td>
<td>(abc){2,}</td>
<td>abcabc, abcabcabc</td>
</tr>
<tr class="tcw">
<td class="bld ce">{x,y}</td>
<td>Match between 'x' and 'y' times.</td>
<td>(a){2,4}</td>
<td>aa, aaa, aaaaa</td>
</tr>
<tr class="tcw">
<td class="bld ce">*</td>
<td>Greedy match that matches everything in place of the *</td>
<td>ab*c</td>
<td>abc, abbcc, abcdc</td>
</tr>
<tr class="tcw">
<td class="bld ce">$</td>
<td>Matches end of line</a></td>
<td>abc$</td>
<td>my:abc, 123abc, theabc</td>
</tr>
<tr class="tcw">
<td class="bld ce">.</td>
<td>Match any character</a></td>
<td>a.c</td>
<td>abc, asg, a2c</td>
</tr>

</tr>
</tbody></table>

### Method: test()

test() method searches for a match between a regular expression and a String. It returns true or false if a match is found or not.

     return !!pattern.test(str);

## The Basics of regular Expressions

<table class="mtable2 tab">
<tbody><tr>
<th>Character</th>
<th>What does it do?</th>
<th>Example</th>
<th>Matches</th>
</tr>
<tr class="tcw">
<td class="bld ce">^</td>
<td>Matches beginning of line</td>
<td>^abc</td>
<td>abc, abcdef.., abc123</td>
</tr>
<tr class="tcw">
<td class="bld ce">$</td>
<td>Matches <a href="/jargon/e/eol.htm">end of line</a></td>
<td>abc$</td>
<td>my:abc, 123abc, theabc</td>
</tr>
<tr class="tcw">
<td class="bld ce">.</td>
<td>Match any <a href="/jargon/c/charact.htm">character</a></td>
<td>a.c</td>
<td>abc, asg, a2c</td>
</tr>
<tr class="tcw">
<td class="bld ce">|</td>
<td><a href="/jargon/o/oroperat.htm">OR</a> operator</td>
<td>abc|xyz</td>
<td>abc or xyz</td>
</tr>
<tr class="tcw">
<td class="bld ce">(...)</td>
<td><a href="/jargon/c/capture.htm">Capture</a> anything matched</td>
<td>(a)b(c)</td>
<td>Captures 'a' and 'c'</td>
</tr>
<tr class="tcw">
<td class="bld ce">(?:...)</td>
<td>Non-capturing group</td>
<td>(a)b(?:c)</td>
<td>Captures 'a' but only groups 'c'</td>
</tr>
<tr class="tcw">
<td class="bld ce">[...]</td>
<td>Matches anything contained in <a href="/jargon/b/bracket.htm">brackets</a></td>
<td>[abc]</td>
<td>a,b, or c</td>
</tr>
<tr class="tcw">
<td class="bld ce">[^...]</td>
<td>Matches anything not contained in brackets</td>
<td>[^abc]</td>
<td>xyz, 123, 1de</td>
</tr>
<tr class="tcw">
<td class="bld ce">[a-z]</td>
<td>Matches any characters between 'a' and 'z'</td>
<td>[b-z]</td>
<td>bc, mind, xyz</td>
</tr>
<tr class="tcw">
<td class="bld ce">{x}</td>
<td>The exact 'x' amount of times to match</td>
<td>(abc){2}</td>
<td>abcabc</td>
</tr>
<tr class="tcw">
<td class="bld ce">{x,}</td>
<td>Match 'x' amount of times or more</td>
<td>(abc){2,}</td>
<td>abcabc, abcabcabc</td>
</tr>
<tr class="tcw">
<td class="bld ce">{x,y}</td>
<td>Match between 'x' and 'y' times.</td>
<td>(a){2,4}</td>
<td>aa, aaa, aaaaa</td>
</tr>
<tr class="tcw">
<td class="bld ce">*</td>
<td><a href="/jargon/g/greedy.htm">Greedy</a> match that matches everything in place of the *</td>
<td>ab*c</td>
<td>abc, abbcc, abcdc</td>
</tr>
<tr class="tcw">
<td class="bld ce">+</td>
<td>Matches character before + one or more times</td>
<td>a+c</td>
<td>ac, aac, aaac,</td>
</tr>
<tr class="tcw">
<td class="bld ce">?</td>
<td>Matches the character before the ? zero or one times. Also, used as a non-greedy match</td>
<td>ab?c</td>
<td>ac, abc</td>
</tr>
<tr class="tcw">
<td class="bld ce">\</td>
<td>Escape the character after the backslash or create an <a href="/jargon/e/escasequ.htm">escape sequence</a>.</td>
<td>a\sc</td>
<td>a c</td>
</tr>
</tbody></table>

## Table of Contents

- [RegEx for JavaScript](#regex-for-javascript)
  - [Summary of an example used in this homework](#summary-of-an-example-used-in-this-homework)
    - [URL validation in JavaScript](#url-validation-in-javascript)
    - [Constructor Function](#constructor-function)
    - [Flag](#flag)
    - [Pattern explained](#pattern-explained)
    - [Method: test()](#method-test)
  - [The Basics of regular Expressions](#the-basics-of-regular-expressions)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
    - [Anchors](#anchors)
    - [Quantifiers](#quantifiers)
    - [Grouping Constructs](#grouping-constructs)
    - [Bracket Expressions](#bracket-expressions)
    - [Character Classes](#character-classes)
    - [The OR Operator](#the-or-operator)
    - [Flags](#flags)
      - [Usage:](#usage)
    - [Escape Character Escape](#escape-character-escape)
  - [Considerations](#considerations)
  - [Author](#author)

## Regex Components

### Anchors

Anchors are used to match a position: before, after, or between characters. They do not match any character at all.
Following a list of anchors used in JavaScript:

<table class="reference" id="tableflavor" style="width: 565px;">
<tbody><tr><th>Feature</th><th>Syntax</th><th>Description</th><th>Example</th>

</tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">^</span></tt>&nbsp;(caret)</td>
    <td>Matches at the start of the string the regex pattern is applied to.</td>
    <td><tt class="code"><span class="regexspecial">^</span><span class="regexspecial">.</span></tt> matches <tt class="match">a</tt> in <tt class="string">abc\ndef</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: table-cell;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td></tr>

<tr><td>String anchor</></td>
    <td><tt class="code"><span class="regexspecial">$</span></tt>&nbsp;(dollar)</td>
    <td>Matches at the end of the string the regex pattern is applied to.</td>
    <td><tt class="code"><span class="regexspecial">.</span><span class="regexspecial">$</span></tt> matches <tt class="match">f</tt> in <tt class="string">abc\ndef</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: table-cell;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">$</span></tt>&nbsp;(dollar)</td>
    <td>Matches before the final line break in the string (if any) in addition to matching at the very end of the string.</td>
    <td><tt class="code"><span class="regexspecial">.</span><span class="regexspecial">$</span></tt> matches <tt class="match">f</tt> in <tt class="string">abc\ndef\n</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">n/a</td><td style="display: none;">no</td></tr>

<tr><td>Line anchor</a></td>
    <td><tt class="code"><span class="regexspecial">^</span></tt>&nbsp;(caret)</td>
    <td>Matches after each line break in addition to matching at the start of the string, thus matching at the start of each line in the string.</td>
    <td><tt class="code"><span class="regexspecial">^</span><span class="regexspecial">.</span></tt> matches <tt class="match">a</tt> and <tt class="match">d</tt> in <tt class="string">abc\ndef</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: table-cell;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">basic<br>extended<br>grep<br>egrep<br>awk</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td style="display: none;">n/a</td><td class="yes" style="display: none;">option</td></tr>

<tr><td>Line anchor</a></td>
    <td><tt class="code"><span class="regexspecial">$</span></tt>&nbsp;(dollar)</td>
    <td>Matches before each line break in addition to matching at the end of the string, thus matching at the end of each line in the string.</td>
    <td><tt class="code"><span class="regexspecial">.</span><span class="regexspecial">$</span></tt> matches <tt class="match">c</tt> and <tt class="match">f</tt> in <tt class="string">abc\ndef</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: table-cell;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">basic<br>extended<br>grep<br>egrep<br>awk</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td class="yes" style="display: none;">option</td><td style="display: none;">n/a</td><td class="yes" style="display: none;">option</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\A</span></tt></td>
    <td>Matches at the start of the string the regex pattern is applied to.</td>
    <td><tt class="code"><span class="regexspecial">\A</span><span class="regexspecial">\w</span></tt> matches only <tt class="match">a</tt> in <tt class="string">abc</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td class="yes" style="display: none;">ECMA<br>extended<br>egrep<br>awk</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">10gR2</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>Attempt anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\A</span></tt></td>
    <td>Matches at the start of the match attempt.</td>
    <td><tt class="code"><span class="regexspecial">\A</span><span class="regexspecial">\w</span></tt> matches <tt class="match">a</tt>, <tt class="match">b</tt>, and <tt class="match">c</tt> when iterating over all matches in <tt class="string">abc def</tt></td>
<td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>Attempt anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\G</span></tt></td>
    <td>Matches at the start of the match attempt.</td>
    <td><tt class="code"><span class="regexspecial">\G</span><span class="regexspecial">\w</span></tt> matches <tt class="match">a</tt>, <tt class="match">b</tt>, and <tt class="match">c</tt> when iterating over all matches in <tt class="string">abc def</tt></td>
<td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">4.0–7.9</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>Match anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\G</span></tt></td>
    <td>Matches at the end of the previous match during the second and following match attempts.  Matches at the start of the string during the first match attempt.</td>
    <td><tt class="code"><span class="regexspecial">\G</span><span class="regexspecial">\w</span></tt> matches <tt class="match">a</tt>, <tt class="match">b</tt>, and <tt class="match">c</tt> when iterating over all matches in <tt class="string">abc def</tt></td>
<td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">8.00</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">ECMA<br>extended<br>egrep<br>awk</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\z</span></tt></td>
    <td>Matches at the end of the string the regex pattern is applied to.</td>
    <td><tt class="code"><span class="regexspecial">\w</span><span class="regexspecial">\z</span></tt> matches <tt class="match">f</tt> in <tt class="string">abc\ndef</tt> but fails to match <tt class="string">abc\ndef\n</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td class="yes" style="display: none;">ECMA<br>extended<br>egrep<br>awk</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">10gR2</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\Z</span></tt></td>
    <td>Matches at the end of the string the regex pattern is applied to.</td>
    <td><tt class="code"><span class="regexspecial">\w</span><span class="regexspecial">\Z</span></tt> matches <tt class="match">f</tt> in <tt class="string">abc\ndef</tt> but fails to match <tt class="string">abc\ndef\n</tt> or <tt class="string">abc\ndef\n\n</tt></td>
<td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\Z</span></tt></td>
    <td>Matches at the end of the string as well as before the final line break in the string (if any).</td>
    <td><tt class="code"><span class="regexspecial">.</span><span class="regexspecial">\Z</span></tt> matches <tt class="match">f</tt> in <tt class="string">abc\ndef</tt> and in <tt class="string">abc\ndef\n</tt> but fails to match <tt class="string">abc\ndef\n\n</tt></td>
<td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">10gR2</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\Z</span></tt></td>
    <td>Matches at the end of the string as well as before all trailing line breaks in the string (if any).</td>
    <td><tt class="code"><span class="regexspecial">.</span><span class="regexspecial">\Z</span></tt> matches <tt class="match">f</tt> in <tt class="string">abc\ndef</tt> and in <tt class="string">abc\ndef\n</tt> and in <tt class="string">abc\ndef\n\n</tt></td>
<td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">ECMA<br>extended<br>egrep<br>awk</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexescaped">\‘</span></tt> (backslash backtick)</td>
    <td>Matches at the start of the string the regex pattern is applied to.</td>
    <td><tt class="code"><span class="regexescaped">\‘</span><span class="regexspecial">\w</span></tt> matches only <tt class="match">a</tt> in <tt class="string">abc</tt></td>
<td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">ECMA<br>extended<br>egrep<br>awk</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>Attempt anchor</a></td>
    <td><tt class="code"><span class="regexescaped">\‘</span></tt> (backslash backtick)</td>
    <td>Matches at the start of the match attempt.</td>
    <td><tt class="code"><span class="regexescaped">\‘</span><span class="regexspecial">\w</span></tt> matches <tt class="match">a</tt>, <tt class="match">b</tt>, and <tt class="match">c</tt> when iterating over all matches in <tt class="string">abc def</tt></td>
<td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><td>String anchor</a></td>
    <td><tt class="code"><span class="regexspecial">\'</span></tt> (backslash quote)</td>
    <td>Matches at the end of the string the regex pattern is applied to.</td>
    <td><tt class="code"><span class="regexspecial">\w</span><span class="regexspecial">\'</span></tt> matches <tt class="match">f</tt> in <tt class="string">abc\ndef</tt> but fails to match <tt class="string">abc\ndef\n</tt></td>
<td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: table-cell;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">ECMA<br>extended<br>egrep<br>awk</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td><td class="yes" style="display: none;">YES</td><td class="yes" style="display: none;">YES</td><td style="display: none;">no</td><td style="display: none;">no</td><td style="display: none;">no</td></tr>

<tr><th>Feature</th><th>Syntax</th><th>Description</th><th>Example</th>

</tr>

<script type="text/javascript" src="selflavor.js"></script>

</tbody></table>

### Quantifiers

Quantifiers are used to indicate the number of characters or expressions we need to match.

Example:

`[a-z\\d-]*` - This syntax is used to match any of the characters between the square brackets zero or more times.

### Grouping Constructs

We can match groups of characters by surrounding them with parentheses. This allows us to combine a sequence of literals and pattern characters for example, with a quantifier to find repeating or optional matches.

A regular expression grouping construct is similar to what a parenthetical statement is to math operations.

[ ] - groups evaluation criteria together for evaluation. The regular expression will consider all data in the group [ ] for matching to remain True.

() - Matches a subexpression in the input string

<table id="myTable" class="tablesorter" border="0" style="margin-left: 0;margin-right: auto;" summary="Regular expression grouping constructs and their descriptions">
            <caption style="font-weight: bold;">Regular Expression Grouping Constructs</caption>
            <colgroup><col>
            <col>
            </colgroup><thead>
                <tr>
                    <th style="font-weight: bold;">Regular Expression</th>
                    <th style="font-weight: bold;">Description</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="tabletext">(<i>expr</i>)
                    </td>
                    <td class="tabletext">Match or capture group. Captures the information that matches the expression in parentheses</td>
                </tr>
                <tr>
                    <td class="tabletext">(?:<i>expr</i>)</td>
                    <td class="tabletext">Non-capturing group. Groups the contained expressions together (e.g., to apply a quantifier to multiple symbols at once), but does not restrict the information to be captured to only that group.</td>
                </tr>
                <tr>
                    <td class="tabletext">(?=<i>expr</i>)</td>
                    <td class="tabletext">Captures information that is followed by the expression if the expression is true and the input matches the pattern that follows this expression.</td>
                </tr>
                <tr>
                    <td class="tabletext">(?&lt;&gt;) </td>
                    <td class="tabletext">Named capture group.*</td>
                </tr>
                <tr>
                    <td class="tabletext">\k&lt;&gt;</td>
                    <td class="tabletext">Named back reference. *</td>
                </tr>
            </tbody>
        </table>

### Bracket Expressions

A bracket expression is a list of characters enclosed by ‘[’ and ‘]’. It is used to

- Match any single character in the list
  for example: '[absdefghijkl]' - matches any letter inside the square brackets
- Match any character not in the list when the first character in the list is the caret ^.
  for example: '[^()]' - matches any single character that is not an opening or closing parenthesis, and might or might not match an encoding error.
- Match any character in a range expression.
  for example: '[0-9]' - - matches all numbers from 0 to 0 or it is equivalent with '[0123456789]'

certain named classes of characters are predefined within bracket expressions, as follows. Their interpretation depends on the LC_CTYPE locale; for example, ‘[[:alnum:]]’ means the character class of numbers and letters in the current locale.

‘[:alnum:]’
Alphanumeric characters: ‘[:alpha:]’ and ‘[:digit:]’; in the ‘C’ locale and ASCII character encoding, this is the same as ‘[0-9A-Za-z]’.

‘[:alpha:]’
Alphabetic characters: ‘[:lower:]’ and ‘[:upper:]’; in the ‘C’ locale and ASCII character encoding, this is the same as ‘[A-Za-z]’.

‘[:blank:]’
Blank characters: space and tab.

‘[:cntrl:]’
Control characters. In ASCII, these characters have octal codes 000 through 037, and 177 (DEL). In other character sets, these are the equivalent characters, if any.

‘[:digit:]’
Digits: 0 1 2 3 4 5 6 7 8 9.

‘[:graph:]’
Graphical characters: ‘[:alnum:]’ and ‘[:punct:]’.

‘[:lower:]’
Lower-case letters; in the ‘C’ locale and ASCII character encoding, this is a b c d e f g h i j k l m n o p q r s t u v w x y z.

‘[:print:]’
Printable characters: ‘[:alnum:]’, ‘[:punct:]’, and space.

‘[:punct:]’
Punctuation characters; in the ‘C’ locale and ASCII character encoding, this is ! " # $ % & ' ( ) \* + , - . / : ; < = > ? @ [ \ ] ^ \_ ` { | } ~.

‘[:space:]’
Space characters: in the ‘C’ locale, this is tab, newline, vertical tab, form feed, carriage return, and space. See Usage, for more discussion of matching newlines.

‘[:upper:]’
Upper-case letters: in the ‘C’ locale and ASCII character encoding, this is A B C D E F G H I J K L M N O P Q R S T U V W X Y Z.

‘[:xdigit:]’
Hexadecimal digits: 0 1 2 3 4 5 6 7 8 9 A B C D E F a b c d e f.

### Character Classes

Character classes are used to distinguish letters from characters and the way they work, changing their functionalities.

- \d — This character matches a digit. i.e. a number from 0–9. You can use this character /\d/ or /[0–9]/ to match digits.
- \D — This is used to match any character that’s not a digit. /\D/ is equivalent to / [^0-9]/.
- \w — This character is used for matching alphanumeric characters from the basic Latin alphabet. /\w/ is equivalent to [A-Za-z0–9_].
- \W — This is used to match non- alphanumeric characters. i.e. characters not from the basic Latin alphabet. /\W/ is equivalent to [^a-za-z0–9_].
- \s — This is used to match a single whitespace character. i.e. a space, tab, form-feed, line-feed, and other Unicode spaces. /\s/ is equivalent to [ \f\n\r\t\v\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff].
- . — The dot sign is used to match single characters except for line terminators like \n, \r, \u2028, and \u2029.
- [\b] — This character is used for matching a backspace.
- \0 — This matches a null character.
- \xhh — This syntax is used for matching a character (x) with two hexadecimal digits.
- \uhhhh — This syntax is used for matching a UTF-16 code unit with hexadecimal digits.
- \cX — This is used to match a control character using the caret notation.
  There are other special characters like \t, \r, \n, \v, \f which match a horizontal tab, carriage return, line feed, vertical tab, and form feed respectively.

### The OR Operator

The OR Operator/Alternation, denoted with a vertical line | in a regex, is used to match any of the characters or strings in a subexpression. In my example:
"((([a-z\\d]([a-z\d-]*[a-z\d])\*)\\.)+[a-z]{2,}|" + // domain name
"((\\d{1,3}\\.){3}\\d{1,3}))" + // OR ip (v4) address

I am trying to match my the domain name "((([a-z\\d]([a-z\d-]*[a-z\d])\*)\\.)+[a-z]{2,} |" or the IP Address "((\\d{1,3}\\.){3}\\d{1,3}))"

### Flags

The flags are used to enhance the patterns. Regex in JS hve 7 flags.

- d — used for generating indices for substring matches.
- g — used to indicate global search.
- i — to ignore the case in a Regex, for example to perform searches without enforcing case sensitivity.
- m — used for performing multi-line search.
- u — This flag indicates Unicode; it treats a pattern as a sequence of Unicode code points.
- y — used to perform a sticky search.
- s — The s flag allows the dot . character to match newline characters.

#### Usage:

```
//for literal notation
var re = /pattern/flags;
// or
//for constructor function
var re = new RegExp('pattern', 'flags');
```

### Escape Character Escape

\ - Backslash is a an escape character used in javascript. Escape characters can be used when we need to use special characters literally for example when searching for a '\*', '.', '?', etc

## Considerations

- Not all programming languages use the same regular expressions, but they all share similarities.
- Escape characters are case sensitive.
- Advisable to be added also in the server side, not on the client side as on the client side JS might be disabled.

## Author

Vilma Qerama - MsC Computer Science & BsC Computer Engineering

- Github: https://github.com/vilmaq
- Portfolio: https://vilmaq.github.io/Portfolio/
- Linkedin: https://www.linkedin.com/in/vilmaqerama/

```

```
