---
name: tarot-persona-creator
description: Architect deeply nuanced, human-like personas using the 78-card tarot deck as a psychological framework. Builds characters grounded in archetypal spectrums with built-in contradiction, shadow, and transformation potential rather than flat trait lists. Three modes — Create (build from scratch), Assess (evaluate existing characters), Consult (advise on story/cast planning). Triggers on phrases like "using tarot persona creator", "tarot persona", "build a character using tarot", "assess this character", "persona architecture", or requests for psychologically grounded, non-stereotypical character design. Use when user submits character drafts, story outlines, GDDs, cast lists, or asks for help designing believable, layered characters.
---

# TarotPersonaCreator

Architect psychologically layered personas using the tarot deck as a structural framework — where characters emerge from archetypal spectrums, not trait lists, and behavior surfaces organically from situational pressure rather than forced authorial decisions.

## Activation

Trigger: **"using tarot persona creator"** or **"tarot persona"** with a character concept, draft, story plan, or cast outline.

## Philosophy

Traditional character design asks: "What traits does this character have?"

Tarot persona architecture asks: "What archetypal energy does this character embody, and what is the spectrum of behavior that energy produces under pressure?"

The difference: flat traits produce predictable characters. Archetypal spectrums produce characters who surprise even their creators — because the system encodes contradiction, shadow, and transformation as structural features, not afterthoughts.

**Characters should not be told what to do. They should be architecturally predisposed to behave in ways that feel inevitable.**

## Core System Rules

1. **Polarity Is Inherent** — Every trait carries its own negation. Upright/reversed are not good/bad but two expressions of the same energy.
2. **The Journey Is the Structure** — The Major Arcana describe sequential psychological development (The Fool's Journey). A character's position defines who they are, where they came from, and where they refuse to go.
3. **Cards Layer, They Don't Replace** — Primary card = core archetype. Secondary cards add complexity, internal conflict, domain-specific texture.
4. **Reversal Is Not Failure** — Characters in reversed states are expressing shadow, not broken. Some of the most compelling personas live primarily in reversal.
5. **Suit Defines Domain** — Wands (will/fire), Cups (emotion/water), Swords (intellect/air), Pentacles (material/earth).
6. **Court Cards Define Social Role** — Page (student), Knight (pursuer), Queen (inward master), King (outward master).
7. **Accept, Reject, or Forget** — At every stage, the character accepts the lesson and grows, rejects it and calcifies, or forgets it and repeats. This trichotomy is the arc engine.

## Modes

### Create Mode
Build a persona from scratch.

```
1. RECEIVE character concept, role, or narrative need
2. READ references/persona-build-protocol.md
3. READ assets/tarot-card-data.json for card reference
4. ASSIGN primary Major Arcana card based on core psychological energy
5. DETERMINE polarity (upright/reversed/tending)
6. POSITION on the Fool's Journey (origin/identity/inner-truth/cosmic/integration)
7. ASSIGN secondary Minor Arcana card for situational domain
8. ASSIGN Court Card for social role and maturity
9. OPTIONAL: assign second Major Arcana for internal conflict
10. DEFINE trichotomy response (accept/reject/forget)
11. MAP shadow (reversed meaning as gravitational pull)
12. READ references/relationship-dynamics.md if multiple characters
13. READ references/output-template-dossier.md
14. GENERATE [CharacterName]_PersonaDossier.md
```

### Assess Mode
Evaluate an existing character against the tarot framework.

```
1. RECEIVE character draft, outline, GDD entry, or story description
2. READ references/assessment-protocol.md
3. READ assets/tarot-card-data.json
4. IDENTIFY which Major Arcana the character is already expressing (conscious or not)
5. IDENTIFY current polarity and journey position
6. ASSESS depth across seven dimensions (see Assessment Dimensions below)
7. IDENTIFY where contradictions feel organic vs. forced
8. IDENTIFY missing shadow architecture
9. IDENTIFY arc engine (is there a trichotomy? or is the arc externally imposed?)
10. READ references/output-template-assessment.md
11. GENERATE [CharacterName]_TarotAssessment.md with scores and enhancement suggestions
```

### Consult Mode
Advise on story planning, cast design, and narrative dynamics before writing begins.

```
1. RECEIVE story premise, setting, cast outline, or narrative problem
2. READ references/consult-protocol.md
3. READ references/relationship-dynamics.md
4. READ assets/tarot-card-data.json
5. ANALYZE premise for archetypal needs
6. SUGGEST primary card assignments for key characters
7. IDENTIFY natural tensions between assigned archetypes
8. SUGGEST situational environments that would pressure archetypes organically
9. IDENTIFY where cast has archetypal gaps or redundancies
10. FLAG where plot-driven decisions could be replaced by archetype-emergent behavior
11. READ references/output-template-consult.md
12. GENERATE [ProjectName]_TarotConsult.md
```

## Assessment Dimensions (Assess Mode)

| # | Dimension | Key Question | Score Range |
|---|-----------|-------------|-------------|
| 1 | Archetypal Grounding | Does the character embody a recognizable archetypal energy, or are they a trait collage? | 1-5 |
| 2 | Polarity Depth | Does the character operate on a spectrum, or are they fixed at one pole? | 1-5 |
| 3 | Shadow Presence | Is there a gravitational pull toward the reversed expression? Is the shadow visible? | 1-5 |
| 4 | Journey Coherence | Does the character's arc follow a psychologically coherent path? | 1-5 |
| 5 | Organic Contradiction | Do the character's contradictions feel like two sides of one energy, or like separate traits glued together? | 1-5 |
| 6 | Situational Emergence | Would this character's behavior arise naturally from their archetype under pressure, or does the plot have to force their hand? | 1-5 |
| 7 | Arc Engine | Is there an internal trichotomy (accept/reject/forget) driving the arc, or is the arc externally imposed? | 1-5 |

**Scoring Guide:**
- 5 = The character could be a tarot study. Archetype fully realized with organic spectrum.
- 4 = Strong grounding. Minor gaps in shadow or emergence.
- 3 = Recognizable archetype but flat in places. Some forced decisions.
- 1-2 = Trait collage. No internal engine. Behavior is plot-driven, not character-emergent.

**Overall Persona Depth Score:** Average of all seven dimensions.

## Relationship Dynamics

When multiple characters are designed together, their card assignments create natural dynamics:

**Complementary Pairs** — Cards that complete each other (Emperor/Empress, Sun/Moon, Magician/High Priestess). These create stable partnerships or philosophical mirrors.

**Tension Pairs** — Cards whose energies conflict (Tower/Emperor, Devil/Hierophant, Fool/World). These create organic friction without requiring plot-manufactured conflict.

**Journey Echoes** — Characters at different stages of the same journey (one Fool, one Hermit, one World). These create generational or mentorship dynamics naturally.

**Shadow Mirrors** — One character's upright is another's reversed expression of the same card. These create the deepest antagonist relationships because they are fundamentally the same person who made a different choice.

## Constraints

- **Never flatten** — If a card assignment produces uncomfortable complexity, that's the system working. Don't simplify.
- **Preserve creator vision** — The tarot framework amplifies existing intent. It does not replace the designer's instinct.
- **Archetypes are starting points** — The card provides structure. The character's specific history, culture, voice, and quirks remain the designer's domain.
- **No stereotypes** — The system should produce characters that transcend genre stereotypes, not reinforce them. A Hermit is not always an old man on a mountain.
- **Situational over forced** — Always prefer architectural predisposition over plot-mandated decisions. If the character "needs to" do something for the plot but wouldn't based on their archetype, the plot needs adjusting, not the character.
- **Shadow is not villainy** — Reversed expressions are not evil. They are the other side of the same coin. Most real people live partially in reversal most of the time.

## Quick Reference: The Fool's Journey Phases

| Phase | Cards | Theme | Character State |
|-------|-------|-------|-----------------|
| Origin | 0 | Pure potential | Unformed, open, vulnerable |
| Identity Formation | I–VII | Building the conscious self | Discovering power, belief, choice, will |
| Inner Truth | VIII–XIV | Confronting internal reality | Mastery, fate, consequence, sacrifice, synthesis |
| Cosmic Forces | XV–XIX | Encountering forces larger than self | Shadow, destruction, hope, illusion, illumination |
| Integration | XX–XXI | Reckoning and wholeness | Self-knowledge, completion, or abandonment |

## References

- **Card data:** See [assets/tarot-card-data.json](assets/tarot-card-data.json)
- **Full deck reference:** See [references/tarot-deck-complete.md](references/tarot-deck-complete.md)
- **Build protocol:** See [references/persona-build-protocol.md](references/persona-build-protocol.md)
- **Assessment protocol:** See [references/assessment-protocol.md](references/assessment-protocol.md)
- **Consult protocol:** See [references/consult-protocol.md](references/consult-protocol.md)
- **Relationship dynamics:** See [references/relationship-dynamics.md](references/relationship-dynamics.md)
- **Arc engine:** See [references/arc-engine.md](references/arc-engine.md)
- **Dossier template:** See [references/output-template-dossier.md](references/output-template-dossier.md)
- **Assessment template:** See [references/output-template-assessment.md](references/output-template-assessment.md)
- **Consult template:** See [references/output-template-consult.md](references/output-template-consult.md)

## The Ultimate Test

A persona achieves tarot-grounded depth when:
1. You can name their primary card without being told — the archetype is felt, not labeled
2. Their contradictions feel like one energy expressing two poles, not two traits in a trenchcoat
3. Their worst moments feel like their best qualities inverted, not like a different person
4. Their arc has an internal engine — they are moving toward or away from something psychological, not just reacting to plot events
5. Under new situational pressure, you can predict their behavior from their architecture — and it still surprises you
6. Other characters in the cast create tension or harmony with them based on archetypal dynamics, not plot-manufactured conflict
7. The character feels like they existed before the story started and will continue after it ends
