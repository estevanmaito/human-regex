# Human Regex

Simple, human readable Regular Expressions for JavaScript

## TODO

### Assertions

- **Lookahead assertion**: Matches `x` only if `x` is followed by `y`.
  - `x(?=y)`
- **Negative lookahead assertion**: Matches `x` only if `x` is not followed by `y`.
  - `x(?!y)`
- **Lookbehind assertion**: Matches `x` only if `x` is preceded by `y`.
  - `(?<=y)x`
- **Negative lookbehind assertion**: Matches `x` only if `x` is not preceded by `y`.
  - `(?<!=y)x`

### Boundaries

- **Begining of input**
  - `^`
- **End of input**
  - `$`
- **Word boundary**
  - `\b`
- **Non-word boundary**
  - `\B`

### Character classes

- **Single character**
  - `.`
- **Any digit**
  - `\d`
- **Any character that is not a digit**
  - `\D`
- **Any alphanumeric character**
  - `\w`
- **Any character that is not a word character**
  - `\W`
- **Single white space**
  - `\s`
- **Single character that is not a white space**
  - `\S`
- **Horizontal tab**
  - `\t`
- **Carriage return**
  - `\r`
- **New line (linefeed)**
  - `\n`
- **Vertical tab**
  - `\v`
- **Form-feed**
  - `\f`

### Groups and ranges

- **Or**
  - `x|y`
- **Character set**
  - `[abcd]`
  - `[a-d]`
- **Negated character set**
  - `[^abc]`
- **Capturing group**
  - `(x)`
- **Non-capturing group**
  - `(?:x)`

### Quantifiers

- Matches the preceding item `x` 0 or more times
  - `x*`
- Matches the preceding item `x` 1 or more times
  - `x+`
- Matches the preceding item `x` 0 or 1 time
  - `x?`
- Matches exactly `n` occurrences of item `x`
  - `x{n}`
- Matches at least `n` occurrences of item `x`
  - `x{n,}`
- Matches at least `n` and at most `m` occurrences of item `x`
  - `x{n,m}`
- Non-greedy quantifier, stops as soon as it finds a match
  - `?`

### Flags

- **Global search**
  - `g`
- **Case-insensitive search**
  - `i`
- **Multi-line search**
  - `m`
- **Allows `.` to match newline characters**
  - `s`
- **Unicode**
  - `u`
- **Sticky search**
  - `y`

[MDN Regular Expressions Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScrit/Guide/Regular_Expressions)
