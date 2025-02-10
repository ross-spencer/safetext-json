# safetext characters

The characters described in this JSON file are used for steganographic purposes.
That is, they can be hidden in streams of text and while they remain
imperceivable to the human eye, can be used to ecode messages, or some other
payload that is otherwise unknown to the user.

In the year 2025, being able to indentify text streams with this kind of
information is as important as ever.

Extracted from David Jacobson's [SafeText][safetext-1] in support of more
steganographic tooling.

[safetext-1]: https://github.com/DavidJacobson/SafeText/

The idea is to make these characters available in JSON so that they can be
consistently processed and output, like the [big list of naughty strings][blns].

[blns]: https://github.com/minimaxir/big-list-of-naughty-strings/tree/master

## More information

Zach Aysan describes the importance of knowing about the characters listed in
these SafeText lists and their potential uses fingerprinting text to enable
corporations and bad-actors to identify whistleblowers.

Zach further describes [counter measures][counter-1] that are important for
journalists:

1. Avoid releasing excerpts and raw documents.
2. Get the same documents from multiple leakers to ensure they have the exact
same content on a byte-by-byte level.
3. Manually retype excerpts to avoid invisible characters and homoglyphs.
4. Keep excerpts short to limit the amount of information shared.
5. Use a tool that strips non-whitelisted characters from text before sharing
it with others.

It is hoped other tools supporting these counter-measures can be created from
a source of truth such as this list started by David Jacobson.

[counter-1]: https://www.zachaysan.com/writing/2018-01-01-fingerprinting-update

## Notes on Unicode

The file [safetext-ucd.json](safetext-ucd.json) was output using Cooper Hewitt's
[Unicode UCD library][ucd-1] for more accurate Unicode character names.

[ucd-1]: https://github.com/cooperhewitt/py-cooperhewitt-unicode/tree/master

## Character classes

Character classes described in this file.

### ZERO-WIDTH CHARACTERS

Zero width characters are visible when reading, as they take up no space.
However, they can be used in fingerprinting.

### NON-STANDARD SPACES

These are not zero-width, they are visible. However, they are unique, and need
to be normalized",

### HOMOGLYPHS

> NB. To quickly verify that these characters are not Latin, enter them in
> Google with autocomplete. The response should be a character set other than
> Latin.

The characters are organized by:

```text
CHARACTER SET _ [UPPER/LOWER] _ LATIN COUNTERPART
```

e.g.: `GREEK_small_M`

In the UCD output, characters are written as follows:

```text
UCD CHARACTER NAME ([UPPER/LOWER] LATIN COUNTERPART)
```

e.g.: `GREEK CAPITAL LETTER MU (small M)`

#### Cyrillic characters

Are used in Russian, Belarusian, Ukrainian, Bulgarian, Serbian, Bosnian,
Croatian and more.

This character set is the most common used in homoglyph fingerprinting as it has
the most characters that are visually similar to their Latin counterparts

#### Greek characters

There are Greek characters that are identical to Cyrillic, German, and Serbian
however this tool is built around Latin.

## LICENSE

These files are [licensed][license] MIT per the original SafeText license.

[license]: LICENSE.md
