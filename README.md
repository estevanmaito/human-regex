# Human Regex

Simple, human readable Regular Expressions for JavaScript

## TODO

### Assertions

- **Lookahead assertion**: Matches `x` only if `x` is followed by `y`.
  - `x(?=y)`
  - `isFollowedBy`
- **Negative lookahead assertion**: Matches `x` only if `x` is not followed by `y`.
  - `x(?!y)`
  - `isNotFollowedBy`
- **Lookbehind assertion**: Matches `x` only if `x` is preceded by `y`.
  - `(?<=y)x`
  - `isPrecededBy`
- **Negative lookbehind assertion**: Matches `x` only if `x` is not preceded by `y`.
  - `(?<!=y)x`
  - `isNotPrecededBy`

### Boundaries

- **Begining of input**
  - `^`
  - `startsWith`
  - `beginsWith`
- **End of input**
  - `$`
  - `endsWith`
  - `inTheEnd`
  - `endOfLine`
- **Word boundary**
  - `\b`
- **Non-word boundary**
  - `\B`

### Character classes

- **Single character**
  - `.`
  - `anyCharacter`
- **Any digit**
  - `\d`
  - `anyNumber`
  - `number`
  - `digit`
- **Any character that is not a digit**
  - `\D`
  - `notNumber`
  - `notDigit`
- **Any alphanumeric character**
  - `\w`
  - `anyAlphanumericAndUnderscore`
  - `anyWord`
- **Any character that is not a word character**
  - `\W`
  - `notWord`
- **Single white space**
  - `\s`
  - `singleWhitespace`
- **Single character that is not a white space**
  - `\S`
  - `notWhitespace`
- **Horizontal tab**
  - `\t`
  - `tab`
- **Carriage return**
  - `\r`
  - `carriageReturn`
- **New line (linefeed)**
  - `\n`
  - `newLine`
- **Vertical tab**
  - `\v`
  - `verticalTab`
- **Form-feed**
  - `\f`
  - `formFeed`

### Groups and ranges

- **Or**
  - `x|y`
  - `or`
- **Character set**
  - `[abcd]`
  - `[a-d]`
  - `anyOf`
- **Negated character set**
  - `[^abc]`
  - `noneOf`
  - `anythingBut`
- **Capturing group**
  - `(x)`
  - `multipleOf`
  - `groupOf`
- **Non-capturing group**
  - `(?:x)`

### Quantifiers

- Matches the preceding item `x` 0 or more times
  - `x*`
  - `zeroOrMore`
  - `neverOrMore`
  - `toOccurZeroOrMore`
- Matches the preceding item `x` 1 or more times
  - `x+`
  - `oneOrMore`
  - `onceOrMore`
  - `toOccurOnceOrMore`
- Matches the preceding item `x` 0 or 1 time
  - `x?`
  - `zeroOrOne`
  - `optional`
  - `maybe`
  - `toMaybeOccur`
- Matches exactly `n` occurrences of item `x`
  - `x{n}`
  - `exactly`
  - `numberOfOccurrences`
  - `count`
  - `toOccurExactly`
- Matches at least `n` occurrences of item `x`
  - `x{n,}`
  - `atLeast`
  - `minimumOccurrences`
  - `toOccurAtLeast`
- Matches at least `n` and at most `m` occurrences of item `x`
  - `x{n,m}`
  - `between`
  - `range`
  - `atMost`
  - `maximumOccurrences`
  - `toOccurAtMost`
  - `toOccurBetween`
- Non-greedy quantifier, stops as soon as it finds a match
  - `?`
  - `lazy`
  - `stopImmediatelly`
  - `findAndStop`

### Flags

- **Global search**
  - `g`
  - `findFirst`
- **Case-insensitive search**
  - `i`
  - `caseInsensitive`
- **Multi-line search**
  - `m`
  - `multiLine`
- **Allows `.` to match newline characters**
  - `s`
- **Unicode**
  - `u`
- **Sticky search**
  - `y`

[MDN Regular Expressions Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScrit/Guide/Regular_Expressions)

## Examples

### Matching a password

Matches a string with a minimium of 5 and maximum 16 letters, numbers, underscores or hyphens

```js
// same as /^[a-z0-9_-]{5, 16}$/
// Matches mypassw0rd
// Does not match mypa$$w0rd
hre()
  .find(password)
  .startsWith()
  .anyOf("a-z0-9_-")
  .toOccurBetween(5, 16)
  .endsWith();

hre()
  .find(password)
  .startsWith()
  .openCapturingGroup()
  .anyAlphanumericAndUnderscore()
  .toOccurZeroOrMore()
  .singleCharacter("-")
  .toOccurZeroOrMore()
  .closeCapturingGroup()
  .toOccurBetween(5, 16)
  .endsWith();
```

Matches a string with a minimium of 6 and maximum 16 characters, at least 3 letters and 2 numbers.

```js
/* same as /^(?=(.*\d){2,})(?=(.*[A-Za-z]){3,})[a-zA-Z0-9]{6,16}$/
^ - from start
(?=(.*\d){2,})
(?=(.*[A-Za-z]){3,})
[a-zA-Z0-9]
{6,16}
$ - until end
*/
```
