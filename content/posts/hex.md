---
title: "Understanding Hexadecimal"
summary: "hexadecimal: what it is, what it's used for, and examples in the wild"
date: 2020-02-06
draft: false
tags: [programming]
---

If you come into programming without a computer science background (honestly, even with one, no one taught me this stuff), you may have looked at sequences like `\u2318` or `&#x0041;` and wondered what it meant. If you have ever tried to read a stack trace or a crash dump of one of your programs, you may see some similar sequences like `0x39` or `0xF5`. If you are a web developer, you are most likely familiar with something called hex color codes, used for coloring your text, background, and borders, like `#FFFFFF` for white, or `#000000` for black.

All of these examples are some variation of _hexadecimal_ numbers, or hex for short. Typically the hex is used in combination with some sort of prefix to denote it as a hex number. Most programming languages have the ability understand hex literals so long as you use the specified prefix. In most languages, it tends to be `0x` followed by the number. In CSS, it is prefixed with `#`.

In order to understand the what and why behind hexadecimal, it may help to first exlore a more fundamental topic.

## Where do numbers come from?

To better understand hexidecimal, it helps to understand numbers and numerical representation. A number is something used to count, measure, or label. Numerals are the symbols used to represent numbers. Our pre-historic ancestors have been counting on their fingers for millenia, so you could say our fingers were the first numerals, and adding up the fingers together would have been the first numeral system. The Egyptians are credited with the first _ciphered_ numeral system, meaning they mapped them to hieroglyphs.

![Image credit to Encyclopedia Britannica](/img/egyptnumerals.jpg "Ancient Egyptian Numeral System")

The Greeks quickly followed, mapping their numbers to Doric and Ionian.
The Sumerians and Babylonians represented numbers using wedge-shaped marks on clay tablets also known as Cuneiform. The Romans, arguably the most famous, used Roman Numerals.

Today, outside of Super Bowls, time units, angles, and watch faces [^1], the the vast majority of people know numbers as being 0-9. This is known as the Indo-Arabic numeral system (Fun fact: Zero wasn't discovered until 628 AD by an Indian mathematician and astronomer named Brahmagupta).

Besides numerals, another important component in a numeral system is the _positional notation_. Most of us are taught from a young age how to count using the positional notation of base 10, also known as decimal. You may recall being taught in school the different "places" that a number, such as the "ones", "tens", "hundreds", and so on. Positional systems are what allow you to easily express larger values beyond the basic numerals of 0-9. The Babylonians were credited with creating the first positional system referred to in modern times as _Sexagesimal_. The overwhelming majority of the world uses decimal today.

Thus, when we think of "numbers" in the modern sense, we are really talking about two things: a numeral system, such as Indo-Arabic, and a positional system, such as base 10.

If we attempt to visualize base 10, it might look something like this:

```
// the base 10 positional system:
______ ______ ______ ______ ______
 10^4   10^3   10^2   10^1   10^0
```

If you evaluate those exponents, you may start to see that famous language in regards to those positions: _"ones, tens, hundreds, thousands"_. Any number raised to the zero power is 1 or ones. Then you have 10^1 which is 10 or tens, 10^2 which is 100 or hundreds, 10^3 which is 1000, 10^4 which is 1000 or thousands. In the immortal words of Gus Portokalos, ["There you go."](https://www.youtube.com/watch?v=VL9whwwTK6I)

What is interesting about this is that it is generalizable. Starting from the furthest digit to the right, you have position 0. Each time you add a significant digit to the left, you have a new position, so you add one.

```
// a generalized form:
______ ______ ______ ______ ______
base^n base^3 base^2 base^1 base^0
```

As you may have caught whiff of by now, you don't have to use 10 as the base. You can use other numbers, like 2, 4, 6, 8, 12, 16, or even 60. For reasons beyond the scope of this post, there are qualities, both mathematical and pratical, that make certain bases work better than others. The pervailing theory around base 10's popularity is because people liked counting with their fingers.

## The answer to our first riddle

Now we are ready to put it all together. _Hexadecimal_ is a positional numeral system that uses 16 symbols, 0-9 and A-F, and a base of 16. Since there are only 10 Indo-Arabic numbers to choose from, hex makes use of the first 5 letters of the English alphabet. To count to 10 in decimal, you would say outloud, _"one, two, three...nine, ten!"_. To count to 16 in hexadecimal, you would say outloud, _"one, two, three...A, B, C, D, E, F, ten!"_. A is 10, B is 11, C is 12, D is 13, E is 14, and F is 15. [^2]

```
// the base 16 positional system:
______ ______ ______ ______ ______
 16^4   16^3   16^2   16^1   16^0
```

The maximum value you can represent using a single hexadecimal digit, sometimes called a _nibble_, is 15. Just like in decimal when you pass 9 you have to add an aditional position, in hex when you pass 15 you have to add another position.

```
// going from 9 to 10 in decimal

  9         ->        1     0
10^0        ->      10^1   10^0

// going from 15 to 16 in hexadecimal
  F         ->        1     0
16^0        ->      16^1   16^0
```

Another way to arrive at a value a hexadecimal digit represents is to take the nibble and it's position value, multiply them together, and add it to the next. In the above example, we would take `(0*16^0)` and add it to `(1 * 16^1)`, which is 16. With this knowledge, we now have the ability to represent any decimal value we wish in hex.

```
// some examples:

// decimal 345

  1     5      9
16^2   16^1   16^0

// 1 times 16^2 + 5 times 16^1 + 9 times 16^0
// 1 times 256 + 5 times 16 + 9 times 1
// 256 + 80 + 9
// = 345
```

## Why Hexadecimal?

Hexadecimal seems like an odd choice at first glance. Computers like to do everything in 1's and 0's. Humans learned to count with their hands so we count by 10's. Where did counting by groups of 16s come from? In order to understand this, we now turn our focus to binary.

## Binary

Armed with our new knowledge of number systems, binary is simply a base 2 positional system using the numerals 0 and 1.

```
// binary (base 2)
______ ______ ______ ______ ______
  2^4    2^3    2^2    2^1    2^0
```

The reason binary is found in so many electronics is because 0 and 1 is really easy to implement in digital circuts using logic gates. The "high" waveform of a signal can be used to represent "on" or 1, and a "low" waveform can be used to represent "off" or 0. As computers and electronics became more widespread, more people started to use binary.

A single binary digit is referred to as a _bit_. Eight bits equals a _byte_. Early computers could only consume 8 bits or a single byte at a time (The number of bits a CPU can consume all at once is typically called the _word size_). As we moved from 8-bit machines, to 8 byte machines, then 16, 32, to now 64, the size of binary code quickly became unmanagble for humans.

This is where hex comes in. Hex became a human-readable format for reading binary because of it's ability to represent _four_ bits in just one _nibble_ [^3]. It isn't known who exactly was the first person to discover this, but I am pretty sure the discovery went something like "Oh cool, you can use a single hex digit to represent 4 bits!"

Hex is now ubiquitous whenever binary is involved. It is especially useful for deciphering _binary-to-text encodings_, such as ASCII or Unicode. When we type the uppercase letter 'A', on our screens we see the letter, but to the computer using an ASCII or UTF8 encoding, that really is a `01000001`. Now suppose we had to recognize this in a stream of input or output trying to debug a program! Luckily, those smart computer science pioneer folk thought of us, because we can represent that entire sequence with the hex number of `41`

Typically, people use a "nibble table" or "table of nibbles" to assist in conversion. Visualizing it in a table also makes it apparent how straightforward the conversion is:

| hex&nbsp;&nbsp;&nbsp; | decimal |  binary   |
| :-------------------: | :-----: | :-------: |
|          `0`          |   `0`   | `0 0 0 0` |
|          `1`          |   `1`   | `0 0 0 1` |
|          `2`          |   `2`   | `0 0 1 0` |
|          `3`          |   `3`   | `0 0 1 1` |
|          `4`          |   `4`   | `0 1 0 0` |
|          `5`          |   `5`   | `0 1 0 1` |
|          `6`          |   `6`   | `0 1 1 0` |
|          `7`          |   `7`   | `0 1 1 1` |
|          `8`          |   `8`   | `1 0 0 0` |
|          `9`          |   `9`   | `1 0 0 1` |
|          `A`          |  `10`   | `1 0 1 0` |
|          `B`          |  `11`   | `1 0 1 1` |
|          `C`          |  `12`   | `1 1 0 0` |
|          `D`          |  `13`   | `1 1 0 1` |
|          `E`          |  `14`   | `1 1 1 0` |
|          `F`          |  `15`   | `1 1 1 1` |

We can now easily convert long sequences of binary digits into a more compact representation by grouping them into 4 bits and replacing them with the corresponding nibble. Try some combinations out!

## Color Codes, Binary-To-Text Encodings, and Crashing Programs

The last thing to do is tie all of this knowledge back to our other examples we have not discussed: hex colors, that you see in CSS such as `#FFFFFF`, the `\u2318` types you may see if you have a string of emojis, accent characters, or other non-standard alpha numeric characters in a string of text, and finally output you may see from a stack trace or debug log from your program crashing.

### Color codes

As we mentioned earlier, binary is the language of the machine. It's what your computers and electronics understand. It's one of those things when you hear about for the first time sounds crazy but is true: everything on your computer really is about zeros and ones. When you are specifying a hex color code in CSS, you are mapping a hex number to a Red-Green-Blue (RGB) color space with a 24-bit depth. If you consider the total number of combinations of red blue and green you can represent with 24 bits, it equals out to 16,777,216, of which 16,777,215 are used in computer representations.

Are you ready for a doozy? The max hex color code in binary is `111111111111111111111111`.

Luckily for us, armed with our new hexadecimal knowledge, we can make more sense of this by breaking it up into fours and mapping it to hex:

```
1111 1111 1111 1111 1111 1111
```

Now we can refer to our nibble table, and do the conversion. Each group of four 1's becomes an F:

```
F F F F F F
```

You may recognize this value: #FFFFFF is the hex color code for white!

### Binary-To-Text Encodings

What about that `\u2318` character sequence? More hex in action! This time, however, it also has a `\u` prefix which is commonly used in many programming languages to denote the start of a [Unicode](https://home.unicode.org/) _code point_ (The other most common prefix is `U+`). Sometimes you may see these sequences show up in code because the display or UI you are using isn't interpreting it as UTF-8 so it prints the raw value out. These are also handy when designing regular expressions to match certain characters or symbols in text.

## Where to Go From Here

We discussed some common examples of hexadecimal found in the wild. My hope is now you can approach these numbers and feel like you have a better grasp of what is going on. Hexadecimal is used in a variety of very important computing contexts such as memory addresses, encodings, color representation, and more. Remember that computers speak binary, and hex helps us humans read it.

The Wikipedia articles on these topics are all excellent and can provide some reinforced learning if you wish to learn more. Happy hacking.

### Links

1. [Wikipedia: Hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal)
2. [Wikipedia: Binary](https://en.wikipedia.org/wiki/Binary_number)
3. [Wikipedia: Numeral System](https://en.wikipedia.org/wiki/Numeral_system)
4. [Wikipedia: RGB Color Model](https://en.wikipedia.org/wiki/RGB_color_model)
5. [Wikipedia: Unicode](https://en.wikipedia.org/wiki/Unicode)
6. [If you really want to go down a rabbit hole: The Story of Mathematics](https://www.storyofmathematics.com/)
7. [If you want to flex those new memory address reading skills, try this article on reading Go stack traces](https://www.ardanlabs.com/blog/2015/01/stack-traces-in-go.html)

#### Footnotes:

[^1]: The Super Bowl and watch faces are examples of Roman Numerals still in use today, while time, angles, and geographic coordinates are examples of base 60, which was used by the Babylonians. Base 60 is also known as 'Sexagesimal'
[^2]: I found it really helpful when I was learning all of this to think of playing cards. We typically assign a numeric representation to the Jack (11), Queen (12), King (13), and Ace (1). A deck of cards written out thus looks like this: A,2,3,4,5,6,7,8,9,10,J,Q,K. Hex written out looks like this: 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F. It's not an exact mapping, but it helped normalize the concept a little more in my brain.
[^3]: _nibble_ is a playful little term that comes from the fact that a single hex digit represents 'half a byte' with 'byte' being a homophone for 'bite'
