#PigLatin

Famous PigLatin translator in JS.

## API

### `PigLatin`

This is a JS class which should be initialized by providing a string, if no initial argument or not a valid string is provded, an `Error` will be thrown.

`let translator = new PigLatin('michelada');`

### `#phrase`

It return current's instance string.
```
translator.phrase();
> 'michelada'
```

### `#reset`

It resets the current's instance string
`translator.reset('colima')`

### `#translate`

It transforms the current string according to PigLatin's set of rules.
```
translator.reset('michelada fria');
translator.phrase();
> 'michelada fria'
translator.translate();
> 'icheladamay iafray'
```

## Implementation

The basic translation/classification rules of words has been implemented with the aid of regular expressions. For example:

```
const STARTS_WITH_VOWEL = /^[aeiou]/i;
const STARTS_WITH_CONSONANT = /^[b-df-hj-np-tv-z]{1}/i
const STARTS_WITH_TWO_CONSONANTS = /^[b-df-hj-np-tv-z]{2}/i;
const ENDS_WITH_VOWEL = /[aeiou]$/i;
const ENDS_WITH_CONSONANT = /[b-df-hj-np-tv-z]$/i;
const ENDS_WITH_Y = /y$/i;
const CAPTURE_LEADING_CONSONANTS = /^([b-df-hj-np-tv-z]{1,})([a-zA-Z]*)/i;
const PHRASE = /\w+/ig;
```

Also a few word transformations has been done by using regex captures and replacing, particular string transformations has been implemented using core `String` methods like `slice` or `replace`.

# Test

Run `npm i; npm test`