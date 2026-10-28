# HarnMaster Status Effects & Conditions Reference

This document provides a reference of status effects, conditions, trauma states, and enchantments in the **HarnMaster 3.5E** ruleset for **Fantasy Grounds Unity (FGU)**.

---

## 1. How Effects Work in HarnMaster 3.5E

In the Fantasy Grounds Unity ruleset, effects applied to characters in the Combat Tracker fall into two categories:

1. **Automated Engine Effects**: Recognized keywords and conditions that the ruleset programmatically parses and applies to attack rolls, defense rolls, ability/skill checks, tactical modifiers, or trauma recovery sequences.
2. **Informational & Descriptive Labels**: Status names or reminder text (such as *Bleeding*, *Burning*, or *Infected*) displayed on tokens and in the Combat Tracker to remind the GM and players of ongoing conditions that require manual tracking or narrative resolution according to tabletop HarnMaster rules.

```
┌─────────────────────────────────────────────────────────────┐
│                    COMBAT TRACKER EFFECT                    │
├──────────────────────────────┬──────────────────────────────┤
│    Automated Engine Tags     │    Informational Labels      │
│  (ATK, DEF, CHECK, Prone,    │   (Bleeding, Burning,        │
│   Invisible, Unconscious)    │    Infected, Diseased)       │
├──────────────────────────────┼──────────────────────────────┤
│ Applied directly to rolls,   │ Visual widget & GM reminder; │
│ EML calculations & saves.    │ resolved manually per round. │
└──────────────────────────────┴──────────────────────────────┘
```

---

## 2. Automated Engine Effects & Keywords

### A. Core Supported Conditions

These conditions are registered in the ruleset engine (`DataCommon.conditions`) and have direct mechanical automation or dedicated token status icons:

| Condition | In-Game Mechanical Automation | Token Icon |
| :--- | :--- | :--- |
| **Prone** | Attacker: suffers disadvantage / penalty on attacks. Target: standing attackers gain tactical advantage; prone defenders suffer penalty on defense. | `cond_prone` |
| **Invisible** | Grants `ADVATK` (+20 EML tactical advantage) to attacks. Attackers without special awareness suffer tactical disadvantage against the invisible target. | `cond_invisible` |
| **Blinded** | Imposes `DISATK` (-20 EML penalty) on all attack rolls. | `cond_blinded` |
| **Frightened** | Imposes `DISATK` on attack rolls and `DISCHK` on ability/skill checks. | `cond_frightened` |
| **Intoxicated** | Imposes `DISATK` on attack rolls and `DISCHK` on ability/skill checks. | — |
| **Poisoned** | Imposes `DISATK` on attack rolls and `DISCHK` on ability/skill checks. | `cond_sickened` |
| **Restrained** / **Grappled** | Imposes `DISATK` on attacks and limits mobility. | `cond_restrained` / `cond_grappled` |
| **Paralyzed** / **Petrified** | Actor is frozen and incapable of making physical attacks or actions. | `cond_paralyzed` |
| **Stunned** | Actor cannot initiate offensive actions; defense rolls penalized. | `cond_stunned` |
| **Unconscious** | Helpless state. Automatically drops Prone. Defenses cannot be mounted (uncontested hits). Governs the automated Shock Recovery system. | `cond_unconscious` |
| **Incapacitated** | Transitional trauma state between Unconscious and Shock or full recovery. Automatically rolls shock checks on recovery. | `cond_paralyzed` |
| **Shock** | Critical medical trauma state (Healing Rate H5). Triggers 4-hour recovery cycles. | `cond_paralyzed` |
| **Surprised** | Tactical surprise state. | `cond_disadvantage` |
| **Deafened** | Informational condition tag; acoustic awareness checks penalized. | `cond_deafened` |
| **Charmed** | Informational condition tag; social/allegiance tracking. | `cond_charmed` |
| **Cursed** | Informational condition tag; can be paired with `CHECK: -10`. | `cond_sickened` |
| **Encumbered** | Informational condition tag; physical skills penalized. | `cond_encumbered` |
| **Stable** | Trauma stabilization state. | — |
| **Bleeding** / **Bleed** | Informational condition tag for bloodloss tracking. | `cond_bleed` |

---

### B. Numerical Modifier Keywords

Fantasy Grounds evaluates effect strings containing numerical components using the format `TAG: [number]`. The following modifier tags are active in the HarnMaster 3.5E ruleset:

| Keyword Syntax | Affected Rolls | Description | Example |
| :--- | :--- | :--- | :--- |
| `ATK: [n]` | Melee & Ranged Attacks | Adds or subtracts flat EML from attack rolls. | `ATK: 20` or `ATK: -10` |
| `@ATK: [n]` | Incoming Attacks | Modifies incoming attacks against the targeted actor. | `@ATK: -20` |
| `DEF: [n]` | Defense Rolls | Adds or subtracts flat EML from Dodge, Block, or Counterstrike rolls. | `DEF: -20` or `DEF: 10` |
| `CHECK: [n]` | Ability & Skill Checks | Adds or subtracts flat EML from general skill and attribute checks. | `CHECK: -15` |
| `INIT: [n]` | Initiative | Modifies the calculated initiative roll for the actor. | `INIT: -10` or `INIT: 20` |
| `[ATTR]: [n]` | Specific Attributes | Flat modifier to specific HarnMaster attributes (`STR`, `DEX`, `AGL`, `END`, `WIL`, `AUR`, `INT`, `EYE`, `HRG`, `SML`, `VOI`, `CML`, `MOR`, `STA`). | `STR: 2; END: 1` |

> [!NOTE]
> Numerical modifiers in FGU effect strings must always be flat integers (e.g. `CHECK: -20`). Formula expressions, percentages, or division operators like `CHECK: /2` or `SPEED: /2` are **not supported** by the FGU effect parser.

---

### C. Tactical & Conditional Effect Tags

| Keyword Tag | Mechanical Behavior in Ruleset |
| :--- | :--- |
| `ADVATK` / `@ADVATK` | Forces Tactical Advantage (+20 EML) on attacks. |
| `DISATK` / `@DISATK` | Forces Tactical Disadvantage (-20 EML) on attacks. |
| `GRANTADVATK` | Any attacker targeting this actor gains Tactical Advantage (+20 EML). |
| `GRANTDISATK` | Any attacker targeting this actor suffers Tactical Disadvantage (-20 EML). |
| `ADVCHK` / `DISCHK` | Grants advantage or disadvantage on skill and ability checks. |
| `ADVINIT` / `DISINIT` | Grants advantage or disadvantage on initiative rolls. |
| `COVER` / `SCOVER` / `FULLCOVER` | Applies standard cover modifiers to defense and ranged targeting. |
| `SIZE: <1ft` to `SIZE: 16-32ft` | Ranged size modifier tags (from -20 to +20 EML) when targeting creatures of non-human scale. |

---

## 3. Trauma & Recovery System Automation

HarnMaster 3.5E features automated state progression for trauma checks (Shock Rolls) triggered by injury or recovery:

```
                      ┌──────────────────────┐
                      │   Suffers Injury     │
                      └──────────┬───────────┘
                                 │
                                 ▼
                      ┌──────────────────────┐
                      │     Shock Roll       │
                      │  (1d6 per UP vs END) │
                      └──────────┬───────────┘
                                 │
                     ┌───────────┴───────────┐
                     ▼                       ▼
                 [Pass]                   [Fail]
             No change in              Collapses:
             consciousness           ┌───────────────────────────────┐
                                     │ • Effect: "Unconscious"       │
                                     │ • Effect: "Prone"             │
                                     │ • Defenses: Uncontested       │
                                     └───────────────┬───────────────┘
                                                     │
                                                     │ 1-minute / 10-minute
                                                     │ Recovery Roll
                                                     ▼
                                     ┌───────────────────────────────┐
                                     │     Recovery Shock Roll       │
                                     └───────────────┬───────────────┘
                                                     │
                                     ┌───────────────┴───────────────┐
                                     ▼                               ▼
                                  [Pass]                          [Fail]
                         Transition to Recovery:            Remains Unconscious
                         ┌─────────────────────────┐
                         │ • Removes Unconscious   │
                         │ • Effect: Incapacitated │
                         │ • Immediate Shock Check │
                         └───────────┬─────────────┘
                                     │
                     ┌───────────────┴───────────────┐
                     ▼                               ▼
                  [Pass]                          [Fail]
          Full Recovery from Shock:         Degrades into Deep Shock:
          ┌───────────────────────┐         ┌─────────────────────────┐
          │ Removes Incapacitated │         │ • Removes Incapacitated │
          │ Returns to action     │         │ • Effect: "Shock"       │
          └───────────────────────┘         │ • Healing Rate H5 state │
                                            └─────────────────────────┘
```

* **Unconscious**: Applied automatically when failing a Shock roll. The character collapses (`Prone; Unconscious`), drops weapons, and cannot make defense rolls (opponents make uncontested strikes).
* **Incapacitated**: Applied automatically when passing an Unconscious recovery roll. Triggers an immediate follow-up Shock check. If passed, the character recovers completely; if failed, the character degrades into medical **Shock**.
* **Shock**: Represents the critical physiological shock state (HarnMaster Healing Rate H5). Requires medical intervention and daily 4-hour recovery rolls (`HR × END`).

---

## 4. Physical Combat & Tabletop Conditions Reference

The table below outlines common tabletop conditions, noting their actual rule mechanics and the corresponding valid FGU effect syntax:

| Condition | HarnMaster Rule Mechanics | FGU Implementation & Effect String | Automation Level |
| :--- | :--- | :--- | :--- |
| **Prone (Knockdown)** | Character on ground. -20 EML to attacks and defenses. Standing foes gain +20 EML. Costs movement to stand. | `Prone; ATK: -20; DEF: -20` | **Automated** (via `Prone` condition & flat modifiers) |
| **Stumble** | Failed Agility test from knockback or leg injury. Character drops Prone. | `Prone; ATK: -20; DEF: -20` | **Automated** (apply Prone) |
| **Fumble** | Dropped weapon or lost guard from critical failure or arm injury. | Narrative resolution; disarm/drop weapon | **Manual** |
| **Bleeder (Bloodloss)** | Grievous wound generates 1 Bloodloss Point (BP) per minute. Exsanguination if BPs exceed Endurance. | `Bleeding` (shows `cond_bleed` icon) | **Informational** (tracked via Injuries tab / manual BPs) |
| **Crippled Limb** | G4/G5 extremity injury. Limb unusable until healed to M1. | `CHECK: -20` (applied to affected limb skills) | **Semi-Automated** (flat modifier) |
| **Blinded (Complete)** | Both eyes destroyed or blinded by flash/magic. -40 EML attack, -20 EML defense. | `Blinded; ATK: -40; DEF: -20` | **Automated** |
| **Deafened** | Loss of hearing from trauma or blast. Acoustic awareness fails automatically. | `Deafened; CHECK: -30` | **Semi-Automated** (shows icon; check penalty applies) |
| **Fatigue (FL)** | Exertion or heavy armor. Each level adds +1 to Universal Penalty (UP). | Native **FT** box on character sheet / CT | **Automated** (native engine counter) |
| **Encumbered** | Load exceeds capacity. Movement halved; physical skills penalized. | `Encumbered; CHECK: -10` | **Semi-Automated** |
| **Infected** | Wound fails 5-day healing roll. Evaluated daily on Infection Table. | `Infected` | **Informational** (GM tracks daily HR progression) |
| **Diseased** | Pathogen exposure. Causes fever, chills, or weakness (-10 to -30 penalty). | `Diseased; CHECK: -20` | **Semi-Automated** |
| **Poisoned** | Venom exposure (irritant, paralytic, or lethal). | `Poisoned; CHECK: -20; ATK: -20` | **Automated** (applies disadvantage/penalties) |
| **Burning (On Fire)** | Character on fire. Takes 1d6 Fire damage each round until extinguished. | `Burning` | **Informational** (GM rolls 1d6 F damage on turn) |
| **Frightened / Morale Broken** | Failed morale check. Must flee or surrender; cannot initiate attacks. | `Frightened; ATK: -20; DEF: -10` | **Automated** (forces disadvantage & attack penalties) |
| **Tactical Advantage (TA)** | Won combat exchange or tactical position. +20 EML on next strike. | `ATK: 20` | **Automated** |
| **Tactical Disadvantage** | Outmaneuvered or poor footing. -20 EML on next action. | `ATK: -20; DEF: -20` | **Automated** |

---

## 5. Supernatural Powers & Spells Effect Configuration

When configuring spell action sets, psionic powers, or divine miracles in Fantasy Grounds Unity, use these standard effect strings:

### Arcane Magic (*Shek-Pvar*)
* **Globe of Setath (Savorya / Mind)**:
  * *Critical/Marginal Failure on Save*: `Stunned; DEF: -20`
  * *Marginal Success on Save*: `CHECK: -10; DEF: -10`
* **Invisibility (Lyahvi / Air & Light)**:
  * `Invisible` *(automatically applies tactical advantage to attacker and disadvantage to foes)*
* **Flesh of Stone / Earth Armour (Fyvria / Earth)**:
  * Armor protection bonuses are configured directly on the hit location or item record.
* **Haste / Quickening (Peleahn / Fire)**:
  * `INIT: 20; ATK: 10`
* **Web / Entanglement (Fyvria / Earth)**:
  * `Restrained; ATK: -20; DEF: -20`
* **Slumber / Deep Sleep (Savorya / Mind)**:
  * `Unconscious; Prone`

### Divine Invocations & Miracles
* **Blessing / Divine Favor (Common)**:
  * `Blessed; CHECK: 10; ATK: 10`
* **Curse / Malison (Common)**:
  * `Cursed; CHECK: -10; ATK: -10`
* **Holy Radiance / Awe (Larani / Honor & War)**:
  * `Awestruck; ATK: -20`
* **Battle Fury (Sarajin / Battle & Frost)**:
  * `Berserk; ATK: 20` *(GM manually ignores pain/shock checks)*
* **Sanctuary / Pacification (Peoni / Mercy & Healing)**:
  * `Sanctuary; DEF: 20`
* **Silence (Save-K'nor / Order & Riddles)**:
  * `Silenced` *(narrative/informational; prevents verbal casting)*

---

## 6. Master FGU Effect Syntax Cheat Sheet

Use this quick-reference table when building character sheets, NPC actions, and item effects in Fantasy Grounds Unity:

| Desired Mechanical Result | Valid FGU Effect String | Notes |
| :--- | :--- | :--- |
| **Attack Bonus** | `ATK: 20` | Adds +20 EML to attack rolls |
| **Attack Penalty** | `ATK: -20` | Subtracts 20 EML from attack rolls |
| **Defense Bonus** | `DEF: 20` | Adds +20 EML to Dodge/Block/Counterstrike |
| **Defense Penalty** | `DEF: -20` | Subtracts 20 EML from Dodge/Block/Counterstrike |
| **General Skill / Check Bonus** | `CHECK: 10` | Adds +10 EML to all attribute and skill checks |
| **General Skill / Check Penalty** | `CHECK: -15` | Subtracts 15 EML from all attribute and skill checks |
| **Initiative Modifier** | `INIT: 10` or `INIT: -10` | Adjusts initiative roll |
| **Tactical Advantage on Attacks** | `ADVATK` | Forces tactical advantage on attack rolls |
| **Tactical Disadvantage on Attacks** | `DISATK` | Forces tactical disadvantage on attack rolls |
| **Attacker Advantage Against Target** | `GRANTADVATK` | Anyone attacking this target gains tactical advantage |
| **Full Cover** | `FULLCOVER` | Applies full cover modifiers against ranged attacks |
| **Target Scale (Tiny to Huge)** | `SIZE: <1ft` to `SIZE: 16-32ft` | Modifies ranged attack EML based on target size |
| **Knockdown / Prone** | `Prone; ATK: -20; DEF: -20` | Standard prone combat state |
| **Complete Blindness** | `Blinded; ATK: -40; DEF: -20` | Standard blindness combat state |
| **Unconscious Collapse** | `Unconscious; Prone` | Marks character helpless; triggers shock recovery |
| **Shock Recovery State** | `Incapacitated` | Triggers shock check upon recovery |
| **Critical Trauma State** | `Shock; CHECK: -20` | Critical medical state (H5) |
| **Bloodloss Marker** | `Bleeding` | Displays bleed token icon; tracked manually |
| **Fire Hazard Marker** | `Burning` | Reminder tag; GM rolls 1d6 F damage per round |

---
*Reference manual compiled for the HarnMaster 3.5E ruleset on Fantasy Grounds Unity.*
