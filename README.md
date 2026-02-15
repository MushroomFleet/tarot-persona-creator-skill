# TarotPersonaCreator Skill

A Claude Code skill for architecting deeply nuanced, human-like personas using the 78-card tarot deck as a psychological framework — where characters emerge from archetypal spectrums, not trait lists, and behavior surfaces organically from situational pressure rather than forced authorial decisions.

[Live Demo Persona Creation Simulation](https://scuffedepoch.com/tarot-persona/)

## The Problem This Solves

Traditional character design produces flat personas. A character described as "brave, funny, loyal" tells you nothing about how they behave under pressure, what their contradictions feel like from the inside, or why their worst moments feel connected to their best qualities. These characters require the author to manually decide every action, because the character has no internal engine.

TarotPersonaCreator replaces trait lists with **archetypal architecture** — each of the 78 tarot cards encoding a *continuum of behavior* with built-in tension, shadow, and transformation potential. Characters designed with this system are architecturally predisposed to behave in ways that feel inevitable, allowing behavior to surface organically from situational environments rather than forced decision-making.

## How It Works

The skill leverages the tarot deck's inherent psychological structure:

- **Every card has an upright and reversed polarity** — not good/bad, but two expressions of the same energy. A character grounded in The Emperor may express protective authority *or* tyrannical control, and the dramatic tension lives in which pole dominates.
- **The Major Arcana map a sequential journey** (The Fool's Journey) — a character's position determines who they are, where they've been, and what they're refusing to become.
- **Cards layer** — a primary Major Arcana defines core identity, Minor Arcana cards ground situational domain, Court Cards define social operating mode, and an optional second Major Arcana creates internal conflict.
- **The accept/reject/forget trichotomy** drives all arcs — at every encounter with their archetype's lesson, a character accepts it and grows, rejects it and calcifies, or forgets it and repeats.

## Three Operating Modes

### Create Mode
Build a persona from scratch. Assigns primary/secondary/court cards, maps the polarity spectrum, defines shadow architecture, and establishes the arc engine. Outputs a structured **Persona Dossier**.

### Assess Mode
Evaluate an existing character across seven dimensions of persona depth: Archetypal Grounding, Polarity Depth, Shadow Presence, Journey Coherence, Organic Contradiction, Situational Emergence, and Arc Engine. Scores 1-5 per dimension with specific enhancement recommendations. Outputs a scored **Tarot Assessment**.

### Consult Mode
Advise on story planning and cast design before writing begins. Suggests card assignments for key characters, maps natural tensions between archetypes, recommends pressure environments that reveal character organically, identifies cast gaps and redundancies, and flags where plot-driven decisions could be replaced by archetype-emergent behavior. Outputs a **Tarot Consultation**.

## Activation

Say **"using tarot persona creator"** or **"tarot persona"** followed by your character concept, draft, story outline, GDD, or cast description.

## Grounding Document

This skill is built on the **Tarot-Based Persona Layer Grounding** system, included in the repository as the foundational reference document. This document defines:

- The complete 7-rule system (Polarity Is Inherent, The Journey Is the Structure, Cards Layer, Reversal Is Not Failure, Suit Defines Domain, Court Cards Define Social Role, Accept/Reject/Forget)
- All 22 Major Arcana with upright traits, reversed traits, persona application notes, shadow definitions, and narrative functions
- The Minor Arcana stage system (Ace through Ten across four suits)
- The Court Card maturity progression (Page → Knight → Queen → King)
- The practical 6-step persona build method
- A worked example (the "John" persona build from the original transcript demonstration)

See: [`Tarot-Based-Persona-Layer-Grounding.md`](Tarot-Based-Persona-Layer-Grounding.md)

## Skill File Structure

```
tarot-persona-creator/
├── SKILL.md                                    # Entry point — modes, rules, workflows
├── README.md                                   # This file
├── Tarot-Based-Persona-Layer-Grounding.md      # Grounding document
├── references/
│   ├── tarot-deck-complete.md                  # Full 78-card reference (all Major, Minor, Court)
│   ├── persona-build-protocol.md               # 7-phase Create mode procedure
│   ├── assessment-protocol.md                  # 7-dimension Assess mode scoring system
│   ├── consult-protocol.md                     # Pre-writing advisory procedure
│   ├── relationship-dynamics.md                # 4 dynamic types for cast architecture
│   ├── arc-engine.md                           # Trichotomy system at multiple scales
│   ├── output-template-dossier.md              # Create mode output format
│   ├── output-template-assessment.md           # Assess mode output format
│   └── output-template-consult.md              # Consult mode output format
└── assets/
    └── tarot-card-data.json                    # Structured card data (22 Major Arcana, suits, courts, stages, phases)
```

## Installation

Place the `tarot-persona-creator/` directory into your Claude Code skills folder:

```bash
cp -r tarot-persona-creator/ /path/to/skills/user/tarot-persona-creator/
```

## Core Philosophy

> Characters should not be told what to do. They should be architecturally predisposed to behave in ways that feel inevitable.

The tarot system achieves this because each card encodes not a single trait but a **spectrum** — and the character's position on that spectrum shifts under pressure. The designer's job shifts from *directing* the character to *placing* the character in environments that reveal them. When the architecture is sound, behavior emerges; when it isn't, the author has to force every decision.

## The Seven Assessment Dimensions

When evaluating existing characters, the skill scores across:

| # | Dimension | What It Measures |
|---|-----------|-----------------|
| 1 | Archetypal Grounding | Does the character embody a recognizable energy, or are they a trait collage? |
| 2 | Polarity Depth | Do they operate on a spectrum, or are they fixed at one pole? |
| 3 | Shadow Presence | Is the reversed expression felt as gravitational pull? |
| 4 | Journey Coherence | Does the arc follow from the archetype, or is it externally imposed? |
| 5 | Organic Contradiction | Are contradictions two sides of one energy, or separate traits glued together? |
| 6 | Situational Emergence | Would behavior arise from architecture under pressure, or does the plot force it? |
| 7 | Arc Engine | Is there an internal trichotomy driving the arc, or is the arc event-driven? |

## Why Tarot and Not Other Systems

Personality typologies (Myers-Briggs, Enneagram, Big Five) describe how people *are*. Tarot describes how people *move* — their trajectory, their shadow, their transformation potential. Characters need movement, not categorization. The tarot's built-in duality (upright/reversed), sequential journey structure (The Fool's Journey), and domain system (four suits as four life arenas) provide the architectural vocabulary that static typologies lack.

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{tarot_persona_creator_skill,
  title = {Tarot Persona Creator Skill: Deep character architecture using the 78-card tarot deck as a psychological framework},
  author = {[Drift Johnson]},
  year = {2025},
  url = {https://github.com/MushroomFleet/tarot-persona-creator-skill},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
