# HarnMaster 3.5E for Fantasy Grounds — User Manual

## Introduction

This manual covers the Fantasy Grounds Unity implementation of **HarnMaster 3.5E**. It focuses on how to use the software — what each button does, how the roll sequence works, and how data is laid out — rather than repeating the tabletop rules. Keep your HarnMaster rulebook handy for the underlying mechanics.

---

## The Character Sheet

The character sheet header always displays the character's name and a prominent **UP / PP** indicator:
* **UP (Universal Penalty)**: Cumulative penalty from open wounds and active fatigue levels (1 per wound + 1 per fatigue). Automatically penalizes all percentile skill and attack/defense rolls by -5 EML per UP point, and adds dice to Shock and Death tests.
* **PP (Physical Penalty)**: Combined penalty of Universal Penalty plus Encumbrance Penalty (`UP + Encumbrance`). Applies to physical tests, movement, fumbles, and stumbles.

The character sheet has six tabs:

| Tab | Contents |
|---|---|
| **Skills** | Attributes and skills, ML, SB calculations, and development rolls |
| **Powers** | Convocations, rituals, invocations, and psionics with power groups, actions, and general rolls |
| **Inventory** | Carried items, currencies, armor equipping, and encumbrance load/penalty calculation |
| **Combat** | Penalties summary (Fatigue, UP, PP), detailed injury list, and worn strike location armor map (B/E/P/F) |
| **Actions** | General combat action rolls (Shock, Stumble, Fumble, Location), weapons, aim zones, and range brackets |
| **GM** | Biographical background, appearance, social class, and birthdate/sunsign (GM-only) |

---

### Skills Tab — Attributes {#skills-tab-attributes}

The top portion of the Skills tab always shows the character's fifteen attributes in a compact grid.

**Main view (compact):** Each row shows the attribute abbreviation and its **Total** score — the final value used in play. Click the roll button to make an attribute roll. The roll can be adjusted using the Modifier Box (see below).

**Attribute Editor (detail popup):** Click the **Details** button (top-right of the ATTRIBUTES header) to open the attribute editor in a separate window. Each row there shows:

| Column | Meaning |
|---|---|
| **Name** | Full attribute name |
| **Base** | The raw value set during character creation — editable |
| **Mod.** | A flat bonus (from species, magic, etc.) — editable |
| **Total** | Computed final value (Base + Mod.) — read-only |

---

### Skills Tab {#skills-tab}

Below the attributes, the same tab shows the character's skill list in compact form.

**Main view (compact):** Each row shows:

| Column | Meaning |
|---|---|
| **Name** | Skill name (with speciality appended if set) |
| **SB** | Skill Base — computed from the linked attributes |
| **ML** | Mastery Level — the number rolled against; click to roll |

Skills are grouped by skill group (Physical, Combat, etc.). Use the filter box at the bottom to search by name.

**Rolling a skill:** Click the roll button on the right of any skill row to send the roll to chat.

**Detailed Skills Window:** Click the **Details** button (top-right of the SKILLS header) to open the full skill editor in a wider popup window. Each row there shows all fields:

| Column | Meaning |
|---|---|
| **Name** | Skill name |
| **Speciality** | Optional specialization within the skill |
| **Skill Group** | Category (Physical, Combat, Crafts & Lore, etc.) |
| **Attributes** | The attributes the SB is derived from (up to three) |
| **Sunsigns** | Sunsign bonus value (if applicable) |
| **OML** | Opening Mastery Level — the initial ML at skill acquisition |
| **SB** | Skill Base — computed, read-only |
| **Dev.** | Development ranks added through play — editable |
| **ML** | Mastery Level — computed final value |

The detailed window also has a **Development Roll** button per row (the dice icon next to ML). Use this to test whether the skill improves.

---

### Powers Tab — Magic, Invocations & Psionics {#powers-tab-magic-invocations-psionics}

The **Powers** tab manages all supernatural and mental disciplines in HarnMaster: Arcane Magic (Shek-Pvar), Clerical Miracles (Invocations & Rituals), and Psionic Talents.

#### Top Panels: Penalties & General Actions
* **Penalties Bar**: Displays active Fatigue, Universal Penalty (UP), and Physical Penalty (PP) directly at the top of the powers tab.
* **Collapsible Actions Header**: Clicking the **ACTIONS** header expands or collapses quick-roll buttons for **Shock**, **Stumble**, **Fumble**, and **Strike Location**, making emergency saves and tactical reactions immediately accessible without switching tabs.

#### Power Traditions & Group Types

Characters organize abilities into customizable **Power Groups** via the group detail window:
- **Group Settings**: Configure group display name, caster type, linked base skill (e.g., Convocation skill, Ritual skill, or Psionic talent), attack attribute, preparation mode, and Piety pool.
- **Arcane Magic (Shek-Pvar)**: Standard Harnic magic divided into Gray (Neutral) mysteries and six elemental Convocations:

| Tradition / Convocation | Element / Focus | Spells & Scope |
|---|---|---|
| **Gray (Neutral)** | Fundamental / Common | 22 universal spells (*Dispell*, *Maintain*, *Ward*, *Soul Stealer*, *Attune*, *Arwyn's Bubble*, etc.) |
| **Fyvria** | Earth / Nature | 10 spells governing flora, fauna, natural healing, and earth spirits (*Balm of Gresan*, *Verdant Hand*, etc.) |
| **Jmorvi** | Metal / Craft | 10 spells governing minerals, metallurgy, enchanting, and kinetics (*Aspect of Tarus*, *Fist of Kuhan*, etc.) |
| **Lyahvi** | Light / Air | 10 spells governing optical illusions, color, invisibility, and atmosphere (*Cloak of Kalaerin*, *Globe of Setath*, etc.) |
| **Odivshe** | Water / Cold | 10 spells governing ice, permafrost, darkness, liquid forms, and stealth (*Breath of Dhivu*, *Shadow of Yanar*, etc.) |
| **Peleahn** | Fire / Heat | 10 spells governing thermal energy, pyrotechnics, smoke, and bodily heat (*Sea of Fire*, *Skin of Lexesh*, etc.) |
| **Savorya** | Mind / Spirit | 10 spells governing telepathy, clairvoyance, memory, and cognitive shielding (*Aron's Thought*, *Spirit Block*, etc.) |

- **Divine Religion (Invocations & Rituals)**:
  - Tracks divine favor via **Piety Points** (`Piety / Max Piety`).
  - Covers Common Church Rituals and domain-specific miracles across the pantheon (Agrik, Halea, Ilvir, Larani, Morgath, Naveh, Peoni, Sarajin, Save-K'nor, Siem).
  - Casting invocations consumes Piety points; failed tests or transgressions track divine displeasure.
- **Psionics & Esoteric Talents**:
  - Innate mental disciplines rolled against specific Talent ML.
  - Psionic exertion inflicts direct Fatigue on the caster and triggers psionic shock tests upon critical failures.

#### Power Action Types & Automation Engine

Each power entry supports embedded interactive action rows:
- **Cast Action**: Rolls against the caster's linked Convocation, Invocation, or Psionic skill ML. Automatically outputs the Degree of Success (**CS**, **MS**, **MF**, **CF**).
- **Degree of Success (DoS) Synchronization**: The result of the Cast roll automatically propagates to child actions and synchronizes sibling action rows (`cycler_power_dos`), allowing spell damage, saving throw DCs, and secondary effects to adapt dynamically to Critical vs. Marginal casting outcomes.
- **Fatigue Cost Automation**: Automatically increments character fatigue (`hp.fatigue`) upon casting (e.g. 1 FT for standard spells, doubled on failures or heavy castings), feeding directly into the Universal Penalty.
- **Six Modular Action Types**:
  1. **Cast**: Evaluates spell success and initiates the casting sequence.
  2. **Attack**: Opposed melee/ranged spell attack rolls that integrate directly with the Combat Resolution Window (CRW).
  3. **PowerSave (Saving Throw)**: Prompts targets for attribute-based saves (STR, DEX, CON/STA, INT, WIL, AUR) with DC scaling and 4-degree resolution (CS, MS, MF, CF).
  4. **Damage**: Rolls spell impact dice filtered by degree of success, applying damage aspect (Blunt, Edge, Point, Fire, Frost) and matrix multipliers.
  5. **Heal**: Interactive healing actions that reduce injury levels or remove bleeding conditions.
  6. **Effect**: Applies targeted HarnMaster conditions, wards, or buffs (e.g., `Blinded`, `Invisible`, `Prone`, `Hastened`) directly to tokens in the Combat Tracker.
- **Detail View**: Full reference popup displaying complexity level, fatigue cost, casting time, range, duration, target types, and bonus effects.

---

### Inventory Tab {#inventory-tab}

The Inventory tab lists all items carried, monetary wealth, and encumbrance calculations:

#### Carried Items & Armor Equipping
* **Count / Name / Location**: Quantity, item name, and stowage location.
* **Weight**: Total weight calculated as `Count × Unit Weight`.
* **Carried State**: Click the carried state icon to toggle between:
  * **Not Carried** (stored in camp/mount; ignored for weight)
  * **Carried** (stowed in backpack or sack; counts toward carried load)
  * **Equipped** (worn armor, clothing, or drawn weapons; automatically feeds protection into the strike location armor table)

#### Encumbrance Section
Encumbrance is calculated dynamically using character physical attributes:
* **Base Calculation**: Average physical prowess computed as `(STR + STA + WIL) / 3`.
* **Equipped Load & Carried Load**: Displays rounded total weights for equipped items and carried gear.
* **Total Load**: Sum of all carried and equipped weight.
* **Penalty Base Cycler**: Toggle between **Equipped** (standard Harnic armor-only encumbrance in combat) and **Carried** (total pack load).
* **Penalty**: Computed as `round(Load / Base)`. Feeds directly into **Physical Penalty (PP)**, penalizing physical skills and movement by -5 EML per step.

---

### Combat Tab — Armor & Penalties {#combat-tab-armor-penalties}

The Combat tab summarizes three key systems:

1. **Strike location armor** — The strike location table showing B/E/P/F protection values per body location. See [Combat Tab — Strike Locations](#combat-tab-strike-locations) below.
2. **Penalties list** — A summary of active injury penalties feeding into Universal Penalty and Physical Penalty.
3. **Injury list** — All current wounds. See [Combat Tab — Injuries](#combat-tab-injuries) below.

---

### Combat Tab — Injuries & Medical Resolution {#combat-tab-injuries}

Injuries are listed as a sub-panel on the Combat tab:
* **Compact Row**: Shows the injury description, aspect, and Injury Level (IL: 1–5).
* **Two-Step Delete**: Built-in delete control allows safe wound clearing.

#### Detailed Injuries Window & Medical Resolution
Clicking the **Details** button on the INJURIES header opens the expanded **Detailed Injuries Window** (`charsheet_injuries_detailed`):

| Column / Control | Meaning |
|---|---|
| **Location / Description** | Body part affected and descriptive wound name (e.g. *Bruised*, *Grievous Cut*) |
| **Aspect** | Blunt, Edge, Point, Fire, or Frost |
| **IL (Injury Level)** | 1 to 5 (Minor = 1, Serious = 2–3, Grievous = 4–5) |
| **HR (Healing Rate)** | Days per healing step |
| **Date Incurred** | Calendar date formatted via Tuzyn Calendar (e.g. *24th Kelen*) |
| **Notes** | Free-text clinical notes |
| **Treat Button (Roll)** | Opens the interactive **Medical Resolution Window (MRW)** for treatment, diagnosis, and surgical interventions |
| **Heal Button (Roll)** | Performs standard medical healing check progression |

#### Interactive Medical Resolution Window (MRW)
The dedicated Medical Resolution Window guides physicians and GMs through official HarnMaster medical procedures:
* **Diagnosis**: Diagnostic roll establishing bonus modifier for treatment.
* **Treatment**: Applies medical treatment, adjusting wound status from Untreated to Tended/Treated and improving Healing Rate (HR).
* **Healing Cycle**: Resolves 5-day healing intervals, testing condition and reducing Injury Levels upon success.
* **Infection Day**: Daily infection checks for open, dirty, or untreated wounds.
* **Shock Watch**: 4-hour watch recovery tests for characters in critical medical Shock.
* **Cauterization & Tourniquet**: Emergency field procedures to staunch active Bleeders.
* **Surgical Amputation**: Amputation resolution for non-viable limbs.
* **Bloodloss**: Tracking active bleeders and cumulative bloodloss points.

---

### Combat Tab — Strike Locations {#combat-tab-strike-locations}

Located below the injuries sub-panel, the **Strike Locations** section displays the character's body map and armor protection:

| Column | Meaning |
|---|---|
| **Strike Locations** | Body location name (Skull, Face, Neck, Thorax, Shoulders, Arms, Hands, Abdomen, Groin, Hips, Legs, Feet) |
| **B / E / P / F** | Total armor protection at that location for Blunt, Edge, Point, and Fire |
| **Cover** | Cover rating status (e.g. low wall, shield cover, or fortifications) providing additional protective mitigation |

During combat resolution, the system rolls against this table (or High/Low aim sub-tables) to determine exactly where a hit lands and automatically applies the corresponding armor and cover mitigation.

---

### Actions Tab — Weapons & General Actions {#actions-tab-weapons}

The Actions tab is the primary interface for combat rolls and quick emergency saves.

#### General Actions Panel
At the top of the Actions tab, the **ACTIONS** panel provides one-click rolls for essential combat reactions:
* **Shock**: Performs an immediate System Shock roll. Roll uses `math.max(1, UP)` d6 vs. the character's Endurance (or Condition skill/5).
* **Stumble**: Rolls 3d6 (plus physical penalty) vs. Agility. Failure causes the character to fall **Prone** and adds the condition to the Combat Tracker.
* **Fumble**: Rolls 3d6 (plus physical penalty) vs. Dexterity. Failure drops held weapons or shields.
* **Strike Location**: Performs a strike location roll against the default Harnic hit location table and announces the struck body part.

#### Weapon Row Controls

Weapon entries can be reordered in the list by dragging them to the desired position.

| Control | Function |
|---|---|
| **Name** | Weapon or attack name (underlined; click to rename) |
| **Attack (Sword icon)** | Click to make an attack roll; displays current effective **AML** |
| **Defend (Shield icon)** | Click to make a defense roll; displays current effective **DML** |
| **Damage (Fist icon)** | Click to roll damage; displays dice for the active aspect |
| **Damage Aspect** | Cycles between **Blunt**, **Edge**, and **Point** |
| **Aim Zone** | Cycles between **High** (-10 EML), **Mid** (default), and **Low** (-10 EML) |
| **Range Bracket** | Current range band for ranged/thrown weapons: **Short** (+10), **Medium** (0), **Long** (-20), **Extreme** (-40) |
| **Ammo Counter** | Tracks remaining ammunition with an interactive pip display |

#### Weapon Editor (Detail Popup)

Click the **detail button** (grid icon, right side of each weapon row) to configure weapon stats:

| Field | Meaning |
|---|---|
| **Weapon** | Display name |
| **WQ / Current** | Base Weapon Quality and current condition rating |
| **Note** | Free-text notes (e.g. ammo type, special rules) |
| **Type** | *Melee*, *Ranged*, or *Thrown* |
| **Skill** | Base weapon skill used for ML calculation |
| **A / D / HM** | Attack modifier, Defense modifier, and Handmode penalty |
| **B / E / P** | Base damage dice for Blunt, Edge, and Point aspects |
| **Range S/M/L/E** | Range thresholds in metres for each bracket |
| **Properties** | Notes on special qualities or magical attributes |

#### Adding Attack Entries

Right-click anywhere in the weapon list to access the radial menu:

- **Add Melee** — Adds a melee weapon entry
- **Add Ranged** — Adds a ranged weapon entry
- **Add Throwing** — Adds a thrown weapon entry

---

### GM Tab — Background {#gm-tab-background}

The GM tab is visible only to the GM and tracks character background:

- **Birthdate**, **Sunsign**, **Sunsign (Cusp)**
- **Species**, **Gender**
- **Height**, **Frame**, **Weight**
- **Hair Color**, **Eye Color**, **Voice**
- **Culture**, **Social Class**
- **Speed** (calculated from MOV)

Sunsign affinities automatically grant bonuses to matching skills on the Skills tab.

---

## Making Rolls

All rolls in HarnMaster follow a percentile (d100) test compared against the target Mastery Level (ML):

| Result | Meaning |
|---|---|
| **Critical Success (CS)** | Roll ≤ ML ending in 5 or 0 |
| **Marginal Success (MS)** | Roll ≤ ML (or natural 01–05) |
| **Marginal Failure (MF)** | Roll > ML (or natural 96–00) |
| **Critical Failure (CF)** | Roll > ML ending in 5 or 0 |

How to roll:

- **Attribute check**: Click the roll button next to an attribute on the Skills tab
- **Skill check**: Click the roll button on the Skills tab
- **Attack**: Click the sword button on the Actions tab
- **Defense**: Click the shield button
- **Damage**: Click the damage button
- **Saves & Reactions**: Click the Shock, Stumble, Fumble, or Location roll buttons

### The Modifier Box

The **Modifier Box** is a floating desktop panel that applies situational modifiers to the next roll:

- **Numeric modifier**: Type any number or click the `+2`, `-2`, `+5`, `-5` buttons to apply flat bonuses or penalties.
- **SB Multipliers (×2 through ×7)**: Multiplies Skill Base for difficulty scaling on attribute and skill checks:

| Preset | Target Difficulty |
|---|---|
| **×2** | Target = SB × 2 (Very Hard) |
| **×3** | Target = SB × 3 (Hard) |
| **×4** | Target = SB × 4 (Moderate) |
| **×5** | Target = SB × 5 — **Default** (Standard) |
| **×6** | Target = SB × 6 (Easy) |
| **×7** | Target = SB × 7 (Trivial) |

For **damage rolls**, multiplier buttons multiply the number of damage dice rolled together (e.g. `x2` rolls 2d6).

#### Tactical & Situational Preset Modifiers
The Modifier Box includes built-in HarnMaster tactical buttons:
* **DEF_COVER (Low Cover)**: -10 EML to incoming attacks; strikes landing on covered zones hit plate obstacle (B6/E10/P6/F2).
* **DEF_SCOVER (High Cover)**: -20 EML; arrow slits / firing ports.
* **DEF_TCOVER (Full Cover)**: Complete barrier; all strikes hit the obstacle.
* **DEF_PRONE**: Applies -15 EML against ranged attacks (reduced silhouette) and -20 EML when defending in melee, while granting melee attackers +20 EML against the prone target.
* **ATT_OPP (Opportunity)**: Attack of opportunity modifiers.

---

## Combat

Combat resolves in three distinct steps: **Attack → Defense → Damage**.

### Initiative

- Right-click a combatant in the **Combat Tracker** and select **Set Initiative**.
- Use **Set All Initiatives**, **Set NPC Initiatives**, or **Set PC Initiatives**.

### Attack

1. Click the **sword button** on the Actions tab.
2. The attack roll posts to chat with the AML, d100 roll, and outcome (CS/MS/MF/CF).
3. **Aim Zones**: Set the Aim Zone (**High**, **Mid**, **Low**) prior to rolling. High/Low aim zones apply a -10 EML modifier. If an attacker is prone, high aim zones are out of reach.
4. **Creature Size Modifiers**: Attacking a creature of a different size step automatically applies a ±10 EML modifier per step difference (e.g. larger targets are easier to hit; smaller targets harder).

### Defense

The defender responds by choosing one of four tactical actions:

| Defense | Effect |
|---|---|
| **Block** | Uses weapon/shield defense ML to deflect the attack |
| **Counterstrike** | Attacks in return; both rolls resolve simultaneously |
| **Dodge** | Uses Agility-based dodge to evade |
| **Ignore** | Takes no action; attack resolves at maximum effectiveness |

Defenders suffering from the **Prone** condition suffer a **-20 EML** penalty on defense rolls.

### Damage

The attacker rolls damage via the **damage button** according to the active aspect (Blunt, Edge, Point):
* Base damage dice are modified by the weapon rating.
* **Creature Size Difference Impact**: Physical impact is automatically adjusted by ±1 point per size step difference between attacker and defender.
* When targeting a combatant with an open Combat Resolution Window, rolling damage automatically updates the resolution window.

### Shock & Kill (Death) Rolls

Taking an injury automatically triggers a Shock Roll:
* **Shock Pool**: Rolls `1d6` per point of Universal Penalty (UP). If the total rolled exceeds the character's **Endurance** (or Condition skill / 5), the roll fails.
* **Kill Rolls (Death Tests)**: Severe or lethal damage triggers a Kill roll using the same UP dice pool vs. Endurance. Failing the Kill roll immediately applies the **Dead** condition.

| Current State | Roll Outcome | Resulting State |
|---|---|---|
| **Normal** | Fail | → **Unconscious** + **Prone** |
| **Unconscious** | Pass | → **Incapacitated** + immediate second check |
| **Incapacitated** | Fail | → **Shock** (Medical critical state) |
| **Incapacitated** | Pass | → Conditions removed (Recovered) |

---

## Game Master Guide

### The Combat Tracker

Key HarnMaster features on the Combat Tracker:

- **Locations**: Quick access to strike location tables and current armor values
- **Injuries**: Summary of active wounds and current penalty total
- **Fatigue (FT)**: Inline fatigue tracking

**Running combat from the Combat Tracker:**

- **Set initiative**: Set initiative and sort the tracker list.
- **Select active combatant**: Click their token or tracker entry to activate.
- **Target opponent**: Drag the target crosshair to link attacker to defender.
- **Roll directly**: Use weapon buttons on the CT entry to roll attack and damage directly without opening the full sheet.

---

### Combat Resolution

Combat interactions (attack vs. defense, hit location determination, armor mitigation, and injury generation) are resolved using the dedicated **Combat Resolution Window**.

👉 **For complete details and a step-by-step walkthrough, see the [Combat Resolution](combat-resolution.md) guide.**

### NPCs

Create NPCs from the **NPCs** sidebar menu:

- **Attributes**: Compact grid identical to PC sheets
- **Skills**: Free-text multi-roll field (e.g. `Sword 65, Riding 42`)
- **Actions**: Narrative actions and abilities list
- **Weapons**: Drag and drop weapon items directly into the Actions section
- **Hit Locations**: Click **Add default Strike Locations** to populate humanoid location tables
- **Armor Values**: Click **Refresh Armor Values** after equipping armor

### Encounters

Build encounters in the **Encounters** module and push them directly to the Combat Tracker when combat begins.

### GM Options

Under **Settings → Options → HarnMaster Rules**:

| Option | Effect |
|---|---|
| **Combat: Knockbacks** | Enables knockback rolls on heavy impact hits |
| **Combat: Limb injuries** | Tracks unusable limb conditions |
| **Combat: Amputations** | Enables amputation outcomes on grievous limb wounds |
| **Combat: Bleeders** | Adds blood-loss tracking for severe wounds |
