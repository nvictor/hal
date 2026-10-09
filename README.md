# Harmonic Architecture Language (HAL)
**Version:** 1.1.0

HAL is a compact notation for describing harmonic center and harmonic motion across a song form.

It captures section-level tonal gravity, transitions, and resolution trends. It does not capture bar-level timing, voice leading, exact rhythm, or Roman numeral function.

## Syntax

```text
HAL ::= <Section>+
Section ::= <Name> ":" [<CenterState>] "(" <Motion> ")"
Name ::= <Text>
CenterState ::= ("=" | "⇄" | "⊃" | "↗" | "↘" | "→") <Chord>
Motion ::= <Phrase> ("," <Phrase>)*
Phrase ::= <Chord> (<Operator> <Chord>)*
Chord ::= <ChordName> ["↑" | "↓"]
Operator ::= "=" | "⇄" | "→"
```

Example:

```text
Verse: ⇄Am (Am ⇄ F → G)
```

The center-state prefix describes the section's harmonic gravity. The motion inside parentheses describes chord-to-chord movement.

## Symbols

### Center State

Use a center-state prefix before the motion to name the section's home feeling.

- `=X`: Established or static center.
- `⇄X`: Stable but oscillating center.
- `⊃X`: Prolonged or expanded center.
- `↗X`: Building harmonic tension toward X.
- `↘X`: Releasing harmonic tension toward X.
- `→X`: Transitioning from the previous center to X.

### Chord Motion

Use in-line operators inside parentheses to describe movement between chords.

- `=`: Sustain or pedal.
- `⇄`: Oscillation.
- `→`: Directed progression.

### Modifiers

- `↑`: Chord displaced up an octave.
- `↓`: Chord displaced down an octave.
- `,`: Phrase separator inside a section.

## Rules

- A section must have a name.
- Chord motion must be contained in parentheses.
- The center-state prefix sets the context for the whole section.
- Operators define the type of motion, not exact duration.
- If no new center is declared, the previous center is assumed to persist.
- HAL intentionally avoids Roman numerals to keep focus on flow over theory.
- Use `=X (X)` for a static center with no motion.
- Use `=X (X = X)` only when explicitly showing sustained or pedal motion.

## Live Shorthand

Live shorthand is for fast capture while listening. Canonical HAL should use the full symbols.

- Omit section names when capturing only a tonal roadmap.
- Use `~` for `⇄`.
- Use `>` for `→`.

Example:

```text
~Am (Am~F>G)
```

Canonical form:

```text
Section: ⇄Am (Am ⇄ F → G)
```

## Examples

### Fictional song in A minor

```text
Intro: =Am (Am)
Verse: ⇄Am (Am ⇄ F)
Verse 2: ⊃Am (Am ⇄ F → Dm)
Pre: ↗E (Am → Dm → F → E)
Chorus: ⇄E (E ⇄ G)
Post: =E (E)
Bridge: →C (E → F → C)
Break: =C (C)
Final Chorus: ↗E (C → Am → E ⇄ G)
Outro: ↘Am (E → Am)
```

Tonal roadmap:

```text
=Am ⇄Am ⊃Am ↗E ⇄E =E →C =C ↗E ↘Am
```

### Holy Forever

"Holy Forever" (Bethel Music & Jenn Johnson):

```text
Intro: ⊃Bb (Bb → C → Am → Dm → C)
Verse: ⊃F (F → Bb → C → Dm → C → Bb → F)
```

### Way Maker

"Way Maker" (Leeland):

```text
Intro, Verse, Chorus: ⊃E (A → E → B → C#m)
Build: ⊃E (A → G#m → B → C#m)
```

### What A Beautiful Name

"What A Beautiful Name" (Hillsong Worship):

```text
Intro: =D (D)
Verse: ⊃D (D → G → Bm → A → Bm → C#° → D)
Chorus: ⊃D (D → A → Bm → A → G → F#m → A → Bm → A → G)
Bridge: ⊃G (G → A → Bm → F#m → G → A → Bm → A)
```

### Wings Of Death / Introduction

"Wings Of Death / Introduction" (Jeroen Hippel):

```text
Intro: =Am (Am)
Verse: ⇄C (C → B° → Am → C → B°)
Inter: ⇄Am (Am → Dm → C → Am → G → Am)
Chorus: ⇄Am (
    Am → C → B° → Am → G → Am → Em,
    C → Em → Dm → Em → Dm → Em,
    Em → Dm → C → Am → G → Am,
    Am → B° → C → Dm → Am
)
```

## Quick Reference

- `Verse: ⇄Am (Am ⇄ F → G)`: Section with oscillating A minor center and directed motion toward G.
- `Intro: =Am (Am)`: Static A minor center with no chord motion.
- `Section: =X (X = X)`: Static center with explicit sustain or pedal motion.
- `Bridge: →C (E → F → C)`: Section transitioning from the previous center to C.
- `Final Chorus: ↗E (C → Am → E ⇄ G)`: Section building harmonic tension toward E.
- `Outro: ↘Am (E → Am)`: Section releasing harmonic tension toward A minor.
- `Chorus: ⇄Am (Am → C → B° → Am, C → Em → Dm)`: Section with two phrase groups.
- `~Am (Am~F>G)`: Live shorthand for `⇄Am (Am ⇄ F → G)`.
