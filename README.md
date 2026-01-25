# Harmonic Flow Notation (HFN)

Harmonic Flow Notation (HFN) is a lightweight, section-level notation for describing harmonic center (tonal gravity) and harmonic motion across a song form.

HFN is designed to answer questions like:
- What harmony is this section centered on?
- Is this section static, oscillating, expanding, or moving toward a new center?
- Where does the song build tension and where does it resolve?

HFN intentionally avoids bar-level analysis and Roman numeral theory. It is meant for songwriting, arranging, quick analysis, and music software tooling.

Quick example:

```
Intro: =Am (Am =)
Verse: ⇄Am (Am ⇄ F)
Pre: ↗E (Am → Dm → E)
Chorus: ⇄E (E ⇄ G)
Outro: =Am (Am =)
```

## Core Idea

HFN separates two concerns:

1. Center state — what feels like “home” at a given moment
2. Harmonic motion — how chords move within or away from that center

A section may:
- Omit the center when it is obvious, or
- Explicitly declare it when changing, ambiguous, or structurally important

## Symbols

### Center-state operators (prefix)

| Notation | Meaning |
|--------|--------|
| `=X` | Established / static center on X |
| `⇄X` | Stable but oscillating center on X |
| `⊃X` | Prolonged or expanded center on X |
| `↗X` | Intensifying toward X |
| `→X` | Directed toward new center X |

Examples:
- `=Am`
- `↗E`
- `→C`

### Harmonic motion operators (in-line)

| Notation | Meaning |
|--------|--------|
| `=` | Sustain / pedal |
| `⇄` | Oscillation |
| `→` | Directed progression |

Examples:
- `Am =`
- `Am ⇄ F`
- `Am → Dm → E`

## Section Syntax

HFN is one line per section:

```
SectionName: <optional center-state> (<chord motion>)
```

Examples:
- `Intro: =Am (Am =)`
- `Verse: ⇄Am (Am ⇄ F)`
- `Pre: ↗E (Am → Dm → F → E)`

Notes:
- The center-state is optional. Omit it when the center is obvious or unchanged.
- The chord motion is a left-to-right sequence of chord tokens separated by motion operators (`=`, `⇄`, `→`).

---

## Examples

### Fictional song in A minor using all symbols

Sections:
```
Intro: =Am (Am =)
Verse: ⇄Am (Am ⇄ F)
Verse 2: ⊃Am (Am ⇄ F → Dm)
Pre: ↗E (Am → Dm → F → E)
Chorus: ⇄E (E ⇄ G)
Post: =E (E =)
Bridge: →C (E → F → C)
Break: =C (C =)
Final Chorus: ↗E (C → Am → E ⇄ G)
Outro: =Am (Am =)
```

Tonal roadmap:
```
=Am ⇄Am ⊃Am ↗E ⇄E =E →C =C ↗E =Am
```

### Holy Forever (Bethel Music & Jenn Johnson)

Sections:
```
Intro: =Bb (Bb → C → Am → Dm → C)
Verse: ⊃F (F → Bb → C → Dm → C → Bb → F)
```

Tonal roadmap:
```
=Bb ⊃F
```

### Way Maker (Leeland)

Sections:
```
Intro, Verse, Chorus: ⊃E (A → E → B → C#m)
Build: ⊃E (A → G#m → B → C#m)
```

Tonal roadmap:
```
⊃E
```

### What A Beautiful Name (Hillsong Worship)

Sections:
```
Intro: =D (D =)
Verse: ⊃D (D → G → Bm → A → Bm → C#° → D)
Chorus: ⊃D (D → A → Bm → A → G → F#m → A → Bm → A → G)
Bridge: ⊃G (G → A → Bm → F#m → G → A → Bm → A)
```

Tonal roadmap:
```
=D ⊃D ⊃G
```

### Wings Of Death / Introduction (Jeroen Hippel)

Sections:
```
Intro: =Am (Am =)
Verse: ⇄C (C → B° → Am → C → B°)
Inter: ⇄Am (Am → Dm → C → Am → G → Am)
Chorus: ⇄Am (
    Am → C → B° → Am → G → Am → Em,
    C → Em → Dm → Em → Dm → Em,
    Em → Dm → C → Am → G → Am,
    Am → B° → C → Dm → Am
)
```

Tonal roadmap:
```
=Am ⇄C ⇄Am
```

## Design Goals

- Readable at a glance
- Compact and expressive
- Parsable for software
- Focused on section-level intent

## Non-goals

HFN does not attempt to:
- Replace chord charts or lead sheets
- Encode rhythm or harmonic rhythm
- Provide Roman numeral functional analysis