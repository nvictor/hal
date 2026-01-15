# Harmonic Flow Notation (HFN) — Specification

This document defines the **syntax and semantics** of Harmonic Flow Notation.

## 1. Lexical Elements

### 1.1 Chord Symbol

A chord symbol is treated as an opaque token.

Examples:
- `Am`
- `E`
- `F#m7`
- `G7`

HFN does not interpret chord quality internally.

### 1.2 Operators

#### Center-state operators (prefix)

```
=  ⇄  ⊃  ↗  →
```

#### Harmonic motion operators (in-line)

```
=  ⇄  →
```

---

## 2. Grammar (EBNF)

```
Song        ::= { Section }

Section     ::= SectionHeader ":" SectionBody

SectionHeader ::= Identifier

SectionBody ::= [ CenterState ] "(" HarmonicMotion ")"

CenterState ::= CenterOperator Chord

HarmonicMotion ::= ChordMotion
                 | ChordMotion Operator ChordMotion

ChordMotion ::= Chord
              | Chord Operator

Operator    ::= "=" | "⇄" | "→"

CenterOperator ::= "=" | "⇄" | "⊃" | "↗" | "→"

Chord       ::= <opaque chord symbol>

Identifier  ::= <free text until ':'>
```

## 3. Semantics

### 3.1 Center State

A center state defines tonal gravity at the section level.

- `=X` establishes X as a stable center
- `⇄X` establishes X with internal harmonic motion
- `⊃X` prolongs or expands X
- `↗X` increases tension toward X
- `→X` indicates arrival of X as the next center

### 3.2 Harmonic Motion

Harmonic motion describes chord behavior within a section.

- `=` sustains the current chord
- `⇄` alternates between two chords
- `→` indicates directed progression

## 4. Valid Examples

```
Verse: Am ⇄ F
Pre: ↗E Am → Dm → E
Chorus: ⇄E E ⇄ G
Outro: =Am Am =
```

## 5. Invalid Examples

```
Verse: ⇄
Intro: Am →
```

## 6. Parsing Notes

- HFN is **line-oriented**: each section is represented as a single logical line of text.
- Chord symbols are not validated by the grammar.
- Parsers should output a structured representation with:
  - section name
  - optional center state
  - ordered chord motion list

## 7. Reference Implementation

A reference parser may be provided in Python to:
- Validate HFN syntax
- Produce a JSON representation
- Serve as an executable specification
