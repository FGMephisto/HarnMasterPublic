# HarnMaster Status Effects & Conditions Reference

This document provides a comprehensive canonical compendium of status effects, conditions, trauma states, afflictions, and enchantments in **HarnMaster (Third Edition / 3.5E)**, synthesized from:
- **HarnMaster Core Rules (3e)**
- **HarnMaster Magic (Shek-Pvar)**
- **HarnMaster Religion (Libram of the Pantheon)**

It includes standard rules mechanics, resistance tests (Saving Throws), durations, and exact **Fantasy Grounds Unity (FGU)** effect strings for automation.

---

## Table of Contents
1. [Physical Combat & Trauma Status Effects](#1-physical-combat--trauma-status-effects)
   - [Consciousness & Shock](#consciousness--shock)
   - [Mobility, Balance & Posture](#mobility-balance--posture)
   - [Wounds, Bleeding & Crippling](#wounds-bleeding--crippling)
   - [Physiological & Environmental Conditions](#physiological--environmental-conditions)
   - [Morale & Combat Mindsets](#morale--combat-mindsets)
2. [Esoteric & Psionic Status Effects](#2-esoteric--psionic-status-effects)
3. [Arcane Magical Status Effects (HarnMaster Magic)](#3-arcane-magical-status-effects-harnmaster-magic)
   - [Lyahvi (Air / Light / Illusion)](#lyahvi-air--light--illusion)
   - [Peleahn (Fire / Heat)](#peleahn-fire--heat)
   - [Jmorvi (Metal / Mineral)](#jmorvi-metal--mineral)
   - [Fyvria (Earth / Flora / Fauna)](#fyvria-earth--flora--fauna)
   - [Odivshe (Water / Cold / Shadow)](#odivshe-water--cold--shadow)
   - [Savorya (Mind / Spirit / Knowledge)](#savorya-mind--spirit--knowledge)
   - [Gray / Neutral Magic](#gray--neutral-magic)
4. [Divine Invocations & Miracles (HarnMaster Religion)](#4-divine-invocations--miracles-harnmaster-religion)
   - [Common Church Rituals](#common-church-rituals)
   - [Agrik (Fire, War, Cruelty)](#agrik-fire-war-cruelty)
   - [Halea (Wealth, Pleasure, Intrigue)](#halea-wealth-pleasure-intrigue)
   - [Ilvir (Creation, Ivashu)](#ilvir-creation-ivashu)
   - [Larani (Honor, Chivalry, War)](#larani-honor-chivalry-war)
   - [Morgath (Death, Undead, Chaos)](#morgath-death-undead-chaos)
   - [Naveh (Shadows, Assassination, Night)](#naveh-shadows-assassination-night)
   - [Peoni (Healing, Agriculture, Mercy)](#peoni-healing-agriculture-mercy)
   - [Sarajin (Battle, Honor, Frost)](#sarajin-battle-honor-frost)
   - [Save-K'nor (Knowledge, Riddles, Order)](#save-knor-knowledge-riddles-order)
   - [Siem (Dreams, Astral, Mystery)](#siem-dreams-astral-mystery)
5. [FGU Automation & Effect String Master Matrix](#5-fgu-automation--effect-string-master-matrix)

---

## 1. Physical Combat & Trauma Status Effects

These conditions stem from physical injuries, tactical combat maneuvers, fatigue, infections, and environmental hazards.

### Consciousness & Shock

| Status Effect | Source / Trigger | Rule Mechanics | Duration & Recovery | FGU Effect Syntax |
| :--- | :--- | :--- | :--- | :--- |
| **Shock Check** | Taking any injury | Roll 1d6 per Universal Penalty (UP). If total exceeds **Endurance**, character collapses. | Instantaneous trigger | `[SHOCK CHECK]` |
| **Unconscious** | Failed Shock Roll or Trauma | Character is helpless. Drops held items, falls Prone, cannot make actions or tests. Opponents gain automatic Tactical Advantage. Defenses are ignored (`DEF: Ignore`), resulting in uncontested strikes. | 1 minute recovery checks (Shock recovery table); then 10 min checks. | `Unconscious; Prone; DEF: Ignore` |
| **Incapacitated** | Passing first recovery check from Unconscious | Transitional recovery state. Must immediately roll a second Shock Check: Pass = full recovery; Fail = degrades into Shock. Initiative penalized by -10. | Instant / 1 round | `Incapacitated; INIT: -10` |
| **Shock (Medical State)** | Degraded from Incapacitated or Trauma threshold | Critical state with Healing Rate H5 (no injury levels). Requires a Shock Recovery roll every **4 hours** (Target = HR × END). Reaches H6 = recovered; H0 = death. | 4-hour checks until H6 or death | `Shock; CHECK: -20` |

### Mobility, Balance & Posture

| Status Effect | Source / Trigger | Rule Mechanics | Duration & Recovery | FGU Effect Syntax |
| :--- | :--- | :--- | :--- | :--- |
| **Stumble** | Leg injury (S2+), Knockback, sudden terrain shift | Roll **Agility** check (modified by UP). Failure causes loss of balance: character drops to **Prone**, suffers Tactical Disadvantage. | 1 round (until character stands) | `Stumble; Prone` |
| **Fumble** | Arm/Shoulder injury (S2+), Wild attack result | Roll **Dexterity** check. Failure causes weapon or shield to be dropped, misdirected, or damaged. | Instantaneous | `Fumble` |
| **Prone (Knockdown)** | Result of Stumble, tackle, or impact | Character is on the ground. Suffers **-20 EML** on attacks and defenses (`ATK: -20; DEF: -20`). Standing opponents striking a prone target gain **+20 EML**. Costs half movement to stand. | Until standing (requires move action) | `Prone; ATK: -20; DEF: -20` |
| **Knockback** | Effective blunt/physical impact > Strength | Character is forced backward 1 hex (5 ft) per threshold. Must make an immediate **Stumble Roll**. | Instantaneous | `Knockback: 1 hex` |
| **Disarmed** | Tactical maneuver or critical fumble | Weapon is dislodged, knocked away, or pinned. Character must draw another weapon or fight unarmed. | Until retrieved or switched | `Disarmed` |
| **Restrained / Grappled** | Grapple, entanglement, pinning | Move reduced to 0. Suffers **-20 EML** on non-grapple actions and defenses. Opponents gain **+20 EML** against the restrained target. | Until broken via STR or AGL contest | `Restrained; ATK: -20; DEF: -20` |

### Wounds, Bleeding & Crippling

| Status Effect | Source / Trigger | Rule Mechanics | Duration & Recovery | FGU Effect Syntax |
| :--- | :--- | :--- | :--- | :--- |
| **Bleeder (Bloodloss)** | Grievous wound (G4, G5) from Blunt, Edge, or Point | Accumulates **1 Bloodloss Point (1 BP)** every minute. BPs act as a cumulative injury. If total BPs exceed **Endurance**, victim dies of exsanguination. | Continuous until treated (Tourniquet, Pressure, Cauterization, Magic) | `Bleeding: 1 BP/min` |
| **Limb Crippled / Unusable** | Grievous injury (G4, G5) to arm, leg, wing, or tail | Limb is completely non-functional. Leg: crawl or crutch (half Move); Arm: cannot hold items or parry. Biped with 1 bad leg crawls; with 2 bad legs immobilized. | Until wound heals to M1 | `Crippled Limb; CHECK: -20` |
| **Amputation / Severed Limb** | Grievous Edge strike to extremity | Body part is severed if damage roll exceeds 1/10th body weight. Automatically becomes a **G5 wound**, causes automatic Stumble/Fumble, and creates an immediate **Bleeder**. | Permanent | `Amputated; Bleeding: 1 BP/min; CHECK: -30` |
| **Blinded (Single Eye)** | Puncture/Slash to eye location (S2+) | Loss of binocular vision. Permanent -20 EML on missile weapons, visual awareness, and depth perception. | Permanent unless magically restored | `Blinded Eye; CHECK: -20 eyesight` |
| **Blinded (Complete)** | Both eyes destroyed, flash spells, venom | Total loss of sight. Suffers **-40 EML** on attacks and **-20 EML** on defenses (reliant on acoustic awareness). Movement halved; tactile awareness tests required. | Permanent or spell duration | `Blinded; ATK: -40; DEF: -20` |
| **Deafened** | Skull/Ear trauma, thunder spells/miracles | Inability to hear auditory cues. Automatic failure on Hearing tests. -20 EML on surprise checks; verbal communication impossible. | Medical recovery or spell duration | `Deafened; CHECK: -30 hearing` |

### Physiological & Environmental Conditions

| Status Effect | Source / Trigger | Rule Mechanics | Duration & Recovery | FGU Effect Syntax |
| :--- | :--- | :--- | :--- | :--- |
| **Fatigue (FL)** | Exertion, heavy armor, heat, spells | Each Fatigue Level adds **+1 to Universal Penalty (UP)** (-10% to all skills and +1d6 to Shock rolls). Recorded directly in the sheet/CT **FT** box. | 1 FL recovers per 10 minutes of resting | Native **FT** Box: `+1 FT per FL` |
| **Encumbered** | Load exceeds carrying capacity | Encumbrance Penalty (EP) directly subtracts from all physical skills (Move, Dodge, Acrobatics, Combat). Move rate halved or quartered. | Until load is dropped or adjusted | `Encumbered; CHECK: -10; SPEED: /2` |
| **Infected (INF)** | Open wound failing 5-day Healing Roll | Wound becomes infected. Tested daily on Infection Table (HR × END). Lowers HR on failure. Sepsis/Gangrene causes death if HR reaches H0. Defeated at HR6. | Daily tests until defeated or death | `Infected; HR: -1` |
| **Diseased** | Pathogen exposure (Contagion Index 1-7) | Character suffers specific disease symptoms (Fever, Delirium, Chills, Nausea). Applies a **Special Penalty of -10 to -30** to physical skills. Tested daily. | Daily recovery tests (HR1-HR5) | `Diseased; CHECK: -20` |
| **Poisoned (Venom)** | Toxin via injection, ingestion, contact | Categories: Irritant (-10 to -30 penalty), Paralytic (stiffness to complete paralysis), Soporific (drowsiness/sleep), Lethal (rapid tissue death). Evaluated like fast-acting infections. | Hours, minutes, or rounds depending on toxin | `Poisoned; CHECK: -20` |
| **Burning (On Fire)** | Flammable impact, fire magic, Greek fire | Inflicts **1d6 Fire (F)** damage per round. Equipment may ignite. Requires a full round and Agility test (or rolling on ground) to extinguish. | Until smothered, doused, or consumed | `Burning: 1d6 F` |
| **Frostbite / Hypothermia** | Extreme cold, Odivshe ice magic | Mild: Shivering, numbness (-10 Special Penalty); Serious: 2nd degree frostbite (blisters); Grievous: 3rd degree (gangrene, requires amputation). | Warming over 1d3 hours or medical care | `Frostbite; CHECK: -10` |
| **Asphyxiation / Drowning** | Submersion, choking, smoke, vacuum | Deprived of air. Can hold breath for Endurance × 10 seconds. Afterward, makes an **Endurance check** each round (cumulative -10 penalty). Failure = Unconscious, followed by death in 1d3 rounds. | Rounds until air is restored or death | `Asphyxiating; Drowning` |

### Morale & Combat Mindsets

| Status Effect | Source / Trigger | Rule Mechanics | Duration & Recovery | FGU Effect Syntax |
| :--- | :--- | :--- | :--- | :--- |
| **Frightened / Morale Broken** | Leader casualty, severe wounds, terrifying foes | Failed Morale check (Will × multiplier). Character panics, retreats, or surrenders. Cannot initiate attacks; focuses purely on flight or defensive parries (-20 EML attack / -10 EML defense). | Until rallying check or combat ends | `Frightened; ATK: -20; DEF: -10` |
| **Berserk / Battle Rage** | Cultural trait, Sarajin miracles, frenzy | Character enters an uncontrollable bloodlust. Ignores all pain, shock, and fatigue penalties. Gains **+20 EML** to attack. Cannot parry, dodge, or disengage until all enemies fall. | Duration of melee engagement | `Berserk; ATK: 20; IGNOREPENALTY` |
| **Tactical Advantage (TA)** | Combat Matrix outcome (CS vs CF/MF, or tactical maneuvers) | The victor of a combat exchange earns **Tactical Advantage**, allowing them to dictate the next exchange (initiative, posture, or +10/+20 EML on follow-up attack) over their opponent. | 1 exchange / active round | `ATK: 20` |
| **Tactical Disadvantage** | Outmaneuvered, poor footing, restricted space | Actor is put at tactical disadvantage by opponent; suffers **-20 EML** on combat actions. | 1 exchange / active round | `ATK: -20; DEF: -20` |

---

## 2. Esoteric & Psionic Status Effects

Psionic talents represent innate psychic phenomena that bypass physical armor and directly target mind or physiology.

| Psionic Talent | Activation & Range | Target Resistance | Resulting Status Effect | FGU Effect Syntax |
| :--- | :--- | :--- | :--- | :--- |
| **Charm** | 15-SI Secs; Range: SI yards | **Will × 5 (MS)** / **Will × 3 (CS)** | **CF**: Frozen in place for 10s; must choose *Ignore* defense if attacked.<br>**MF**: Frozen in place for 10s; may defend normally.<br>**CS/MS**: Unaffected. | `Charm; Stunned; DEF: Ignore` |
| **Mental Bolt** | 25-SI Secs; Range: SI × 5 yds | None (Direct assault) | **MS**: Victim accrues **2 Fatigue Levels (F2)**.<br>**CS**: Victim accrues **4 Fatigue Levels (F4)**.<br>Victim must make an **immediate Shock Roll**. | Native **FT** Box: `+2 FT (MS) / +4 FT (CS)` |
| **Hex (Evil Eye)** | 15-SI Mins; Line of sight / SI leagues | None (Subject to hair/nail focus) | **MS**: Victim's next skill, talent, or spell test is rolled at **half EML**.<br>**CS**: **Half EML** on all skills for ML minutes. | `Hexed; CHECK: /2` |
| **Negation** | 15-SI Secs; Radius: Will feet | Area Field (SI minutes) | All spells, talents, and magical effects entering the field are degraded by **one success level** (CS→MS, MS→MF, MF→CF). | `Negation Field; SPELLDEGRADE: 1` |
| **Ethereal Possession** | Medium or haunting encounters | **Will vs Spirit Will** | Victim's bodily control is overridden by an ethereal spirit. Soul is suppressed or enters catatonia. | `Possessed; Incapacitated` |

---

## 3. Arcane Magical Status Effects (HarnMaster Magic)

Across the six Shek-Pvar chantries and Gray (Neutral) magic, spells generate distinct tactile and supernatural conditions.

### Lyahvi (Air / Light / Illusion)
- **Globe of Setath (III)**: Creates a fascinating, multi-colored hovering sphere.
  - *Save*: Will × 4 (MS Globe) / Will × 2 (CS Globe)
  - *CF*: Stationary, gazing into globe until removed; cannot make rolls (`Fascinated; Stunned`).
  - *MF*: Gazes helplessly for 10 seconds; roll to break free each 10s (`Stunned; dur: 1 rnd`).
  - *MS*: Distracted for 10s; opponents earn tactical advantage; suffers **-10 Special Penalty** and -10 defense (`Distracted; CHECK: -10; DEF: -10; dur: 1 rnd`).
  - *CS*: Ignores globe.
- **Hlandor's Flash (II)**: Sudden brilliant pulse of light.
  - *Save*: Eyesight test.
  - *Effect*: **Blinded** and disoriented for 1d6 rounds (MS) or 2d6 minutes (CS). Attacks at -40 EML; defense at -20 EML.
  - *FGU Effect*: `Blinded; ATK: -40; DEF: -20; dur: 1d6 rnd`
- **Cloak of Kalaerin (II)**: Bends light around the recipient.
  - *Effect*: **Invisible / Concealed**. Attacks against recipient suffer -20 EML penalty. Recipient gains +20 EML on stealth and attacks from unseen posture.
  - *FGU Effect*: `Invisible; ATK: 20; DEF: 20`
- **Prism of Gethan (III)**: Disorienting rainbow aura.
  - *Effect*: Targets dazzled by shifting hues; **-10 Special Penalty** on visual and combat rolls.
  - *FGU Effect*: `Dazzled; CHECK: -10`
- **Maslor's Charm (VII)**: Potent compulsion of light and charisma.
  - *Save*: Will test.
  - *Effect*: Target is completely **Charmed**; regards caster as absolute master, incapable of harmful intent.
  - *FGU Effect*: `Charmed; PACIFIED`
- **Aeric's Whisper (I)**: Phantasmal auditory illusion.
  - *Effect*: Distracts guards or opponents; forces Awareness checks or imposes surprise.
  - *FGU Effect*: `Distracted; CHECK: -10`
- **Vapor of Hirin (VI)**: Dense illusory obscuration.
  - *Effect*: Total visual cover; all creatures inside treated as **Blinded** to exterior lines of sight.
  - *FGU Effect*: `Obscured; Blinded`

### Peleahn (Fire / Heat)
- **Zyrgin's Heat (I)**: Radiates intense thermal energy.
  - *Save*: Endurance test.
  - *Effect*: Induces **Heat Exhaustion** and dehydration. Target accrues 1 Fatigue Level per round.
  - *FGU Effect*: `Heat Exhaustion`; Native **FT** Box: `+1 FT/round`
- **Sphere of Shanakar (I) & Sea of Fire (IV)**: Flaming burst or wave.
  - *Effect*: Deals direct Fire (F) damage and **Ignites** victims. Victims catch fire (1d6 F damage/round until extinguished).
  - *FGU Effect*: `Burning: 1d6 F`
- **Skin of Lexesh (II)**: Molten defensive mantle.
  - *Effect*: Grants **Fire Immunity / Absorption** and inflicts 1d6 F damage on unarmed/melee attackers striking the caster.
  - *FGU Effect*: `Fire Warded; DMGTHORNS: 1d6 F`
- **Aidan's Hastening (II)**: Cellular hyper-acceleration.
  - *Effect*: **Hastened**. Movement doubled; gains +20 EML to Initiative and an additional defensive/combat option per round.
  - *FGU Effect*: `Hastened; INIT: 20; SPEED: *2`
- **Charachi's Fever (IV)**: Thermal somatic infection.
  - *Save*: Endurance test.
  - *Effect*: Severe internal fever, delirium, and shivering. Imposes **-20 Special Penalty** to all mental and physical actions; progressive fatigue.
  - *FGU Effect*: `Fevered; Delirious; CHECK: -20`
- **Bolts of Dag (V)**: Concentrated projectile plasma.
  - *Effect*: Severe trauma + fire damage; forces immediate Stumble and Shock rolls.
  - *FGU Effect*: `Burn Trauma; Stumble`

### Jmorvi (Metal / Mineral)
- **Aspect of Tarus (II)**: Transmutes outer skin into mineral hardness.
  - *Effect*: Grants +4 to +8 physical armor protection (Blunt, Edge, Point), but increases weight and imposes **-10 to Agility/Acrobatics**.
  - *FGU Effect*: `Armor Buff: 6; AGL: -10`
- **Anvil of Pytama (III) & Fist of Kuhan (IV)**: Telekinetic kinetic bludgeon.
  - *Effect*: Heavy blunt impact; forces automatic **Knockback** (1-3 hexes) and mandatory **Stumble Roll**.
  - *FGU Effect*: `Knockback; Stumble`
- **Barl's Cloak (VI)**: Sheaths target in malleable metallic carapace.
  - *Effect*: Extreme armor value (+12), but reduces Move by half and adds 2 Encumbrance Levels.
  - *FGU Effect*: `Metal Cloak; ARMOR: 12; SPEED: /2`
- **Sirik's Cant (III)**: Molecular reinforcement or degradation of metals.
  - *Effect*: Can render an opponent's weapon brittle (shatters on next impact > 5) or reinforce ally weapons.
  - *FGU Effect*: `Brittle Weapon`

### Fyvria (Earth / Flora / Fauna)
- **Dream of Galega (IV)**: Enchanted natural slumber.
  - *Save*: Will × 5.
  - *CF*: Asleep for 2d6 hours (`Unconscious; Asleep`).
  - *MF*: Asleep for 1d6 hours (`Unconscious; Asleep`).
  - *MS*: Drowsy for 1d6 rounds (`Drowsy; CHECK: -10`).
  - *CS*: Unaffected.
- **Verdant Hand (II) & Hand of Iliam (II)**: Animated undergrowth and roots.
  - *Save*: Agility or Strength check.
  - *Effect*: Targets in area are **Entangled / Restrained**. Move reduced to 0; -20 EML on attacks; opponents gain +20 EML against them.
  - *FGU Effect*: `Entangled; Restrained; ATK: -20; DEF: -20`
- **Vine of Alguinas (IV)**: Constricting magical creepers.
  - *Effect*: **Grappled & Choked**. Inflicts 1d6 Blunt impact per round; forces Asphyxiation checks if wrapped around torso/neck.
  - *FGU Effect*: `Constricted; Asphyxiating`
- **Balm of Gresan (I)**: Accelerated biological coagulation.
  - *Effect*: Immediately **Stops Bleeders**; heals 1-2 Injury Levels; cures minor infections.
  - *FGU Effect*: `Healed; Bleeding Stopped`
- **Animus of Nithri (V)**: Primal empathetic sovereignty.
  - *Effect*: Beasts and natural predators are completely **Pacified / Charmed**; will not attack and follow simple instincts.
  - *FGU Effect*: `Pacified; Charmed`

### Odivshe (Water / Cold / Shadow)
- **Azure Hand (I) & Shadow of Yanar (II)**: Deep shadow synthesis.
  - *Effect*: Extinguishes non-magical light. Caster or area surrounded by absolute gloom; exterior observers suffer **Blinded / Concealed** penalties.
  - *FGU Effect*: `Shadow Cloak; DEF: 20`
- **Breath of Dhivu (III) & Pall of Veshel (IV)**: Freezing gale and creeping permafrost.
  - *Save*: Endurance test.
  - *Effect*: Targets suffer Frost (F) damage and become **Chilled / Numbed**. -10 to -20 penalty to physical dexterity; movement halved.
  - *FGU Effect*: `Chilled; CHECK: -15; SPEED: /2`
- **Mouth of Lathal (III)**: Amphibious pulmonary inversion.
  - *Effect*: Grants water breathing. However, if used offensively (or reversed as Curse of Balrin), victim's lungs fill with water on dry land, causing **Drowning / Suffocation**.
  - *FGU Effect*: `Drowning; Asphyxiating`
- **Curse of Balrin (IV)**: Desiccation or watery asphyxiation.
  - *Save*: Endurance × 3.
  - *Effect*: Inability to breathe air. Victim begins suffocating immediately on dry land.
  - *FGU Effect*: `Suffocating; Drowning`

### Savorya (Mind / Spirit / Knowledge)
- **Ordeal of Frida (III)**: Nightmare psychosis excitation.
  - *Save*: Will × 5 (MS) / Will × 2 (CS).
  - *Effect*: Triggers acute phobias or manias. Victim becomes **Panicked / Cowering** or falls into a **Catatonic Stun** for duration.
  - *FGU Effect*: `Phobic Panic; Frightened; Stunned`
- **Jerila's Zone (V)**: Mnemonic fog field.
  - *Save*: Will test.
  - *Effect*: Induces **Amnesia & Disorientation**. Victims forget recent memories, current combat objectives, and identity of allies/foes.
  - *FGU Effect*: `Confused; Amnesic; CHECK: -20`
- **Aron's Thought (II) & Loth's Key (III)**: Telepathic breach.
  - *Save*: Will test.
  - *Effect*: Target's thoughts laid bare; caster anticipates moves, gaining **+20 EML to attack and defense** against victim.
  - *FGU Effect*: `Mind Probed; DEF: -20`
- **Galra's Enhancement (II) & Perfection of Sif (I)**: Cognitive and sensory amplification.
  - *Effect*: Boosts chosen attribute (INT, WIL, AUR, EYE) by +2 to +5; grants immunity to sensory overload.
  - *FGU Effect*: `Enhanced Mind; INT: 3; WIL: 3`
- **Spirit Block (IV)**: Impenetrable psychic bulwark.
  - *Effect*: Complete immunity to psionics, charm, fear, and mental enchantments.
  - *FGU Effect*: `Mind Shield; IMMUNE: charmed, frightened`
- **Veil of Iros (VI)**: Psychic invisibility.
  - *Effect*: Minds simply ignore presence of caster. Counts as total **Invisibility** against sentient minds.
  - *FGU Effect*: `Invisible; Mind-Veiled`

### Gray / Neutral Magic
- **Dispell (I)**: Arcane unraveling.
  - *Effect*: Strips active enchantments, status effects, and magical wards from target.
  - *FGU Effect*: `Dispelled`
- **Soul Stealer (V)**: Ethereal severing.
  - *Save*: Will test vs Caster CML.
  - *Effect*: Soul drawn out into receptacle. Physical body left in permanent **Catatonia / Coma** until soul is returned.
  - *FGU Effect*: `Catatonic; Comatose; Incapacitated`
- **Arwyn's Bubble (V)**: Life-sustaining biosphere.
  - *Effect*: Immune to environmental hazards, drowning, gas, vacuum, and extreme temperature.
  - *FGU Effect*: `Life Support; IMMUNE: drowning, suffocation`

---

## 4. Divine Invocations & Miracles (HarnMaster Religion)

Clerical rituals invoke divine intervention from the Pantheon of Hârn, producing powerful celestial and infernal conditions.

### Common Church Rituals
- **Awe (III)**: The cleric radiates terrifying divine presence.
  - *Save*: Will × 3 (or Morale check).
  - *Effect*: Opponents are **Awestruck / Frozen** in reverence. Cannot initiate attacks against the priest; must choose *Ignore* or defensive reactions.
  - *FGU Effect*: `Awestruck; Pacified; ATK: -20`
- **Curse (IV)**: Pronouncement of divine wrath.
  - *Effect*: Victim suffers continuous misfortune; **-10 to -20 Special Penalty** on all skill and combat tests for days or months.
  - *FGU Effect*: `Cursed; CHECK: -15`
- **Blessing (II)**: Impartation of celestial grace.
  - *Effect*: Grants **+10 EML** bonus to all tests and saves made in righteous defense.
  - *FGU Effect*: `Blessed; CHECK: 10; ATK: 10`
- **Endure (III)**: Divine analgesic fortitude.
  - *Effect*: Recipient ignores all **Pain, Injury Penalties, and Fatigue Penalties** for duration.
  - *FGU Effect*: `Enduring; IGNOREPENALTY`
- **Command (V)**: Inviolable clerical decree.
  - *Save*: Will test.
  - *Effect*: Target is **Compelled** to execute a single non-suicidal command ("Halt", "Surrender", "Flee", "Kneel").
  - *FGU Effect*: `Commanded; Compelled`
- **Excommunication (V)**: Severance of divine connection.
  - *Effect*: Piety stripped; unable to invoke miracles or receive divine aid; marked as anathema.
  - *FGU Effect*: `Excommunicated`
- **Exorcism (V)**: Expulsion of invading spirits.
  - *Effect*: Forces demonic or ethereal possessors out of the victim's body.
  - *FGU Effect*: `Dispossessed`

### Agrik (Fire, War, Cruelty)
- **Ak-Syt's Peace (II)**: Excruciating ritual torture trance.
  - *Effect*: Target incapacitated by intense sensory agony.
  - *FGU Effect*: `Agony; Incapacitated`
- **Mamaka's Cry (III) & Intimidation (IV)**: Terrifying hellish scream.
  - *Save*: Will test.
  - *Effect*: Enemies are **Terrified / Panicked**; must flee or cower. Attacks suffer -20 EML.
  - *FGU Effect*: `Frightened; Panicked; ATK: -20; DEF: -10`
- **Searing Hand (III) & Flames of the V'hir (IV)**: Unholy hellfire projection.
  - *Effect*: Causes severe 3rd degree burns and sets victims **On Fire** (1d6 F damage/round).
  - *FGU Effect*: `Burning: 1d6 F`
- **Agrik's Rot (IV)**: Demonic necrotic curse.
  - *Save*: Endurance test.
  - *Effect*: Flesh instantly decays with necrotic gangrene. Healing Rate drops to H1; spreads rapidly.
  - *FGU Effect*: `Necrotic Rot; Infected; HR: 1`
- **Crimson Dance (IV)**: Blood-crazed berserk trance.
  - *Effect*: Cleric or champion enters divine frenzy; immune to shock and pain; +20 EML to attack.
  - *FGU Effect*: `Crimson Frenzy; Berserk; ATK: 20`

### Halea (Wealth, Pleasure, Intrigue)
- **Ecstasy (II) & Tania's Pleasure (III)**: Overwhelming sensual bliss.
  - *Save*: Will × 4 (MS) / Will × 2 (CS).
  - *Effect*: Target is completely **Incapacitated with Pleasure**; drops weapons, placid, incapable of hostile action.
  - *FGU Effect*: `Ecstatic; Incapacitated; Docile`
- **Dulcia's Song (II) & Silver Tongue (II)**: Irresistible allure.
  - *Save*: Will test.
  - *Effect*: Target is **Charmed / Enamored**; regards speaker with adoration, highly gullible to suggestion.
  - *FGU Effect*: `Charmed; Enamored`
- **Sadura's Rash (V)**: Agonizing, maddening pruritus.
  - *Save*: Endurance test.
  - *Effect*: Unbearable violent itching across the body. Imposes **-20 Special Penalty** on all skills and prevents spellcasting.
  - *FGU Effect*: `Maddening Rash; CHECK: -20; ATK: -20`
- **Halea's Apple (IV)**: Seeds of covetous discord.
  - *Save*: Will test.
  - *Effect*: Inoculates intense **Greed & Paranoia**; targets turn upon their companions to seize riches.
  - *FGU Effect*: `Covetous Paranoia; Confused`

### Ilvir (Creation, Ivashu)
- **Bellow of the Aklash (III)**: Shattering sonic roar of the Craven Beast.
  - *Save*: Endurance or Will test.
  - *Effect*: Opponents are **Deafened** for 1d6 hours and must make an immediate **Stumble Roll** to avoid falling prone.
  - *FGU Effect*: `Deafened; Stumble; Prone`
- **Ibenis' Withering (IV)**: Atrophy curse of the Brooder.
  - *Save*: Endurance × 3.
  - *Effect*: Struck limb shrivels into dead wood; becomes permanently **Crippled / Unusable**.
  - *FGU Effect*: `Withered Limb; Crippled`
- **Serpent of the Claw (IV)**: Transmutation into virulent venom.
  - *Save*: Endurance test.
  - *Effect*: Strikes inflict deadly paralytic venom; victim becomes **Stiffened / Paralyzed** within 3 rounds.
  - *FGU Effect*: `Paralytic Venom; Paralyzed`
- **Feat of Albarra (III)**: Bestial physical distortion.
  - *Effect*: Grants monstrous strength and natural claws/bite attacks.
  - *FGU Effect*: `Beast Form; STR: 4; ATK: 15`

### Larani (Honor, Chivalry, War)
- **Courage of Mendiz (II) & Blessing of the Winged Lion (III)**: Valiant celestial mantle.
  - *Effect*: Recipients gain absolute **Immunity to Fear, Dread, and Intimidation**; +20 to Morale tests.
  - *FGU Effect*: `Valiant; IMMUNE: frightened; MORALE: 20`
- **Curse of the Reluctant Warrior (II)**: Rebuke to the dishonorable.
  - *Save*: Will test.
  - *Effect*: Struck with craven cowardice and trembling limbs. Suffers **-20 EML** in combat; forces immediate flight.
  - *FGU Effect*: `Cowardice; Frightened; CHECK: -20`
- **Light of Dolithor (II)**: Radiance of the High Castle.
  - *Effect*: Blinds undead, demons, and creatures of darkness; imposes -40 EML on their strikes.
  - *FGU Effect*: `Holy Radiance; Blinded (Undead)`
- **Knight's Peace (III)**: Sanctuary of the Lady of Paladins.
  - *Effect*: Complete aura of non-violence. All weapons sheathed; hostile actions prevented.
  - *FGU Effect*: `Sanctuary; Pacified`
- **Valamin's Sleep (IV)**: Gentle restorative slumber.
  - *Effect*: Wounded warriors fall into peaceful healing sleep; accelerates recovery from shock and wounds.
  - *FGU Effect*: `Peaceful Sleep; Healing Buff`

### Morgath (Death, Undead, Chaos)
- **Heart of Darkness (II)**: Shroud of ultimate terror.
  - *Save*: Will × 3.
  - *Effect*: Opponents suffer suffocating dread; become **Panicked / Fleeing**; cannot look upon the priest.
  - *FGU Effect*: `Horrified; Frightened; ATK: -20`
- **Necrosy (II)**: Instantaneous putrefactive leprosy.
  - *Save*: Endurance test.
  - *Effect*: Skin rots and sloughs off. Inflicts permanent scarring, loss of Comeliness, and open infected wounds.
  - *FGU Effect*: `Rotting Flesh; Infected; CML: -5`
- **Throat of Klyss (III)**: Spectral strangulation.
  - *Save*: Endurance test.
  - *Effect*: Invisible claws crush victim's trachea. Target is **Asphyxiating / Choked**; unable to speak, cast spells, or breathe.
  - *FGU Effect*: `Strangled; Asphyxiating`
- **Myvria's Kiss (IV)**: Soul drain of the Black Mistress.
  - *Save*: Will test.
  - *Effect*: Drains life force directly; inflicts 2d6 unhealable trauma and places target in **Catatonic Coma**.
  - *FGU Effect*: `Life Drained; Comatose; Incapacitated`

### Naveh (Shadows, Assassination, Night)
- **Dekejis' Gift (II) & Gytevsha's Passage (III)**: Shadow realm passage.
  - *Effect*: Complete **Invisibility and Silence**. Steps make no sound; scent masked; immune to passive detection.
  - *FGU Effect*: `Shadow Cloak; Invisible; SILENCE`
- **Flash from Kamil (III)**: Abrupt blinding detonation.
  - *Save*: Eyesight test.
  - *Effect*: Targets in radius are **Blinded** and disoriented for 2d6 rounds. Attacks at -40 EML; defense at -20 EML.
  - *FGU Effect*: `Blinded; ATK: -40; DEF: -20`
- **Krasula's Pillow (III)**: Nightmare asphyxiation.
  - *Save*: Will test.
  - *Effect*: Target slips from normal sleep into a deep comatose state, suffocating in their own nightmare.
  - *FGU Effect*: `Nightmare Coma; Asleep; Suffocating`
- **Krasula's Whisper (III)**: Seed of paranoia and madness.
  - *Save*: Will × 3.
  - *Effect*: Induces auditory and visual hallucinations; target attacks phantoms or friends in panic.
  - *FGU Effect*: `Hallucinating; Confused; ATK: -20; CHECK: -20`
- **Talons of Gekrish (V)**: The ultimate assassin's coating.
  - *Effect*: Envenoms weapon with Navehan venom; successful hit causes instant **Paralysis** (round 1) and **Death** (round 2) on failed END check.
  - *FGU Effect*: `Lethal Venom; Paralyzed`

### Peoni (Healing, Agriculture, Mercy)
- **Peace of Valon (III)**: The celestial calm of the White Maiden.
  - *Effect*: Aura in which no blood may be shed. Attackers must test Will to even initiate violence.
  - *FGU Effect*: `Aura of Peace; Pacified`
- **Tirrala's Cure (III) & Healing of Gorlan (IV)**: Miraculous divine remedy.
  - *Effect*: Immediately cures all diseases, neutralizes venoms, purifies infections, and clots all bleeders.
  - *FGU Effect*: `Purified; Cured; Bleeding Stopped`
- **Mirytha's Shade (III)**: Refreshing pastoral relief.
  - *Effect*: Clears all Fatigue Levels (FL) and removes dehydration/heatstroke conditions.
  - *FGU Effect*: `Refreshed; Fatigue Removed`

### Sarajin (Battle, Honor, Frost)
- **Spirit of Shalka (III)**: Battle-fury of the Ice Barbarians.
  - *Effect*: Warrior enters sacred **Ivinian Berserk**. Completely ignores shock checks, fatigue, and pain penalties; +20 EML to axe/sword.
  - *FGU Effect*: `Ivinian Berserk; ATK: 20; IGNOREPENALTY`
- **Usnarl's Hug (II)**: Crushing grip of the Great Bear.
  - *Save*: Strength contest.
  - *Effect*: Target is **Grappled & Pinned**; ribs crushed; suffers 2d6 Blunt damage each round held.
  - *FGU Effect*: `Bear Hugged; Restrained; CRUSH: 2d6 B`
- **Njehu's Wind (V) & Njehu's Stir (V)**: Wrath of the Northern Blizzard.
  - *Save*: Endurance test.
  - *Effect*: Freezing blizzard blinds all within area; causes severe Frostbite and **Hypothermia** (-20 EML).
  - *FGU Effect*: `Blizzard Shroud; Blinded; Frostbite; CHECK: -20`
- **Fakang's Edge (V)**: Rime weapon enchantment.
  - *Effect*: Weapon blade covered in sub-zero frost; causes numbing shock and slows opponent's reactions.
  - *FGU Effect*: `Rime Edge; Frost: 1d6 F; INIT: -10`

### Save-K'nor (Knowledge, Riddles, Order)
- **Silence of Uhla (III)**: Vow of holy wordlessness.
  - *Save*: Will test.
  - *Effect*: Target is rendered completely **Mute / Speechless**. Cannot cast verbal spells, shout orders, or speak.
  - *FGU Effect*: `Silenced; Mute; NO_VERBAL`
- **Argenon's Riddle (III)**: The paradox of the Lost Sage.
  - *Save*: Intelligence test.
  - *Effect*: Mind locked in solving an insoluble paradox. Target stands motionless, unable to act or defend (`Stunned / Baffled`).
  - *FGU Effect*: `Baffled; Stunned; DEF: -20`
- **Daemar's Discipline (III)**: Mathematical cognitive tranquility.
  - *Effect*: Immunity to emotional manipulation, fear, and confusion; +10 to all intellectual and ritual tests.
  - *FGU Effect*: `Disciplined; INT: 2; IMMUNE: frightened`

### Siem (Dreams, Astral, Mystery)
- **Curse of Sloth (III)**: The weight of eternal slumber.
  - *Save*: Will test.
  - *Effect*: Target struck with crippling lethargy. Movement rate halved; universal penalty doubled; cannot run.
  - *FGU Effect*: `Lethargic; SPEED: /2; CHECK: -20`
- **Ilsiri Dance (III) & Yael's Calm (III)**: Astral song of the Sindarin.
  - *Save*: Will test.
  - *Effect*: Targets fall into a peaceful **Dreamlike Trance**; mesmerized by swirling lights, laying down weapons.
  - *FGU Effect*: `Dream Trance; Pacified; Docile`
- **Sweldre's Cloak (V)**: Shroud of the Blessed Realm.
  - *Effect*: Caster and allies step sideways into the astral weave; completely invisible and untouchable by physical attacks.
  - *FGU Effect*: `Astral Shroud; Invisible; IMMUNE: all`

---

## 5. FGU Automation & Effect String Master Matrix

Use this master lookup table when creating weapon actions, spell effects, and miracle items in Fantasy Grounds Unity.

| Condition / Status Effect | Category | Primary Mechanical Impact | Engine Keywords & FGU Effect String |
| :--- | :--- | :--- | :--- |
| **Prone** | Physical Combat | -20 EML to attacks/defenses; +20 EML to attackers | `Prone; ATK: -20; DEF: -20` |
| **Stumble** | Physical Combat | Balance lost; forced prone on failure | `Stumble; Prone` |
| **Fumble** | Physical Combat | Drop weapon, shield destroyed, guard dropped | `Fumble` |
| **Bleeder (Bloodloss)** | Physical Trauma | 1 BP accrued per minute; death if BPs > END | `Bleeding: 1 BP/min` |
| **Shock State** | Physical Trauma | Medical state (H5); 4-hr check vs HR×END | `Shock; CHECK: -20` |
| **Unconscious** | Physical Trauma | Helpless; auto-fail checks; attacks strike uncontested | `Unconscious; Prone; DEF: Ignore` |
| **Incapacitated** | Physical / Recovery | Shock transition; -10 penalty on initiative | `Incapacitated; INIT: -10` |
| **Crippled Limb** | Physical Trauma | Arm/Leg unusable until healed to M1 | `Crippled Limb; CHECK: -20` |
| **Amputated** | Physical Trauma | Extremity severed; permanent loss; bleeder | `Amputated; Bleeding: 1 BP/min; CHECK: -30` |
| **Blinded** | Physical / Magic | Vision lost; -40 EML attack / -20 EML defense | `Blinded; ATK: -40; DEF: -20` |
| **Deafened** | Physical / Magic | Hearing lost; auto-fail acoustic awareness | `Deafened; CHECK: -30 hearing` |
| **Fatigued** | Physiological | +1 Universal Penalty per level | Native **FT** Box (+1 per FL) |
| **Encumbered** | Physiological | Speed halved/quartered; physical skill penalties | `Encumbered; CHECK: -10; SPEED: /2` |
| **Infected** | Physiological | Daily test vs HR×END; spreads to adjacent limbs | `Infected; HR: -1` |
| **Diseased** | Physiological | Skill penalties -10 to -30; daily progression | `Diseased; CHECK: -20` |
| **Poisoned** | Physiological | Irritant, paralytic, or lethal progressive decline | `Poisoned; CHECK: -20` |
| **Burning (On Fire)** | Environmental | 1d6 Fire damage per round until extinguished | `Burning: 1d6 F` |
| **Frostbite / Chilled** | Environmental | Shivering, hypothermia, speed halved | `Frostbite; CHECK: -15; SPEED: /2` |
| **Asphyxiating / Drowning** | Environmental | Air deprived; END test per round until death | `Drowning; Asphyxiating` |
| **Frightened / Morale Broken** | Psychological | Panicked; must flee or cower; cannot attack | `Frightened; ATK: -20; DEF: -10` |
| **Berserk / Battle Rage** | Psychological | +20 EML attack; immune to shock/pain; cannot parry | `Berserk; ATK: 20; IGNOREPENALTY` |
| **Tactical Advantage (TA)** | Combat Matrix Outcome | Winner dictates next exchange; +10 to +20 EML | `ATK: 20` |
| **Tactical Disadvantage** | Combat State | Outmaneuvered / off balance; -20 EML on actions | `ATK: -20; DEF: -20` |
| **Fascinated / Mesmerized** | Magic / Psionic | Frozen gazing; cannot make rolls or actions | `Globe of Setath; Fascinated; Stunned` |
| **Distracted** | Magic / Spell | Opponents gain tactical adv; -10 Special Penalty | `Distracted; CHECK: -10; DEF: -10` |
| **Entangled / Restrained** | Magic / Fyvria | Speed 0; -20 EML attacks & defenses | `Entangled; Restrained; ATK: -20; DEF: -20` |
| **Asleep / Slumber** | Magic / Religion | Unconscious slumber; wake on injury or duration | `Asleep; Unconscious; DEF: Ignore` |
| **Charmed / Enamored** | Magic / Religion | Friendly regard; cannot attack caster; compliant | `Charmed; Pacified` |
| **Silenced / Mute** | Magic / Religion | Cannot speak, chant, or cast verbal spells | `Silenced; NO_VERBAL` |
| **Awestruck** | Religion / Common | Frozen in reverence; cannot attack; -20 EML | `Awestruck; Pacified; ATK: -20` |
| **Cursed** | Religion / Common | Misfortune; -15 penalty on all checks | `Cursed; CHECK: -15` |
| **Blessed** | Religion / Common | Divine grace; +10 bonus on all checks | `Blessed; CHECK: 10; ATK: 10` |
| **Enduring** | Religion / Common | Ignores all pain, shock, and fatigue penalties | `Enduring; IGNOREPENALTY` |
| **Invisible** | Magic / Naveh | Cannot be seen; +20 EML stealth/attack; +20 EML defense | `Invisible; ATK: 20; DEF: 20` |
| **Hastened** | Magic / Peleahn | Speed doubled; +20 Initiative; extra action | `Hastened; INIT: 20; SPEED: *2` |
| **Hexed** | Psionics | Next skill or all skills rolled at half EML | `Hexed; CHECK: /2` |
| **Catatonic / Comatose** | Psionic / Magic | Body alive but mind/soul detached; completely helpless | `Catatonic; Incapacitated; DEF: Ignore` |
| **Dispelled** | Magic / Gray | Magical effects suppressed or stripped | `Dispelled` |

---

*Compiled for the HarnMaster 3.5E Fantasy Grounds Unity development environment.*
