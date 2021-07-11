# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

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

A way to create regular expressions in JavaScript is by using a constructor. This method takes in regular expressions as Strings in function arguments.
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

test()
This RegExp method searches for a match between a regular expression and a String. It returns true or false if a match is found or not.

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

- [Title (replace with your title)](#title-replace-with-your-title)
  - [Summary](#summary)
    - [URL validation in JavaScript](#url-validation-in-javascript)
    - [Constructor Function](#constructor-function)
    - [Flag](#flag)
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
    - [Character Escapes](#character-escapes)
    - [Considerations](#considerations)
  - [Author](#author)

## Regex Components

### Anchors

### Quantifiers

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

### Considerations

- Not all programming languages use the same regular expressions, but they all share similarities.
- Escape characters are case sensitive.

## Author

Vilma Qerama -

```

```