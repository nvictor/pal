# Parts Arrangement Language (PAL)
**Version:** 1.0.0

PAL is a compact notation for describing how parts are arranged, from a short idea to a complete song.

It captures part identity, part length, variations, order, and repeats. It does not capture section names, harmony, melody, groove, instrumentation, or dynamics.

## Syntax

```text
PAL ::= <Item>+
Item ::= <Part> | <Group>
Group ::= "(" <Part> <Part>+ ")" <Repeat>
Part ::= <Identifier> <Bars> [<Repeat>]
Identifier ::= <Letter> ["'"]*
Letter ::= "A" ... "Z"
Bars ::= <PositiveInteger>
Repeat ::= "x" <Count>
Count ::= integer, 2 or more
```

Example:

```text
A8 (B16 C16)x2 D8
```

Items are separated by spaces and read left to right.

Section names are outside PAL. Use any headings, labels, or layout in the surrounding document.

## Symbols

### Part

A part is a letter followed by its length in bars.

- `A8`: Part `A`, 8 bars.
- `B16`: Part `B`, 16 bars.

Assign letters in order of first appearance. Reuse a letter when the same part returns.

```text
A4 B4 A4
```

### Variation

Use an apostrophe to mark a variation of a part.

- `B'16`: A variation of part `B`, 16 bars.
- `B''16`: A second variation of part `B`, 16 bars.

### Repeat

Use `x` and a count to play a part or a group several times in a row. The count is the total number of plays.

- `A4x4`: Part `A`, 4 bars, played 4 times.
- `(B16 C16)x2`: Parts `B` and `C`, played in order, twice.

```text
A8 (B16 C16)x2 D8 = A8 B16 C16 B16 C16 D8
```

## Metadata

PAL has no time signature or tempo field. Record them as metadata beside the expression, never inside it:

```text
6/8 · 69 bpm · A8 (B16 C16)x2 D8
```

- Omit the signature when it is 4/4.
- Tempo is optional.
- Metadata applies to the whole expression.

## Rules

- Every part has a bar count.
- A group contains at least two parts and always has a repeat count.
- Use a repeat on the part itself, not a group, to repeat one part.
- Groups cannot be nested.
- A variation inside a repeated section breaks the group. Write it out.
- PAL describes one time signature per expression.

## Examples

### Idea

```text
A4 B4 A4
```

### Loop

```text
A4x4
```

### Song with a repeated cycle

Intro, verse, chorus, verse, chorus, ending:

```text
A8 (B16 C16)x2 D8
```

### Song with a variation

The second verse changes:

```text
A8 B16 C16 B'16 C16 D8
```

### Compound meter

```text
6/8 · 69 bpm · A4 (B8 C8)x2 A4
```

## Quick Reference

- `A8`: Part `A`, 8 bars.
- `A'8`: Variation of part `A`, 8 bars.
- `A4x4`: Part `A`, played 4 times.
- `(A8 B8)x2`: Parts `A` and `B`, played twice.
- `6/8 · A8`: Time signature beside the expression.
- `69 bpm · A8`: Tempo beside the expression.
