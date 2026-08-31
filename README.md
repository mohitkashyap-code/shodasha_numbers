# Shodasha Numbers

**A Geometric Base-16 Representation with a Native Glyph and Naming
System**

Shodasha is a proposed visual notation for base-16 (hexadecimal) values.
It keeps hexadecimal's existing 4-bit structure while replacing the
alphabetic symbols `A-F` with a dedicated set of geometric glyphs.

Each Shodasha numeric glyph is derived from four spatial quadrants, with
each quadrant representing one bit of a hexadecimal nibble. This creates
a deterministic relationship between the glyph geometry and the
underlying 4-bit value.

> **Status:** Under Development / Draft Specification

## Overview

Shodasha is intended as a **human-facing notation layer for
hexadecimal**, not as a replacement for hexadecimal computation or
binary hardware.

The proposal explores whether a dedicated geometric numeral set can
provide a more visually uniform way to write, read, recognize, teach,
pronounce, and display hexadecimal values.

The underlying numerical value remains unchanged. Software can continue
to store and calculate values as ordinary integers, bytes, bit strings,
or hexadecimal values while using Shodasha as an alternative
representation.

## Core Idea

A hexadecimal digit represents exactly four binary bits.

Shodasha represents those four bits geometrically:

-   Each glyph contains four logical spatial quadrants.
-   Each quadrant represents one binary bit.
-   A quadrant in state `0` is represented by a diagonal path.
-   A quadrant in state `1` is represented by its inner axial
    boundaries.
-   The sixteen possible 4-bit combinations produce sixteen dedicated
    numeric glyphs.

This creates a direct mapping:

**4-bit value → Shodasha glyph**

The numerical meaning of a glyph does not depend on its spoken name.

## What the Specification Contains

1.  **Executive Summary** --- purpose, goals, scope, and non-goals.
2.  **Motivation** --- why a different human-facing representation of
    hexadecimal may be useful.
3.  **Glyph Architecture** --- the four-quadrant geometric construction
    and binary relationship.
4.  **Reference Glyph Directory** --- the sixteen numeric glyphs and
    their corresponding 4-bit values.
5.  **Special Characters** --- `NULL`, `TRUE`, `FALSE`, and optional
    `HEAD`/`TAIL` framing markers.
6.  **Naming System** --- spoken names for individual hexadecimal values
    and positional compounds for larger values.
7.  **Implementation Considerations** --- fonts, keyboard input,
    parsing, OCR/computer vision, and potential applications.
8.  **Validation Plan** --- proposed experiments for recognition,
    writing, learning, OCR, transcription, parsing, font consistency,
    and pronunciation.
9.  **Known Limitations and Open Questions** --- properties that remain
    unvalidated.
10. **Conclusion** --- current scope and intended next steps.

## Numeric Values

  Hexadecimal   Binary   Shodasha Name
  ------------- -------- ---------------
  `0`           `0000`   Sif
  `1`           `0001`   Uni
  `2`           `0010`   Ome
  `3`           `0011`   Tri
  `4`           `0100`   Ĉar
  `5`           `0101`   Pen
  `6`           `0110`   Liu
  `7`           `0111`   Sep
  `8`           `1000`   Okt
  `9`           `1001`   Nau
  `A`           `1010`   Kumi
  `B`           `1011`   Isa
  `C`           `1100`   Kur
  `D`           `1101`   Oru
  `E`           `1110`   Ran
  `F`           `1111`   Zen

The naming system is separate from the numerical mapping. The
specification provides an **Esperanto-Oriented Form / English Spelling**
presentation for the names.

## Special Characters

Shodasha defines five special characters in addition to the sixteen
numeric glyphs:

-   `NULL`
-   `TRUE`
-   `FALSE`
-   `HEAD`
-   `TAIL`

`NULL`, `TRUE`, and `FALSE` are distinct typed values rather than
members of the numeric nibble set.

`HEAD` and `TAIL` are optional framing and stream-context markers. When
used, a stream can be represented conceptually as:

`HEAD + payload + TAIL`

The framing markers do not change the numerical or boolean value of the
payload.

## Naming System

Shodasha includes a spoken naming layer so that hexadecimal values can
be read without reverting to the Latin `A-F` convention.

For larger values, names are formed positionally. The draft uses:

-   `-jo` for the next hexadecimal positional level
-   `-ja` for the following positional level
-   additional positional names for larger values
-   triad grouping for long hexadecimal values

Examples include:

-   `10` → **Unijo**
-   `1F` → **Unijo Zen**
-   `100` → **Unija**
-   `1FF` → **Unija Zenjo Zen**

The naming layer is independent of the underlying numeric
representation.

## Implementation

Shodasha is intended to be implementable without changing the underlying
numerical representation.

### Digital Font

A production font can contain the sixteen numeric glyphs and five
special characters. The geometric construction rules should accompany
the font so that alternate fonts remain recognizably compatible.

### Keyboard and Input

Existing hexadecimal input such as `0-9` and `A-F` can be converted to
Shodasha glyphs. This allows Shodasha to be displayed without requiring
a completely new physical keyboard layout.

### Software Parser

A parser can map the sixteen numeric glyphs internally to values `0-15`,
while treating special characters as separate token types.

### OCR and Computer Vision

Recognition should be evaluated experimentally rather than assumed to be
superior. A useful dataset would include multiple writers, writing
speeds, pen types, rotations, scales, noise levels, and incomplete
strokes.

## Potential Applications

Possible human-facing applications include systems that commonly use
hexadecimal notation, such as:

-   computer networking addresses
-   memory addresses
-   microprocessor and integrated-circuit pin identification
-   digital colour values
-   byte and binary data representation
-   hardware registers
-   other systems that commonly use hexadecimal notation

These are **potential use cases**, not established performance claims.

Shodasha would represent the value differently for humans while allowing
the underlying data format and hardware representation to remain
unchanged.

## Validation

The current proposal has not established that Shodasha is better than
conventional hexadecimal.

The proposed validation areas are:

1.  Visual recognition
2.  Writing speed
3.  Learning curve
4.  OCR accuracy
5.  Noise and rotation
6.  Transcription accuracy
7.  Parsing accuracy
8.  Font consistency
9.  Speech and pronunciation

These experiments are intended to determine whether the proposed
properties of the notation are supported by practical evidence.

## Current Limitations

The specification explicitly leaves several questions open:

-   The glyphs have not yet been validated through a large handwriting
    or OCR dataset.
-   Writing speed has not yet been shown to be better than ordinary
    hexadecimal.
-   Human learning performance has not yet been shown to be better than
    `0-9/A-F`.
-   The effect of optional `HEAD`/`TAIL` framing requires measurement.
-   The spoken naming system requires linguistic usability testing
    across different language backgrounds.
-   Unicode standardization is not addressed by the current draft.
-   Shodasha does not itself provide new arithmetic, storage efficiency,
    or processor instructions.

## What Shodasha Is --- and Is Not

### Shodasha is

-   a proposed geometric base-16 notation
-   a visual representation of hexadecimal values
-   a deterministic glyph system based on four binary bits
-   a human-facing representation that can be implemented in software
    and fonts
-   a notation with an associated spoken naming system

### Shodasha is not

-   a replacement for binary logic
-   a replacement for CPU instruction sets
-   a replacement for decimal arithmetic
-   a new programming language
-   a new storage format by itself
-   a claim of improved performance that has already been experimentally
    proven

## Project Status

This is a **draft specification**.

The purpose of the project at this stage is to define the system clearly
enough for implementation, experimentation, criticism, and future
improvement.

The next practical steps are expected to include:

-   a digital font
-   a hexadecimal-to-Shodasha converter
-   parser support
-   keyboard/input support
-   handwriting data collection
-   OCR benchmarking
-   user studies

## Document

The primary specification is:

**`Shodasha_Numbers.pdf`**\
**`images/`**

It contains the complete description of the proposed numeral system,
glyph architecture, naming system, implementation considerations,
validation plan, limitations, and conclusion.

## Author

**Mohit Kashyap**

## License

This project is licensed under the MIT License.
