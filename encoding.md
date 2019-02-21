# Characters and encoding

> It does not make sense to have a string without knowing what encoding it uses.



## Character Set

- List of distinct characters -> Integers (code-points) are mapped to each character
- Typical character sets: `ASCII`, `Unicode`, `ISO-8859-1`



### ASCII

- English no accent code
- 7 bits used to display up to 127 different things
- 32 -> space, 65 -> "A"
- spare bit could be used by programs



### OEM-Trouble

- multiple manufactures created their own charset by extending the last bit and changing things in the lower ones for their purposes



### ANSI-Standard

- idea was to standardize the charsets that got created by different OEMs
- agreement found on the lower 7 bits (almost the same as ASCII)
- no agreement could be found on the 8th bit
- code pages got created to specify the 8th bit for different regions
- MS-DOS featured multiple code-pages to display different ANSI-formed charsets from English to Icelandic ..
- Almost no multi lingual code page got created -> no support to show characters from different code-pages e.g. Greek and Hebrew at the same time



### Unicode

- Internet required a larger charset to display characters from multiple languages at the same time
- Effort to include all existent characters in the same charset



### Code-point examples

- Display Unicode code-points
    ```bash
    >> 'a'.codepoints.to_a
    => [97]
    >> '€'.codepoints.to_a
    => [8364]
    ```

    

- Display ISO-8859-15 code-points
    ```bash
    >> 'a'.encode('iso-8859-15').codepoints.to_a
    => [97]
    >> '€'.encode('iso-8859-15').codepoints.to_a
    => [164]
    ```



## Code-Page

- Special-Code-Page for different charsets based on ANSI



## Encoding

- Mechanism to map between characters and byte-based representation -> transfer characters into bytes
- Describes how to represent integer code points in the memory
- Typical encodings are: UTF-8, Windows-1252, ISO-8859-1 (Latin1)
- UTF-8 maps the Unicode Character Set into bytes



### Code-point examples

- Display UTF-8 encoding into bytes:

    ```bash
    >> 'a'.bytes.to_a
    => [97]
    >> '€'.bytes.to_a
    => [226, 130, 172]
    ```

- Display ISO-8859-15 encoding into bytes:
    ```bash
    >> 'a'.encode('iso-8859-15').bytes.to_a
    => [97]
    >> '€'.encode('iso-8859-15').bytes.to_a
    => [164]
    ```



### UCS-2 / UTF-16

- idea just use two bytes / 16 bits to store for each unicode character
- Storage of Codeword Hello in Unicode?

    - Hello is represented by Unicode-Codepoints: U+0048 U+0065 U+006C U+006C U+006F
    - Codeword can be stored by

        ```bash
        high-endian: 00 48 00 65 00 6C 00 6C 00 6F
        low-endian: 48 00 65 00 6C 00 6C 00 6F 00
        ```

    - Problem: a lot of zeros



### BOM (Byte-Order-Mark)

- Define if the document is stored with high or low ending by adding hex code before each Unicode string (FE FF or FF FE)



### UTF-8

- Idea was to avoid the double memory demand for Unicode when it's possible
- Code-points from 0-127 are still stored in one byte
- Code-points from 128 are stored stored using from 2 to 6 bytes
- Codeword Hello (U+0048 U+0065 U+006C U+006C U+006F) can now be stored without zeros

    ```bash
    48 65 6C 6C 6F
    ```



---



## References

- https://stackoverflow.com/questions/19109899/what-is-the-exact-difference-between-windows-12521-3-4-and-iso-8859-1

- https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/
