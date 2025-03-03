# safetext-json

The characters described in this JSON file are used for steganographic purposes.
That is, they can be hidden in streams of text and while they remain
imperceivable to the human eye, can be used to encode messages, or some other
payload that is otherwise unknown to the user. Steganographic characters can 
be used to _obfuscate_ information as well, where something like a zero-width 
character will create an artificial word boundary affecting string matching.
Dash alternatives to hyphens might also hide phone numbers or other sensitive
numbers that are often encoded using these.

In the year 2025, being able to identify text streams with this kind of
information is as important as ever.

Extracted from David Jacobson's [SafeText][safetext-1] in support of more
steganographic tooling.

[safetext-1]: https://github.com/DavidJacobson/SafeText/

The idea is to make these characters available in JSON so that they can be
consistently processed and output, like the [big list of naughty strings][blns].

[blns]: https://github.com/minimaxir/big-list-of-naughty-strings/tree/master

## safetext tooling

* [safetext-python][safetext-1] (by David Jacobson)
* [safetext-golang][safetext-2]

[safetext-2]: https://github.com/ross-spencer/safetext

## More information

Zach Aysan describes the importance of knowing about the characters listed in
these SafeText lists and their potential uses fingerprinting text to enable
corporations and bad-actors to identify whistleblowers.

Zach further describes [counter measures][counter-1] that are important for
journalists:

<!--markdownlint-disable-->

| countermeasure                                                                                                   | effectiveness    |
|------------------------------------------------------------------------------------------------------------------|-----------------------|
| Avoid releasing excerpts and raw documents.                                                                      | works perfectly       |
| Get the same documents from multiple leakers to ensure they have the exact same content on a byte-by-byte level. | works perfectly       |
| Manually retype excerpts to avoid invisible characters and homoglyphs.                                           | works unless careless |
| Keep excerpts short to limit the amount of information shared.                                                   | works unless unlucky  |
| Use a tool that strips non-whitelisted characters from text before sharing it with others.                       | doesn't work          |

<!--markdownlint-enable-->

Aysan notes that stripping non-allowlisted characters does not offer enough
protection. This is recognized with this list. Tools generated using safetext-json
might support identification and characterization, andit is hoped other tools will
appear from list such as this started by David Jacobson. But please remember to 
always look after your identity and the identity of others using the most thorough
methods possible.

[counter-1]: https://www.zachaysan.com/writing/2018-01-01-fingerprinting-update

### See also

A [live demo of digital steganography][neatnik-2] using zero-width characters
from [neatnik][neatnik-1].

[neatnik-2]: https://neatnik.net/steganographr/
[neatnik-1]: https://github.com/neatnik/steganographr

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
UCD CHARACTER NAME :: ([UPPER/LOWER] [LATIN COUNTERPART|DEL|SPACE])
```

> NB. Parsers should split on `::` and then read the contents of the the round
> brackets. A direct replacement can be made for characters other than
> `DEL`. `DEL` denotes removing the character entirely where the character
> exists.

Additionally, homoglyphs are separated into character sets per language to
all for the data to be loaded into safetext handlers in other languages.

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
