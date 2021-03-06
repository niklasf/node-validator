**node-validator is a library of string validators and sanitizers**

![tests](https://api.travis-ci.org/chriso/node-validator.png?branch=master)

### Server-side usage

Install the library with `npm install validator`

```javascript
var validator = require('validator');

validator.isEmail('foo@bar.com'); //=> true
```

### Client-side usage

The library can be loaded as a script and supports [AMD](http://requirejs.org/docs/whyamd.html)

```html
<script type="text/javascript" src="validator.min.js"></script>
<script type="text/javascript">
  validator.isEmail('foo@bar.com'); //=> true
</script>
```

### Validators

- **equals(str, comparison)** - check if the string matches the comparison.
- **contains(str, seed)** - check if the string contains the seed.
- **matches(str, pattern [, modifiers])** - check if string matches the pattern. Either `matches('foo', /foo/i)` or `matches('foo', 'foo', 'i')`.
- **isEmail(str)** - check if the string is an email.
- **isUrl(str)** - check if the string is an URL.
- **isIP(str [, version])** - check if the string is an IP.
- **isAlpha(str)** - check if the string contains only letters (a-zA-Z).
- **isNumeric(str)** - check if the string contains only numbers.
- **isAlphanumeric(str)** - check if the string contains only letters and numbers.
- **isHexadecimal(str)** - check if the string is a hexadecimal number.
- **isHexColor(str)** - check if the string is a hexadecimal color.
- **isLowercase(str)** - check if the string is lowercase.
- **isUppercase(str)** - check if the string is uppercase.
- **isInt(str)** - check if the string is an integer.
- **isFloat(str)** - check if the string is a float.
- **isDivisibleBy(str, number)** - check if the string is a number that's divisible by another.
- **isNull(str)** - check if the string is null.
- **isLength(str, min [, max])** - check if the string's length falls in a range.
- **isUUID(str [, version])** - check if the string is a UUID.
- **isDate(str)** - check if the string is a date.
- **isAfter(str [, date])** - check if the string is a date that's after the specified date (defaults to now).
- **isBefore(str [, date])** - check if the string is a date that's before the specified date.
- **isIn(str, values)** - check if the string is in a array of allowed values.
- **isCreditCard(str)** - check if the string is a credit card.

### Sanitizers

- **toString(input)** - convert the input to a string.
- **toDate(input)** - convert the input to a date, or `null` if the input is not a date.
- **toFloat(input)** - convert the input to a float, or `NaN` if the input is not a float.
- **toInt(input [, radix])** - convert the input to an integer, or `NaN` if the input is not an integer.
- **toBoolean(input [, strict)** - convert the input to a boolean. Everything except for `'0'`, `'false'` and `''` returns `true`. In strict mode only `'1'` and `'true'` return `true`.
- **trim(input [, chars])** - trim characters (whitespace by default) from both sides of the input.
- **ltrim(input [, chars])** - trim characters from the left-side of the input.
- **rtrim(input [, chars])** - trim characters from the right-side of the input.
- **escape(input)** - replace `<`, `>`, `&` and `"` with HTML entities.
- **whitelist(input, chars)** - remove characters that do not appear in the whitelist.
- **blacklist(input, chars)** - remove characters that appear in the blacklist.

### Strings only

This library validates and sanitizes **strings** only. All input will be coerced to a string using the following rules

- Call the `toString` property if available.
- Replace `null`, `undefined` or `NaN` with an empty string.
- Everything else is coerced with `input + ''`.

### Deprecations

Version 3 of the library deprecated some functionality

- **XSS sanitizer**: Here's [why](https://github.com/chriso/node-validator/commit/2d5d6999541add350fb396ef02dc42ca3215049e). Use [Google Caja](https://code.google.com/p/google-caja/source/browse/trunk/src/com/google/caja/plugin/html-sanitizer.js) instead.
- **Entity encoding**: Use [fb55/entities](https://github.com/fb55/node-entities) or [substack/node-ent](https://github.com/substack/node-ent).
- **Validator chaining**: The API was too unintuitive. I'd prefer to let users create their own higher-level patterns from the provided building blocks.

### Tests

- `make test` - run the test suite.
- `make test V=1` - run the test suite with added verbosity.
- `make test TEST=pattern` - run tests that match a pattern.
- `make coverage` - run a coverage analysis tool.
- `make lint` - run a lint tool.

### License (MIT)

Copyright (c) 2014 Chris O'Hara <cohara87@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
