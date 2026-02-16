# Harmonic Flow Notation (HFN)
**Version:** 1.0.0

HFN is a lightweight, section-level notation for describing harmonic center (tonal gravity) and harmonic motion across a song form.

## Model: Captures vs Ignores

| Captures | Ignores |
| :--- | :--- |
| Tonal gravity / Center state | Bar-level timing |
| Section-level harmonic motion | Voice leading details |
| Tension and resolution trends | Exact rhythmic duration |
| Structural transitions | Roman numeral function |

## Canonical Syntax

```text
Section ::= <Name> ":" [<CenterState>] "(" <Motion> ")"
CenterState ::= ("=" | "⇄" | "⊃" | "↗" | "→") <Chord>
Motion ::= <Chord> (<Operator> <Chord>)*
Operator ::= "=" | "⇄" | "→"
```

Example: `Verse: ⇄Am (Am ⇄ F → G)`

## Symbol Table

### 1. Center-State (Prefix)
Describes the "home" feeling of a section.
- `=X`: Established / static center.
- `⇄X`: Stable but oscillating center.
- `⊃X`: Prolonged or expanded center.
- `↗X`: Intensifying toward X.
- `→X`: Directed toward a new center.

### 2. Chord Motion (In-line)
Describes movement between chords within a section.
- `=`: Sustain / pedal.
- `⇄`: Oscillation.
- `→`: Directed progression.

### 3. Modifiers
- `↑` / `↓`: Octave shifts (suffix).
- `,`: Phrase separator.

## Semantics Rules

- **Sectional Scope:** HFN defines intent at the section level, not the measure level.
- **Center Dominance:** The center-state prefix sets the context for all chord motion within that section.
- **Motion Priority:** Operators define the *type* of movement, not the specific duration.
- **Implicit Continuity:** Unless a new center is declared, the previous center is assumed to persist.

## Constraints / Invariants

- A section must have a name.
- Chord motion must be contained within parentheses.
- HFN intentionally avoids Roman numerals to maintain focus on flow over theory.

## Live Mode (Shorthand)

Optimized for high-speed harmonic capture.

- Omit section names if just capturing a roadmap.
- Use `~` for oscillation if `⇄` is hard to type.

Example: `~Am (Am~F>G)`

---

See [EXAMPLES.md](./EXAMPLES.md) for usage and [CHEATSHEET.md](./CHEATSHEET.md) for a quick reference.
