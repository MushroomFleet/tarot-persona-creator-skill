# TarotPersonaCreator Skill

A Claude Code skill for architecting deeply nuanced, human-like personas using the 78-card tarot deck as a psychological framework.

## What It Does

Replaces flat trait lists ("brave, funny, loyal") with archetypal spectrums that encode contradiction, shadow, and transformation as structural features. Characters designed with this system behave organically under situational pressure rather than through forced authorial decisions.

## Three Modes

- **Create** — Build a persona from scratch. Assigns primary/secondary/court cards, maps polarity spectrum, defines shadow architecture, and establishes the accept/reject/forget arc engine. Outputs a structured Persona Dossier.

- **Assess** — Evaluate an existing character against seven dimensions of persona depth (Archetypal Grounding, Polarity Depth, Shadow Presence, Journey Coherence, Organic Contradiction, Situational Emergence, Arc Engine). Outputs scored assessment with specific enhancement recommendations.

- **Consult** — Advise on story planning and cast design before writing begins. Suggests card assignments, maps natural character tensions, recommends pressure environments that reveal character organically, and identifies gaps in ensemble architecture.

## Activation

Say **"using tarot persona creator"** or **"tarot persona"** followed by your character concept, draft, story plan, or cast outline.

## Installation

Place the `tarot-persona-creator/` directory in your Claude Code skills folder:

```
/path/to/skills/user/tarot-persona-creator/
```

## Core Philosophy

Characters should not be *told* what to do by the author — they should be *architecturally predisposed* to behave in ways that feel inevitable given their internal structure. The tarot system provides that architecture through:

- **Polarity spectrums** — every trait carries its own negation
- **Shadow architecture** — the reversed expression is always present as gravitational pull
- **The Fool's Journey** — psychological development as sequential narrative structure
- **The Trichotomy** — accept, reject, or forget as the engine that drives all character arcs
- **Layered cards** — primary archetype + situational domain + social role + optional internal conflict

## File Structure

```
tarot-persona-creator/
├── SKILL.md                                # Entry point
├── README.md                               # This file
├── references/
│   ├── tarot-deck-complete.md              # Full 78-card reference
│   ├── persona-build-protocol.md           # Create mode procedure
│   ├── assessment-protocol.md              # Assess mode procedure
│   ├── consult-protocol.md                 # Consult mode procedure
│   ├── relationship-dynamics.md            # Inter-character dynamics
│   ├── arc-engine.md                       # Trichotomy arc system
│   ├── output-template-dossier.md          # Create mode output format
│   ├── output-template-assessment.md       # Assess mode output format
│   └── output-template-consult.md          # Consult mode output format
└── assets/
    └── tarot-card-data.json                # Structured card data
```

## Based On

Tarot-Based Persona Layer Grounding system, drawing from Rider-Waite-Smith, Thoth (Crowley), and Marseille (Jodorowsky restoration) tarot traditions.
