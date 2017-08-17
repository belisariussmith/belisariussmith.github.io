# [](#header-1)Proteus


### [](#header-2)"the totally radixical tool"

> A command-line program for detecting, decoding, and converting radix-encoded strings.

> This program is meant to be used with the most popular base-encodings such as base64, hexadecimal, binary, etc. Also the encodings are expected to be in their most commonly used implementation of each respective radix.
    

##### [](#header-5)Supported radix (base-encodings)

1.  Binary
2.  Octal
3.  Decimal
4.  Hexadecimal
5.  Duotrigesimal (Base-32)
6.  Tetrasexagesimal (Base-64)
7.  _Pentoctogesimal (Base-85)*_

\* _Not yet implemented_

###### [](#header-6)Optimized Conversion

|          | ASCII   | Base-2  | Base-8  | Base-10 | Base-16 | Base-32 | Base-64 |
|:---------|:--------|:--------|:--------|:--------|:--------|:--------|:--------|
| ASCII    |         |    X    |    X    |    X    |   X     |    X    |    X    |
| Base-2   |    X    |         |         |         |         |         |         |
| Base-8   |    X    |         |         |         |         |         |         |
| Base-10  |    X    |         |         |         |         |         |         |
| Base-16  |    X    |         |         |         |         |         |         |
| Base-32  |    X    |         |         |         |         |         |         |
| Base-64  |    X    |         |         |         |         |         |         |

Those slots between radices where there is no optimization are instead run converted to ASCII first. This was a quick and dirty method used after each base-decoding was completed into ASCII. Eventually, every single conversion between radices will be completed so that the program is highly optimized no matter what is being encoded. 

As can be seen below, exapnsion can be made simply by creating the necessary function, no other modification is necessary: 

**Python Code**
```python
    # Quick validation
    if (encoding is decoding): return string         # No reason convert anything
    if ((encoding != ASCII) and (decoding != ASCII)):# Spool through ASCII conversion
      if (encoding+'2'+decoding in globals()):       # Conversion function exists
        return globals()[encoding+"2"+decoding](string)
      else:
        return conversion(ASCII, decoding, conversion(encoding, ASCII, string)) # recursion, ick!
    return globals()[encoding+"2"+decoding](string)
```




* * *