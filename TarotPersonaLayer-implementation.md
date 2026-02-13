# TarotPersonaCreator Skill — Implementation Guide

## Complete Steps and Code for Building a Tarot-Based Persona Architecture Skill

---

## 1. What This Skill Does

The TarotPersonaCreator skill uses the 78-card tarot deck as a structured psychological framework to architect deeply nuanced, human-like personas. It replaces the typical flat-trait approach to character design — where a character is described as "brave, funny, loyal" — with a layered system where identity emerges organically from archetypal spectrums, built-in contradictions, and situational pressure.

The skill operates in three modes:

**Create Mode** — Builds a full persona from scratch using tarot card assignment, polarity mapping, journey positioning, and shadow architecture. The output is a complete Persona Dossier.

**Assess Mode** — Takes an existing character draft, outline, story plan, or GDD and performs a tarot-grounded analysis. It identifies which archetypes the character is already expressing, where they lack depth, where their contradictions feel forced rather than organic, and where their arc has no structural engine. The output is a scored assessment with specific enhancement recommendations.

**Consult Mode** — Operates as an advisor during planning or pre-writing. Given a story premise, setting, or cast outline, the skill suggests tarot-grounded persona configurations that would create organic tension, meaningful relationships, and situationally emergent behavior rather than plot-forced decisions.

The fundamental philosophy: characters should not be *told* what to do by the author — they should be *architecturally predisposed* to behave in ways that feel inevitable given their internal structure. The tarot system provides that architecture.

---

## 2. Skill Directory Structure

```
tarot-persona-creator/
├── SKILL.md                                    # Main skill file (entry point)
├── references/
│   ├── tarot-deck-complete.md                  # Full 78-card reference data
│   ├── persona-build-protocol.md               # Step-by-step build procedure
│   ├── assessment-protocol.md                  # How to assess existing characters
│   ├── consult-protocol.md                     # Advisory mode procedures
│   ├── relationship-dynamics.md                # Inter-persona card interactions
│   ├── arc-engine.md                           # How trichotomy drives narrative arcs
│   ├── output-template-dossier.md              # Template for Create mode output
│   ├── output-template-assessment.md           # Template for Assess mode output
│   └── output-template-consult.md              # Template for Consult mode output
└── assets/
    └── tarot-card-data.json                    # Structured card data for programmatic use
```

---

## 3. Implementation — Step by Step

### Step 1: Create the Structured Card Data

This JSON file is the backbone. Every card encoded with upright traits, reversed traits, element associations, journey position, and persona application notes. This allows the skill to reference card data programmatically rather than relying on freeform interpretation every time.

**File: `assets/tarot-card-data.json`**

```json
{
  "meta": {
    "version": "1.0",
    "total_cards": 78,
    "major_arcana_count": 22,
    "minor_arcana_count": 56,
    "system": "Tarot-Based Persona Layer Grounding"
  },
  "suits": {
    "wands": {
      "element": "fire",
      "domain": "will_and_ambition",
      "governs": ["creativity", "drive", "passion", "ego", "enterprise"]
    },
    "cups": {
      "element": "water",
      "domain": "emotion_and_relationship",
      "governs": ["love", "intuition", "inner_life", "empathy", "fantasy"]
    },
    "swords": {
      "element": "air",
      "domain": "intellect_and_conflict",
      "governs": ["thought", "communication", "truth", "cruelty", "analysis"]
    },
    "pentacles": {
      "element": "earth",
      "domain": "material_and_body",
      "governs": ["work", "health", "wealth", "craft", "physicality", "legacy"]
    }
  },
  "court_ranks": {
    "page": {
      "role": "student_messenger",
      "expression": ["curiosity", "inexperience", "potential", "naivety"],
      "maturity": "emerging"
    },
    "knight": {
      "role": "pursuer_zealot",
      "expression": ["action", "obsession", "momentum", "recklessness"],
      "maturity": "active"
    },
    "queen": {
      "role": "nurturer_inward_master",
      "expression": ["mastery_inward", "emotional_authority", "receptivity"],
      "maturity": "receptive_mastery"
    },
    "king": {
      "role": "commander_outward_master",
      "expression": ["mastery_outward", "control", "institutional_power"],
      "maturity": "directive_mastery"
    }
  },
  "major_arcana": [
    {
      "number": 0,
      "name": "The Fool",
      "core_archetype": "The Unformed Spirit / The Vagabond / Everyman",
      "journey_phase": "origin",
      "journey_stage": "pre-identity",
      "upright": {
        "traits": ["innocence", "spontaneity", "free_spirit", "new_beginnings", "faith_in_unknown", "openness", "beginners_mind", "truth_through_naivety"],
        "energy": "pure_potential"
      },
      "reversed": {
        "traits": ["folly", "mania", "extravagance", "delirium", "frenzy", "negligence", "apathy", "unimportance", "vanity", "betrayal_through_exposure"],
        "energy": "chaotic_destruction"
      },
      "persona_roles": ["wanderer", "everyman", "holy_innocent", "chaotic_catalyst", "truth_teller_as_jester"],
      "shadow": "Destroys without understanding what has been broken",
      "narrative_function": "Enters systems and disrupts them by being unbound by rules"
    },
    {
      "number": 1,
      "name": "The Magician",
      "core_archetype": "The Conscious Will / The Channeler",
      "journey_phase": "identity_formation",
      "journey_stage": "differentiation",
      "upright": {
        "traits": ["willpower", "resourcefulness", "skill", "concentration", "manifestation", "dexterity", "self_confidence", "mastery_of_craft"],
        "energy": "directed_potential"
      },
      "reversed": {
        "traits": ["manipulation", "trickery", "poor_planning", "latent_talents_unused", "deception", "illusion_as_substance", "con_artistry"],
        "energy": "misdirected_skill"
      },
      "persona_roles": ["craftsman", "inventor", "con_artist", "prodigy", "showman"],
      "shadow": "Skill serves only ego; substance replaced by performance",
      "narrative_function": "Shapes reality through competence or cunning"
    },
    {
      "number": 2,
      "name": "The High Priestess",
      "core_archetype": "The Unconscious / The Keeper of Hidden Knowledge",
      "journey_phase": "identity_formation",
      "journey_stage": "inner_awareness",
      "upright": {
        "traits": ["intuition", "mystery", "inner_knowledge", "subconscious_mind", "spiritual_insight", "patience", "stillness", "sacred_feminine_wisdom"],
        "energy": "hidden_knowing"
      },
      "reversed": {
        "traits": ["destructive_secrets", "withdrawal", "repression", "hidden_agendas", "knowledge_hoarding", "intuition_severed", "superficiality"],
        "energy": "guarded_silence"
      },
      "persona_roles": ["oracle", "silent_guide", "enigmatic_mentor", "institutional_memory_keeper", "gatekeeper"],
      "shadow": "Hoards knowledge for power; severed from own inner life",
      "narrative_function": "Knows more than they reveal"
    },
    {
      "number": 3,
      "name": "The Empress",
      "core_archetype": "The Generative Force / The Mother",
      "journey_phase": "identity_formation",
      "journey_stage": "abundance",
      "upright": {
        "traits": ["abundance", "nurturing", "fertility", "beauty", "nature", "comfort", "sensuality", "creative_output", "maternal_care", "groundedness"],
        "energy": "generative_force"
      },
      "reversed": {
        "traits": ["creative_block", "dependence", "smothering", "neglect", "vanity", "overindulgence", "inability_to_release", "barrenness"],
        "energy": "consumptive_care"
      },
      "persona_roles": ["creator", "provider", "mother_figure", "artist", "earth_spirit"],
      "shadow": "Suffocates under guise of nurturing; consumes what it claims to sustain",
      "narrative_function": "Power is generative — creates, sustains, provides"
    },
    {
      "number": 4,
      "name": "The Emperor",
      "core_archetype": "The Structural Authority / The Father",
      "journey_phase": "identity_formation",
      "journey_stage": "external_order",
      "upright": {
        "traits": ["authority", "structure", "stability", "leadership", "discipline", "protection", "strategic_thinking", "fatherly_guidance", "institutional_power"],
        "energy": "imposed_order"
      },
      "reversed": {
        "traits": ["tyranny", "rigidity", "domination", "excessive_control", "stubbornness", "authoritarianism", "emotional_unavailability", "power_abuse"],
        "energy": "crushing_order"
      },
      "persona_roles": ["ruler", "patriarch", "military_commander", "institutional_leader", "bureaucrat"],
      "shadow": "Mistakes the rule for the reason; control becomes its own purpose",
      "narrative_function": "Builds and enforces order"
    },
    {
      "number": 5,
      "name": "The Hierophant",
      "core_archetype": "The Tradition Bearer / The Teacher",
      "journey_phase": "identity_formation",
      "journey_stage": "belief_systems",
      "upright": {
        "traits": ["tradition", "conformity", "education", "spiritual_wisdom", "mentorship", "morality", "religious_structure", "shared_belief", "guidance"],
        "energy": "transmitted_wisdom"
      },
      "reversed": {
        "traits": ["dogmatism", "cult_mentality", "blind_obedience", "hypocrisy", "subversion_of_tradition", "spiritual_bypassing", "restrictive_institutions", "indoctrination"],
        "energy": "corrupted_doctrine"
      },
      "persona_roles": ["priest", "teacher", "ideologue", "cultural_custodian", "rebel_by_opposition"],
      "shadow": "Demands obedience over understanding; defined entirely by what they oppose",
      "narrative_function": "Represents systems of belief"
    },
    {
      "number": 6,
      "name": "The Lovers",
      "core_archetype": "The Choice / The Union",
      "journey_phase": "identity_formation",
      "journey_stage": "moral_choice",
      "upright": {
        "traits": ["love", "harmony", "partnership", "values_alignment", "choice", "union", "attraction", "deep_connection", "moral_crossroads"],
        "energy": "conscious_union"
      },
      "reversed": {
        "traits": ["disharmony", "imbalance", "misalignment", "bad_choices", "broken_trust", "temptation", "infidelity", "self_sabotage", "commitment_avoidance"],
        "energy": "fractured_choice"
      },
      "persona_roles": ["lover", "partner", "the_torn", "the_committed", "the_betrayer"],
      "shadow": "Trapped by a wrong choice; unable to commit to any path",
      "narrative_function": "Defined by a central relationship or pivotal choice"
    },
    {
      "number": 7,
      "name": "The Chariot",
      "core_archetype": "The Directed Will / The Conqueror",
      "journey_phase": "identity_formation",
      "journey_stage": "triumph",
      "upright": {
        "traits": ["determination", "willpower", "victory", "control", "assertion", "ambition", "confidence", "overcoming_obstacles"],
        "energy": "force_of_will"
      },
      "reversed": {
        "traits": ["aggression", "directionlessness", "loss_of_control", "scattered_energy", "recklessness", "defeat_through_overextension"],
        "energy": "uncontrolled_momentum"
      },
      "persona_roles": ["warrior", "competitor", "achiever", "conqueror", "the_driven"],
      "shadow": "Cannot stop moving; has forgotten what they are fighting for",
      "narrative_function": "Advances through sheer will"
    },
    {
      "number": 8,
      "name": "Strength",
      "core_archetype": "The Gentle Power / The Inner Mastery",
      "journey_phase": "inner_truth",
      "journey_stage": "self_mastery",
      "upright": {
        "traits": ["inner_strength", "courage", "patience", "compassion", "self_control", "gentle_persuasion", "endurance", "quiet_confidence", "impulse_mastery"],
        "energy": "contained_power"
      },
      "reversed": {
        "traits": ["self_doubt", "weakness", "insecurity", "raw_uncontrolled_emotion", "cowardice", "cruelty_from_fear", "lost_nerve", "inner_conflict"],
        "energy": "consumed_by_beast"
      },
      "persona_roles": ["quiet_leader", "de_escalator", "endurer", "gentle_giant", "the_patient"],
      "shadow": "Consumed by the beast within; mistakes passivity for patience",
      "narrative_function": "Strength is invisible — quiet voice, the one who endures"
    },
    {
      "number": 9,
      "name": "The Hermit",
      "core_archetype": "The Seeker in Solitude / The Lamp Bearer",
      "journey_phase": "inner_truth",
      "journey_stage": "withdrawal",
      "upright": {
        "traits": ["introspection", "solitude", "inner_guidance", "wisdom", "contemplation", "soul_searching", "distant_mentorship", "spiritual_quest"],
        "energy": "illuminated_solitude"
      },
      "reversed": {
        "traits": ["isolation", "loneliness", "withdrawal", "paranoia", "misanthropy", "excessive_introspection", "connection_refusal", "bitter_wisdom"],
        "energy": "calcified_isolation"
      },
      "persona_roles": ["monk", "exile", "detective", "scholar", "recluse", "lighthouse_keeper"],
      "shadow": "Forgotten why they withdrew; mistakes loneliness for enlightenment",
      "narrative_function": "Retreats to seek truth"
    },
    {
      "number": 10,
      "name": "Wheel of Fortune",
      "core_archetype": "The Cycle / Fate in Motion",
      "journey_phase": "inner_truth",
      "journey_stage": "fate",
      "upright": {
        "traits": ["change", "cycles", "destiny", "turning_points", "luck", "karma", "inevitability", "pattern_recognition"],
        "energy": "turning_wheel"
      },
      "reversed": {
        "traits": ["bad_luck", "resistance_to_change", "broken_cycles", "stagnation", "fate_entrapment", "karmic_debt", "refusal_to_learn"],
        "energy": "stuck_wheel"
      },
      "persona_roles": ["gambler", "fatalist", "cycle_repeater", "agent_of_change", "harbinger"],
      "shadow": "Caught in cycles — keeps returning to the same mistake",
      "narrative_function": "Caught in or embodying cycles of change"
    },
    {
      "number": 11,
      "name": "Justice",
      "core_archetype": "The Consequence / The Measure",
      "journey_phase": "inner_truth",
      "journey_stage": "accountability",
      "upright": {
        "traits": ["fairness", "truth", "accountability", "law", "cause_and_effect", "clarity", "objectivity", "ethical_action", "karmic_balance"],
        "energy": "precise_measure"
      },
      "reversed": {
        "traits": ["injustice", "dishonesty", "unaccountability", "bias", "law_corruption", "harsh_judgment", "consequence_avoidance", "legal_entanglement"],
        "energy": "broken_scales"
      },
      "persona_roles": ["judge", "investigator", "arbiter", "vigilante", "the_accountable"],
      "shadow": "Justice becomes vengeance; fleeing own accountability",
      "narrative_function": "Embodies or enforces consequence"
    },
    {
      "number": 12,
      "name": "The Hanged Man",
      "core_archetype": "The Suspended One / The Voluntary Sacrifice",
      "journey_phase": "inner_truth",
      "journey_stage": "surrender",
      "upright": {
        "traits": ["surrender", "new_perspective", "sacrifice", "letting_go", "suspension", "acceptance_patience", "chosen_martyrdom", "insight_through_discomfort"],
        "energy": "inverted_wisdom"
      },
      "reversed": {
        "traits": ["stalling", "sacrifice_resistance", "unnecessary_martyrdom", "stagnation_as_patience", "victim_mentality", "inability_to_act", "self_pity"],
        "energy": "performative_suffering"
      },
      "persona_roles": ["prisoner_who_finds_freedom", "deliberate_sacrifice", "the_suspended", "the_waiting"],
      "shadow": "Mistakes inaction for wisdom; addicted to suffering",
      "narrative_function": "Gains power through surrender"
    },
    {
      "number": 13,
      "name": "Death",
      "core_archetype": "The Transformation / The Ending That Permits Beginning",
      "journey_phase": "inner_truth",
      "journey_stage": "transformation",
      "upright": {
        "traits": ["transformation", "endings", "transition", "release_of_old", "metamorphosis", "release", "ground_clearing"],
        "energy": "total_change"
      },
      "reversed": {
        "traits": ["change_resistance", "fear_of_endings", "stagnation", "decay_without_renewal", "clinging_to_dead", "inability_to_grieve", "prolonged_suffering"],
        "energy": "refused_death"
      },
      "persona_roles": ["transformer", "agent_of_change", "the_reborn", "the_one_who_forces_endings"],
      "shadow": "Refuses to let something die; drags a corpse of identity",
      "narrative_function": "At the threshold of total transformation — or forces it in others"
    },
    {
      "number": 14,
      "name": "Temperance",
      "core_archetype": "The Alchemist / The Middle Way",
      "journey_phase": "inner_truth",
      "journey_stage": "synthesis",
      "upright": {
        "traits": ["balance", "patience", "moderation", "purpose", "synthesis", "healing", "adaptation", "holding_contradictions", "self_alchemy"],
        "energy": "precise_mixture"
      },
      "reversed": {
        "traits": ["imbalance", "excess", "no_long_term_vision", "impatience", "discord", "forcing_incompatibles", "overcompensation", "burnout"],
        "energy": "lost_center"
      },
      "persona_roles": ["diplomat", "alchemist", "therapist", "bridge_builder", "mediator"],
      "shadow": "Lost center; healer who cannot heal themselves",
      "narrative_function": "Mediates, heals, or synthesizes"
    },
    {
      "number": 15,
      "name": "The Devil",
      "core_archetype": "The Bondage / The Shadow Self",
      "journey_phase": "cosmic_forces",
      "journey_stage": "confrontation_with_shadow",
      "upright": {
        "traits": ["bondage", "addiction", "materialism", "shadow_self", "raw_desire", "sexuality", "earthly_pleasure", "darkness_confrontation", "honest_appetite"],
        "energy": "binding_desire"
      },
      "reversed": {
        "traits": ["bondage_release", "addiction_overcome", "power_reclaimed", "detachment", "deeper_denial", "hidden_addictions", "shadow_refusal"],
        "energy": "chains_removed_or_buried"
      },
      "persona_roles": ["addict", "power_hungry", "toxic_bond_prisoner", "shadow_befriender", "the_chained"],
      "shadow": "Darkness buried so deep it controls invisibly",
      "narrative_function": "Defined by their chains — or by having broken them"
    },
    {
      "number": 16,
      "name": "The Tower",
      "core_archetype": "The Catastrophe / The Necessary Destruction",
      "journey_phase": "cosmic_forces",
      "journey_stage": "destruction",
      "upright": {
        "traits": ["sudden_upheaval", "revelation", "false_structure_destruction", "crisis", "liberation_through_disaster", "undeniable_truth", "rock_bottom_as_foundation"],
        "energy": "lightning_strike"
      },
      "reversed": {
        "traits": ["change_fear", "disaster_averted_temporarily", "inevitable_collapse_prolonged", "suppressed_upheaval", "ruin_narrowly_avoided", "rebuilding_on_flawed_foundation"],
        "energy": "patched_ruin"
      },
      "persona_roles": ["whistleblower", "fallen_king", "the_shattered", "catastrophe_agent"],
      "shadow": "Keeps patching a doomed structure; terrified of what happens when it falls",
      "narrative_function": "Experiences or causes catastrophic revelation"
    },
    {
      "number": 17,
      "name": "The Star",
      "core_archetype": "The Hope / The Renewal After Destruction",
      "journey_phase": "cosmic_forces",
      "journey_stage": "hope",
      "upright": {
        "traits": ["hope", "faith", "renewal", "serenity", "inspiration", "spiritual_connection", "vulnerability_as_strength", "healing", "creative_flow", "purpose_rediscovered"],
        "energy": "gentle_light"
      },
      "reversed": {
        "traits": ["despair", "disconnection", "faithlessness", "creative_drought", "feeling_lost", "hopelessness", "meaning_absent", "spiritual_emptiness"],
        "energy": "extinguished_light"
      },
      "persona_roles": ["survivor", "artist", "rebuilder_from_nothing", "beacon", "the_vulnerable"],
      "shadow": "Lost hope entirely; the light that went out",
      "narrative_function": "Represents hope after devastation"
    },
    {
      "number": 18,
      "name": "The Moon",
      "core_archetype": "The Illusion / The Deep Unconscious",
      "journey_phase": "cosmic_forces",
      "journey_stage": "illusion",
      "upright": {
        "traits": ["illusion", "fear", "anxiety", "subconscious", "intuition", "dreams", "deception", "the_unknown", "psychic_depth", "liminal_space"],
        "energy": "reflected_light"
      },
      "reversed": {
        "traits": ["fear_release", "clarity_emerging", "repressed_emotions_surfacing", "confusion_lifting", "deeper_delusion", "paranoia", "psychic_overwhelm", "madness"],
        "energy": "veil_lifting_or_thickening"
      },
      "persona_roles": ["unreliable_narrator", "dreamer", "reality_questioner", "the_haunted", "liminal_dweller"],
      "shadow": "Final descent into delusion; cannot distinguish fear from reality",
      "narrative_function": "Inhabits ambiguity — nothing is what it appears"
    },
    {
      "number": 19,
      "name": "The Sun",
      "core_archetype": "The Illumination / The Achieved Joy",
      "journey_phase": "cosmic_forces",
      "journey_stage": "illumination",
      "upright": {
        "traits": ["joy", "success", "vitality", "clarity", "confidence", "truth_revealed", "warmth", "celebration", "innocence_restored", "creative_fulfillment"],
        "energy": "total_clarity"
      },
      "reversed": {
        "traits": ["temporary_setbacks", "diminished_joy", "overexposure", "burnout", "false_positivity", "darkness_avoidance", "naive_wisdom"],
        "energy": "blinding_light"
      },
      "persona_roles": ["golden_child", "peak_hero", "truth_teller", "the_radiant", "the_celebrated"],
      "shadow": "Performs happiness; blinded by own brightness",
      "narrative_function": "Radiates — clarity, joy, truth without shadow"
    },
    {
      "number": 20,
      "name": "Judgement",
      "core_archetype": "The Reckoning / The Calling",
      "journey_phase": "integration",
      "journey_stage": "reckoning",
      "upright": {
        "traits": ["judgement", "rebirth", "inner_calling", "absolution", "reckoning", "self_evaluation", "higher_purpose", "culmination", "total_clarity"],
        "energy": "trumpet_call"
      },
      "reversed": {
        "traits": ["self_doubt", "calling_refused", "past_unlearned", "harsh_self_judgement", "reckoning_avoidance", "unprocessed_guilt", "threshold_stagnation"],
        "energy": "unanswered_call"
      },
      "persona_roles": ["the_reckoner", "the_called", "the_self_examiner", "the_haunted_by_past"],
      "shadow": "Refuses the call; haunted by a reckoning they will not face",
      "narrative_function": "Faces their own totality — everything they have done"
    },
    {
      "number": 21,
      "name": "The World",
      "core_archetype": "The Completion / The Integration",
      "journey_phase": "integration",
      "journey_stage": "wholeness",
      "upright": {
        "traits": ["completion", "integration", "accomplishment", "wholeness", "travel", "fulfillment", "unity", "cycle_end", "earned_mastery"],
        "energy": "full_circle"
      },
      "reversed": {
        "traits": ["incompletion", "closure_lacking", "shortcuts_with_gaps", "near_finish_stagnation", "ending_fear", "lesson_unintegrated", "abandoned_journey"],
        "energy": "almost_there"
      },
      "persona_roles": ["the_complete", "the_integrated", "the_almost_there", "the_cycle_closer"],
      "shadow": "Forever almost-there; cycle refuses to close",
      "narrative_function": "Has come full circle — or represents completeness itself"
    }
  ],
  "minor_arcana_stages": {
    "ace": { "stage": "seed", "meaning": "Pure potential. The spark. The offer." },
    "two": { "stage": "duality", "meaning": "Choice, partnership, or tension." },
    "three": { "stage": "growth", "meaning": "First expression, expansion, collaboration." },
    "four": { "stage": "structure", "meaning": "Stability, foundation, rest — or stagnation." },
    "five": { "stage": "conflict", "meaning": "Loss, struggle, disruption. The necessary crisis." },
    "six": { "stage": "harmony", "meaning": "Resolution, generosity, balance restored." },
    "seven": { "stage": "reflection", "meaning": "Assessment, strategy, deception or vision." },
    "eight": { "stage": "mastery_movement", "meaning": "Skill applied, rapid change, discipline, or entrapment." },
    "nine": { "stage": "culmination", "meaning": "Near-completion, abundance or anxiety, the final test." },
    "ten": { "stage": "completion", "meaning": "Full expression of the suit's energy, for better or worse." }
  },
  "journey_phases": {
    "origin": { "cards": [0], "theme": "Pure potential, the unformed self" },
    "identity_formation": { "cards": [1,2,3,4,5,6,7], "theme": "Building the conscious self, forming relationships with power, belief, and choice" },
    "inner_truth": { "cards": [8,9,10,11,12,13,14], "theme": "Confronting internal reality — mastery, fate, consequence, sacrifice, transformation, synthesis" },
    "cosmic_forces": { "cards": [15,16,17,18,19], "theme": "Encountering forces larger than the self — shadow, destruction, hope, illusion, illumination" },
    "integration": { "cards": [20,21], "theme": "Reckoning and wholeness — the journey resolved or abandoned" }
  },
  "trichotomy": {
    "accept": "Character integrates the lesson and grows. Arc progresses forward.",
    "reject": "Character refuses the lesson and calcifies. Arc hardens into rigidity or denial.",
    "forget": "Character encounters the lesson but lets it pass. Arc loops — doomed to repeat."
  }
}
```

---

### Step 2: Create the SKILL.md Entry Point

**File: `SKILL.md`**

```markdown
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
```

---

### Step 3: Create the Persona Build Protocol

**File: `references/persona-build-protocol.md`**

```markdown
# Persona Build Protocol

Step-by-step procedure for constructing a tarot-grounded persona from scratch.

---

## Phase 1: Identify Core Energy

Before assigning any card, ask these diagnostic questions about the character concept:

**Energy Questions:**
- What is the fundamental psychological force this character embodies?
- When they walk into a room, what changes?
- What do they want that they cannot name?
- What are they afraid of becoming?

**Functional Questions:**
- What narrative role does this character serve?
- What do they do to the characters around them?
- What would be lost from the story if they were removed?

Map the answers against the Major Arcana. The card that resonates most strongly — not the most flattering one — is the primary assignment.

**Common Mapping Errors to Avoid:**
- Assigning The Magician to every competent character (consider: is their competence the *point*, or just a trait?)
- Assigning The Hermit to every introverted character (consider: are they seeking truth in solitude, or just socially reluctant?)
- Assigning The Devil only to villains (consider: The Devil is about chains, not evil — many protagonists are chained)
- Defaulting to upright readings because reversed "sounds negative" (consider: reversal is not failure)

---

## Phase 2: Determine Polarity State

The character's current polarity is where they exist on their card's spectrum right now. This is not permanent — polarity can shift across an arc.

**Polarity States:**
- **Upright** — Expressing the aspirational/functional pole of the archetype
- **Reversed** — Expressing the shadow/corrupted pole of the archetype
- **Tending Upright** — Primarily upright but with visible shadow pressure
- **Tending Reversed** — Primarily reversed but with moments of upright expression breaking through
- **Oscillating** — Unstable between poles. The character's central tension is which pole will win.

The most dynamic characters tend toward "tending" or "oscillating" states. Fully upright characters risk being flat. Fully reversed characters risk being one-note antagonists.

---

## Phase 3: Journey Position

Place the character on the Fool's Journey. This determines not just their current state but their psychological history and their available futures.

**Position determines:**
- **Where they've been** — What lessons are behind them (accepted, rejected, or forgotten)
- **Where they are** — What archetypal challenge they currently face
- **Where they're headed** — What comes next on the path (if they continue)
- **What they're refusing** — The next card on the journey that they will not face

A character positioned at Card VIII (Strength) has already navigated identity formation (I–VII). They have opinions about power (Emperor), belief (Hierophant), and choice (Lovers). Their current challenge is inner mastery — but their refusal might be withdrawal (Hermit) or acceptance of fate (Wheel of Fortune).

---

## Phase 4: Secondary Card Assignment

**Minor Arcana Card** — Grounds the character in a specific life domain and developmental stage.

Select based on:
- Which suit governs their primary arena of action? (Wands/Cups/Swords/Pentacles)
- Which numbered stage describes their current situation within that domain? (Ace through Ten)

Example: A character whose primary card is The Emperor (structural authority) but who is living through a Five of Pentacles (material loss, exclusion) has a profound tension: they are architecturally an authority figure but situationally dispossessed. This produces a deposed king, a leader in exile, a father who has lost custody — organically, without the designer having to force those specifics.

**Court Card** — Defines how they operate socially within their domain.

- Page: They are learning, receiving, carrying messages
- Knight: They are pursuing with obsessive momentum
- Queen: They have internalized mastery — their power is receptive and inward
- King: They project mastery outward — their power is institutional and commanding

**Optional Second Major Arcana** — Creates internal conflict.

Use sparingly. This is for characters whose outer self and inner self are governed by different archetypes.

Example: Outwardly The Emperor (authority, structure) / Inwardly The Hanged Man (surrender, suspension). This character maintains an exterior of control while internally having given up — or having achieved a perspective that makes control feel meaningless. This contradiction is not arbitrary; both cards are on the same journey, just at different stages.

---

## Phase 5: The Trichotomy

For the lesson their primary archetype offers, determine: **accept**, **reject**, or **forget**.

This single decision is the character's arc engine.

**Accept:** The character integrates the lesson. This doesn't mean they become "better" — accepting The Devil's lesson might mean acknowledging and living with their chains rather than pretending they don't exist. Arc moves forward.

**Reject:** The character refuses the lesson. They harden. An Emperor who rejects the lesson of authority doesn't become weak — they become tyrannical, doubling down on control as a substitute for the growth they refused. Arc calcifies.

**Forget:** The character encounters the lesson, glimpses understanding, and lets it slip away. A Fool who forgets keeps repeating the journey's beginning, never progressing. This is the most tragic response — not active refusal but passive loss. Arc loops.

The trichotomy can be applied at multiple levels:
- **Story-level:** The character's overall arc across the entire narrative
- **Scene-level:** Within individual encounters that echo their archetype
- **Relationship-level:** How they respond to another character who embodies a complementary or opposing archetype

---

## Phase 6: Shadow Mapping

Every primary card's reversed meaning is the character's shadow — the thing they might become. The shadow is not a separate entity; it is the same energy turned inward, corrupted, or denied.

**Shadow mapping requires defining:**

1. **The Shadow State** — What does the reversed expression look like for this specific character? (Not generic reversed meaning, but how *this person* would express it given their history, culture, and context.)

2. **The Shadow Trigger** — What situational pressure would push them from upright toward reversed? This is the thing that would break them.

3. **The Shadow Visibility** — How much of the shadow is already visible in the character's current behavior? Even upright characters should show traces. The shadow should be felt as a gravitational pull.

4. **The Shadow Relationship** — Is the character aware of their shadow? Do they fight it, deny it, flirt with it, or have they never noticed it?

---

## Phase 7: Compile the Persona Dossier

Assemble all elements into a structured document. See output-template-dossier.md for the complete template.

The dossier should be usable by:
- A writer who needs to know how this character would behave in any given scene
- A game designer who needs dialogue trees that feel organic
- A narrative designer who needs to understand how this character interacts with others in the cast
- Anyone who picks up the dossier and can *feel* the character without needing to read a biography
```

---

### Step 4: Create the Assessment Protocol

**File: `references/assessment-protocol.md`**

```markdown
# Assessment Protocol

How to evaluate an existing character against the tarot persona framework.

---

## Procedure

### 1. Read the Character

Absorb the character as presented — their description, their actions, their dialogue, their role. Do not assign cards yet. First, *feel* the character.

### 2. Identify Emergent Archetype

Ask: Which Major Arcana card does this character already resemble, whether the creator intended it or not?

Most characters with any depth will map to one or two Major Arcana naturally. The question is whether that mapping is conscious and developed, or accidental and shallow.

If the character maps to no Major Arcana at all, they are likely a trait collage — a bundle of characteristics without an underlying archetypal engine.

### 3. Score the Seven Dimensions

For each dimension, score 1-5 and provide specific evidence.

**Dimension 1: Archetypal Grounding (1-5)**
- Does the character feel like they embody a fundamental psychological energy?
- Or are they assembled from a list of traits without a unifying current?
- 5 = unmistakable archetype; 1 = no discernible core

**Dimension 2: Polarity Depth (1-5)**
- Does the character exist on a spectrum between upright and reversed?
- Or are they locked at one pole?
- 5 = rich spectrum visible; 1 = completely static

**Dimension 3: Shadow Presence (1-5)**
- Is the character's shadow — the reversed expression of their energy — visible or implied?
- Is there gravitational pull toward their darker pole?
- 5 = shadow felt in every scene; 1 = no shadow architecture

**Dimension 4: Journey Coherence (1-5)**
- Does the character's arc follow a psychologically coherent path?
- Does their growth (or stagnation) make sense given their archetypal position?
- 5 = arc and archetype are unified; 1 = arc is disconnected from character identity

**Dimension 5: Organic Contradiction (1-5)**
- Do the character's contradictions feel like two sides of the same coin?
- Or do they feel like separate traits bolted together?
- 5 = contradictions are the same energy in dual expression; 1 = contradictions are random or absent

**Dimension 6: Situational Emergence (1-5)**
- Would this character's key decisions arise naturally from their archetype under pressure?
- Or does the plot have to force their hand?
- 5 = behavior emerges from architecture; 1 = behavior is plot-mandated

**Dimension 7: Arc Engine (1-5)**
- Is there an internal engine (accept/reject/forget) driving the character's arc?
- Or is the arc externally imposed by events?
- 5 = internal trichotomy clearly operating; 1 = no internal engine, pure reaction

### 4. Identify Enhancements

For any dimension scoring below 3, provide specific tarot-grounded enhancement suggestions:
- What card assignment would strengthen the archetype?
- What reversed traits would add shadow depth?
- What situational pressures would test the character's polarity?
- What trichotomy response would create an internal arc engine?

### 5. Flag Forced Decisions

Identify moments in the character's story where they do something because the plot requires it rather than because their archetype demands it. For each, suggest how the same outcome could emerge organically from the character's tarot architecture.

### 6. Suggest Cast Dynamics

If the character exists within an ensemble, assess how their archetype interacts with others. Identify complementary pairs, tension pairs, journey echoes, and shadow mirrors. Note where cast dynamics are rich and where they are coincidental rather than architectural.
```

---

### Step 5: Create the Consult Protocol

**File: `references/consult-protocol.md`**

```markdown
# Consult Protocol

Advisory procedure for story planning and cast design before writing begins.

---

## When to Use Consult Mode

- A writer has a premise but hasn't designed their characters yet
- A game designer has a world but needs a cast that will create organic dynamics
- A narrative designer has a plot outline and needs personas that serve it without feeling forced
- A team is building an ensemble and wants to ensure archetypal coverage and tension
- A creator has a "stuck" story and suspects the problem is character architecture, not plot

## Procedure

### 1. Absorb the Premise

Understand the story's world, tone, themes, and central conflicts before suggesting any character architecture. The tarot framework serves the story — not the other way around.

### 2. Identify Archetypal Needs

Every story has archetypal roles that need filling — not character types, but energetic functions:
- Who provides forward momentum? (Chariot, Knight-rank)
- Who provides wisdom or resistance? (Hermit, High Priestess, Hierophant)
- Who embodies the central transformation? (Death, Tower, Wheel of Fortune)
- Who creates the primary tension? (Devil, opposing polarity characters)
- Who provides grounding? (Empress, Emperor, Pentacles-suit characters)
- Who catalyzes change? (Fool, Tower, Star)

### 3. Suggest Card Assignments

For each needed role, suggest a primary Major Arcana card with justification tied to the story's specific needs. Provide polarity recommendations and journey positioning.

### 4. Map Natural Tensions

Once cards are assigned, identify where natural archetypal tensions exist between characters. These tensions do not need to be manufactured by the plot — they exist because of what the characters *are*.

Present tensions as dynamics, not conflicts:
- "These two characters will naturally disagree about [theme] because one embodies [card energy] and the other embodies [opposing energy]"
- "This relationship will create [dynamic] because their cards are [complementary/tension/echo/shadow mirror]"

### 5. Suggest Pressure Environments

Recommend settings, situations, or events that would naturally pressure the assigned archetypes. The goal is to find environments where characters reveal themselves through reaction rather than exposition.

A Hermit placed in a crowd. An Emperor stripped of title. A Fool given responsibility. A Tower character in a perfectly stable institution. These environments force the archetype to express — upright or reversed — without the author needing to dictate behavior.

### 6. Identify Gaps and Redundancies

- **Gaps:** Archetypal energies the story needs but the cast doesn't provide. A story about institutional corruption needs someone embodying the Hierophant (even in reversal) — without it, there's nothing specific being corrupted.
- **Redundancies:** Multiple characters occupying the same archetypal space. Unless deliberately designed as shadow mirrors or journey echoes, redundancy flattens the cast.

### 7. Flag Plot-Architecture Conflicts

Identify places where the plot outline requires characters to do things their archetypes wouldn't produce organically. For each, suggest one of:
- Adjusting the card assignment to match the plot need
- Adjusting the plot to let the archetype lead
- Adding a secondary card that creates the internal conflict necessary for the plot moment to feel organic
```

---

### Step 6: Create the Relationship Dynamics Reference

**File: `references/relationship-dynamics.md`**

```markdown
# Relationship Dynamics

How tarot-grounded personas interact based on their card assignments.

---

## Dynamic Types

### Complementary Pairs
Cards that complete each other. Their energies are different but harmonious — together they form something neither achieves alone.

| Pair | Dynamic | Narrative Effect |
|------|---------|-----------------|
| Emperor + Empress | Structure meets abundance | Stable creative partnership; parental dynamics |
| Magician + High Priestess | Conscious will meets unconscious knowing | Intuition and action in dialogue |
| Sun + Moon | Clarity meets ambiguity | One reveals, the other conceals — mutual dependency |
| Strength + Chariot | Inner mastery meets outer will | Patience and drive in tension-harmony |
| Star + Tower | Hope meets destruction | Renewal only possible after catastrophe |

### Tension Pairs
Cards whose energies fundamentally conflict. These create organic friction — no plot-manufactured disagreement needed.

| Pair | Tension | Narrative Effect |
|------|---------|-----------------|
| Emperor + Fool | Order vs. chaos | Authority threatened by the unbound |
| Hierophant + Tower | Tradition vs. destruction | Institutional stability vs. necessary collapse |
| Devil + Star | Bondage vs. hope | Chains vs. freedom — the core liberation arc |
| Hermit + Lovers | Solitude vs. union | Withdrawal vs. commitment — irreconcilable needs |
| Justice + Moon | Clarity vs. illusion | Truth vs. deception — investigative dynamics |

### Journey Echoes
Characters at different stages of the same journey. One has been where the other is going. Creates mentorship, generational tension, or cautionary dynamics.

Example: A Fool and a World character in the same story. The World has completed the journey the Fool is beginning. Their dynamic is simultaneously mentorship and mourning — the World sees their younger self; the Fool sees what they might become.

### Shadow Mirrors
One character's upright expression is another's reversed expression of the SAME card. These are the deepest antagonist relationships because the characters are fundamentally the same person who made a different choice.

Example: Two Emperor characters — one upright (protective authority), one reversed (tyrannical control). They are mirrors. Their conflict is not about opposing values but about the same value expressed at different poles. Each sees in the other what they fear becoming.

---

## Ensemble Dynamics

When designing a full cast, map all card assignments and check for:

1. **Archetypal coverage** — Does the cast span enough of the journey to create range?
2. **Natural tension lines** — Which characters will organically conflict? Are there at least two major tension pairs?
3. **Complementary anchors** — Which characters stabilize each other? Every tension pair needs at least one complementary pair to prevent the story from becoming pure conflict.
4. **Shadow mirror potential** — Is there at least one shadow mirror relationship? These produce the most psychologically resonant antagonisms.
5. **Journey progression** — Does the cast include characters at different journey stages? This creates depth of perspective.

## Suit Dynamics

Characters assigned Minor Arcana cards in different suits will naturally operate in different life domains. This creates organic misunderstanding:

- A Swords character (intellect) and a Cups character (emotion) will approach the same problem from fundamentally different frameworks — not because they disagree, but because they are literally processing in different domains.
- A Wands character (ambition) and a Pentacles character (material reality) will value different outcomes — one wants the vision, the other wants the result.

These domain conflicts are more subtle and more human than value conflicts. They produce the kind of miscommunication that feels real.
```

---

### Step 7: Create the Arc Engine Reference

**File: `references/arc-engine.md`**

```markdown
# Arc Engine

How the accept/reject/forget trichotomy drives narrative arcs.

---

## The Trichotomy

At every encounter with their archetype's lesson, a character does one of three things:

### Accept
The character integrates the lesson. Growth occurs. But "growth" is not always positive in narrative terms — accepting The Devil's lesson might mean acknowledging addiction rather than overcoming it. Accepting The Tower's lesson might mean letting everything burn.

**Arc shape:** Forward progression. Each acceptance moves the character to the next stage of the journey. Multiple acceptances in sequence produce a character who transforms visibly across the narrative.

**Risk:** If every encounter is accepted, the character can feel too smooth — like they learn too easily. Real people resist.

### Reject
The character refuses the lesson. They harden around their current position. An Emperor who rejects does not become weak — they become more Emperor, more rigid, more controlling. Rejection intensifies the current archetype rather than transforming it.

**Arc shape:** Calcification. The character becomes more extreme over time. This can be tragic (they were offered growth and refused) or terrifying (their worst qualities compound).

**Risk:** If every encounter is rejected, the character becomes predictable in their stubbornness. Mixing rejection with occasional almost-acceptance creates more tension.

### Forget
The character encounters the lesson, briefly glimpses understanding, and then loses it. This is distinct from rejection — the Forgetter is not hostile to growth; they are simply unable to hold onto it. They repeat.

**Arc shape:** Loop. The character returns to their starting position after each encounter. This is the most tragic response because it is not defiant — it is helpless. The audience sees what the character cannot hold.

**Risk:** If the loop is too visible too early, the audience can feel the pattern is contrived. Forgetting works best when the audience slowly realizes the character is repeating.

---

## Trichotomy in Practice

A single character typically has one dominant trichotomy response for their overall arc, but may exhibit different responses at different scales:

- **Story-level:** Overall, does this character accept, reject, or forget their archetype's central lesson?
- **Act-level:** Within each major section, how do they respond to specific encounters?
- **Scene-level:** In individual moments of pressure, which response emerges?

The most complex characters show different trichotomy responses at different scales. A character who is a story-level Forgetter might have scene-level moments of Acceptance — brief flashes where they grasp the truth — before the loop pulls them back. This creates the aching sense of "they almost made it."

---

## Arc Engine Combinations

When characters interact, their trichotomy responses create dynamic patterns:

| Character A | Character B | Dynamic |
|-------------|-------------|---------|
| Accept | Accept | Mutual growth — can feel too easy unless environment resists |
| Accept | Reject | Divergence — one grows while the other hardens. Classic mentor/student break |
| Accept | Forget | Asymmetric grief — A sees B's potential but B cannot hold it |
| Reject | Reject | Escalation — both harden, creating intensifying opposition |
| Reject | Forget | Frustration spiral — one doubles down, the other can't engage |
| Forget | Forget | Parallel loops — tragic if they keep almost finding each other |

---

## Using the Arc Engine for Pre-Writing

Before a scene, ask:
1. What lesson does this situation offer my character's archetype?
2. Will they accept, reject, or forget it in this moment?
3. How does that response move or stall or loop their arc?
4. How does their response interact with other characters' trichotomy states?

This replaces "what happens next?" with "what does this character's architecture produce in this situation?" — letting behavior emerge rather than being imposed.
```

---

### Step 8: Create Output Templates

**File: `references/output-template-dossier.md`**

```markdown
# Output Template: Persona Dossier

```markdown
# [CHARACTER NAME] — Tarot Persona Dossier

> Architected using TarotPersonaCreator
> Created: [date]

---

## Archetypal Identity

**Primary Card:** [Number] — [Card Name] ([Polarity State])
**Core Archetype:** [Archetype description]
**Journey Phase:** [Phase name] — [Phase description]
**Journey Position:** [Specific position and what it implies about their past and available futures]

---

## Card Spread

| Layer | Card | Role | Expression |
|-------|------|------|------------|
| Primary | [Major Arcana] | Core identity | [How this manifests] |
| Secondary | [Minor Arcana] | Situational domain | [Current life circumstances] |
| Court | [Court Card] | Social role | [How they operate in the world] |
| Internal Conflict | [Optional 2nd Major] | Hidden self | [What they are inside vs. outside] |

---

## Polarity Spectrum

**Upright Expression:**
[How this character looks, feels, and behaves when expressing their archetype's aspirational pole. Specific to this character, not generic card meaning.]

**Reversed Expression:**
[How this character looks, feels, and behaves when expressing their archetype's shadow pole. Specific to this character.]

**Current Position:** [Upright / Reversed / Tending Upright / Tending Reversed / Oscillating]

**Polarity Triggers:**
- Pushed toward upright by: [specific situational pressures]
- Pushed toward reversed by: [specific situational pressures]

---

## Shadow Architecture

**Shadow State:** [What this character's reversed expression looks like in concrete terms]

**Shadow Trigger:** [What would push them from current position toward full reversal]

**Shadow Visibility:** [How much of the shadow is already present in their behavior]

**Shadow Relationship:** [Are they aware of it? Do they fight, deny, flirt with, or ignore their shadow?]

---

## Arc Engine

**Trichotomy Response:** [Accept / Reject / Forget]

**Story-Level Arc:** [What their overall trajectory looks like given this response]

**The Lesson:** [What their archetype is trying to teach them]

**If They Accept:** [What they become]
**If They Reject:** [What they harden into]
**If They Forget:** [What loop they repeat]

---

## Behavioral Predictions

Given this architecture, the character will likely:

**Under pressure:** [predicted behavior based on archetype + polarity]
**When trusted:** [predicted behavior]
**When betrayed:** [predicted behavior]
**When given power:** [predicted behavior]
**When stripped of power:** [predicted behavior]
**In solitude:** [predicted behavior]
**In a crowd:** [predicted behavior]

---

## Cast Dynamics

**Complements:** [Which archetypes this character naturally harmonizes with]
**Tensions:** [Which archetypes create organic friction]
**Shadow Mirrors:** [Who in the cast represents their reversed pole]
**Journey Echoes:** [Who is at a different stage of the same path]

---

## Designer Notes

[Any additional context about how this character should be used, common misinterpretations to avoid, and situational environments that will best reveal their depth.]

---

*Architected using TarotPersonaCreator — Tarot-Based Persona Layer Grounding*
```
```

**File: `references/output-template-assessment.md`**

```markdown
# Output Template: Tarot Assessment

```markdown
# [CHARACTER NAME] — Tarot Persona Assessment

> Assessed using TarotPersonaCreator
> Source: [description of input material]
> Assessment Date: [date]

---

## Executive Summary

[2-3 sentences: Who is this character archetypally? What is their current depth level? What are the key enhancement opportunities?]

---

## Emergent Archetype

**Detected Primary Card:** [Card] — [Why this card fits]
**Detected Polarity:** [Current polarity state]
**Detected Journey Position:** [Where they sit on the Fool's Journey]
**Confidence:** [High/Medium/Low — how clearly the archetype emerges from the source material]

---

## Seven-Dimension Assessment

| # | Dimension | Score | Evidence |
|---|-----------|-------|----------|
| 1 | Archetypal Grounding | /5 | [Specific examples] |
| 2 | Polarity Depth | /5 | [Specific examples] |
| 3 | Shadow Presence | /5 | [Specific examples] |
| 4 | Journey Coherence | /5 | [Specific examples] |
| 5 | Organic Contradiction | /5 | [Specific examples] |
| 6 | Situational Emergence | /5 | [Specific examples] |
| 7 | Arc Engine | /5 | [Specific examples] |

**Overall Persona Depth Score:** [X]/5

---

## Enhancement Recommendations

### Critical (Dimensions scoring 1-2)

[For each low-scoring dimension, provide specific tarot-grounded recommendations]

### Strengthening (Dimensions scoring 3)

[For each moderate dimension, suggest specific additions]

### Already Strong (Dimensions scoring 4-5)

[Acknowledge what works and suggest refinements]

---

## Forced Decision Flags

[Identify moments where the character acts because the plot requires it rather than because their architecture demands it. For each, suggest organic alternatives.]

| Moment | Current Motivation | Suggested Organic Motivation |
|--------|-------------------|------------------------------|
| [Scene/decision] | [Plot-driven reason] | [Archetype-emergent reason] |

---

## Cast Dynamic Analysis (if applicable)

[How this character's archetype interacts with others in the ensemble]

---

## Suggested Tarot Spread

If the creator chose to formalize this character's architecture:

| Layer | Suggested Card | Reasoning |
|-------|---------------|-----------|
| Primary | [Card] | [Why] |
| Secondary | [Card] | [Why] |
| Court | [Card] | [Why] |
| Shadow | [Reversed expression] | [Why] |
| Trichotomy | [Accept/Reject/Forget] | [Why] |

---

*Assessed using TarotPersonaCreator — Tarot-Based Persona Layer Grounding*
```
```

**File: `references/output-template-consult.md`**

```markdown
# Output Template: Tarot Consult

```markdown
# [PROJECT NAME] — Tarot Persona Consultation

> Consultation using TarotPersonaCreator
> Premise: [brief description]
> Date: [date]

---

## Premise Analysis

[Brief summary of the story's world, tone, themes, and central conflicts as understood from the input.]

---

## Archetypal Needs

This premise requires the following archetypal energies:

| Need | Suggested Card | Role in Story | Justification |
|------|---------------|---------------|---------------|
| [Function] | [Card] | [How they serve the narrative] | [Why this card fits the premise] |

---

## Suggested Cast Architecture

### [Character Role 1]

**Suggested Primary Card:** [Card] ([Polarity])
**Journey Position:** [Phase]
**Secondary Card:** [Minor Arcana]
**Court Card:** [Court Card]
**Trichotomy:** [Accept/Reject/Forget]
**Why This Configuration:** [How this serves the premise specifically]

### [Character Role 2]
[Same structure]

---

## Tension Map

| Character A | Character B | Dynamic Type | What It Produces |
|-------------|-------------|-------------|-----------------|
| [Name/Role] | [Name/Role] | [Complement/Tension/Echo/Shadow] | [Organic narrative effect] |

---

## Pressure Environments

Situations that would organically reveal character depth:

| Environment | Which Characters It Pressures | What It Reveals |
|------------|------------------------------|-----------------|
| [Situation] | [Characters affected] | [Archetypal behavior that emerges] |

---

## Cast Gaps and Redundancies

**Gaps:** [Archetypal energies the story needs but the current cast doesn't provide]

**Redundancies:** [Characters occupying the same archetypal space unnecessarily]

**Recommendations:** [Specific adjustments]

---

## Plot-Architecture Alignment

| Plot Beat | Required Character Action | Archetype Alignment | Notes |
|-----------|--------------------------|--------------------| ------|
| [Event] | [What needs to happen] | [Does the archetype produce this naturally?] | [Adjustments if needed] |

---

*Consultation using TarotPersonaCreator — Tarot-Based Persona Layer Grounding*
```
```

---

## 4. Installation

To install the skill for Claude Code, place the entire `tarot-persona-creator/` directory into your skills folder:

```bash
# If using Claude Code with user skills
cp -r tarot-persona-creator/ /path/to/your/skills/user/tarot-persona-creator/

# Verify structure
ls -la /path/to/your/skills/user/tarot-persona-creator/
# Should show: SKILL.md, references/, assets/
```

For Claude.ai with custom skills enabled, upload the skill directory following the platform's skill installation procedure.

---

## 5. Usage Examples

### Create Mode
```
User: "Using tarot persona creator, build me a character who is a
disgraced military officer trying to rebuild their life in a small
fishing village. They carry guilt about an order they gave that
got people killed."

Skill: [Reads protocols, assigns cards, generates PersonaDossier.md]
```

### Assess Mode
```
User: "Using tarot persona creator, assess this character:
Elena is a 34-year-old journalist who discovered her editor has been
killing stories about corporate pollution. She's torn between
exposing him and protecting her career. She's described as brave
but also ambitious and sometimes selfish."

Skill: [Reads assessment protocol, scores seven dimensions, generates
TarotAssessment.md with enhancement recommendations]
```

### Consult Mode
```
User: "Using tarot persona creator, I'm planning a story set in a
failing restaurant. The chef-owner is losing the business, their
sous chef wants to take over, there's a food critic coming, and
the chef's estranged daughter shows up. Help me architect these
personas so the drama feels organic."

Skill: [Reads consult protocol, maps archetypal needs, suggests card
assignments, identifies tension pairs, generates TarotConsult.md]
```

---

## 6. Key Design Decisions

**Why Tarot and Not Myers-Briggs / Enneagram / Big Five:**
Personality typologies describe how people *are*. Tarot describes how people *move* — their trajectory, their shadow, their transformation potential. Characters need movement, not categorization.

**Why the Trichotomy Matters:**
Most character design systems describe who a character is. The accept/reject/forget trichotomy describes what a character *does with what happens to them*. This is the difference between a portrait and an engine.

**Why Shadow Architecture Is Non-Negotiable:**
Characters without shadow are characters without depth. The reversed reading is not optional ornamentation — it is the structural counterweight that makes the upright reading meaningful. A character who is "brave" means nothing until you understand that their specific form of bravery is one choice away from their specific form of cowardice.

**Why Situational Emergence Over Forced Decisions:**
If you have to write "and then she decided to..." — the architecture has failed. A properly grounded persona should produce behavior that feels inevitable given who they are and what pressure they're under. The author's job shifts from *directing* the character to *placing* the character in environments that reveal them.

---

*Implementation Guide for TarotPersonaCreator Skill — Tarot-Based Persona Layer Grounding System*
