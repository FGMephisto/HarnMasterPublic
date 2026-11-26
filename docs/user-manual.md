# HarnMaster 3.5E for Fantasy Grounds — User Manual

## Introduction

This manual explains how to use the **HarnMaster 3.5E** interface inside **Fantasy Grounds Unity** — what each button, icon, cycler, and field displays or does, and what multi-step windows or automated actions those controls trigger. Keep your HarnMaster rulebook handy for tabletop rules; rule mechanics are mentioned here only where they clarify what the software automates.

---

## The Character Sheet

### Header Bar (`FATIGUE` & `PEN. & ROLLS`)

Every tab shares the same character sheet header:

| Control / Field | Type | What It Shows or Does |
|---|---|---|
| **Portrait & Name** | Editable / Display | Displays the character portrait (double-click to change) and editable character name. |
| **FATIGUE** | Editable number | Tracks active fatigue levels (`0` minimum). Changes feed immediately into **Universal Penalty (UP)** and the Combat Tracker **FT** column. |
| **PEN. & ROLLS (`UP / PP`)** | Read-only display | Shows current **Universal Penalty (UP)** and **Physical Penalty (PP)** (hover for tooltip). |
| **Rolls Toggle** *(die icon)* | Button | Shows or hides the **Quick Rolls Strip** directly below the header. |

!!! note "Automatic Penalty Application"
    The ruleset applies **UP** and **PP** automatically to attribute, skill, attack, defense, and shock/stumble/fumble rolls. Do **not** subtract them manually in the Modifier Box.

#### Quick Rolls Strip *(Die Icon Beside UP / PP)*

* **How to Trigger:** Click the die icon beside the **PEN. & ROLLS** readout in the character header.
* **What Opens:** Expands a compact quick-roll strip directly beneath the header containing roll buttons for **Dodge**, **Shock**, **Stumble**, and **Fumble**. Every button supports clicking to roll immediately or dragging to chat / a hotbar slot.
* **Conditional Trauma Row:** When severe combat trauma triggers a pending **Kill Roll** or **Amputation** check, a crimson second row automatically appears in this strip with dedicated **Kill Roll** and **Amputation** buttons.

### Character Sheet Tabs

| Tab | Contents |
|---|---|
| **Main** | Attributes, Shek-Pvar overview, Religion & Piety summary, and Physical Appearance summary |
| **Skills** | Skill Group icon filter bar, compact skill list with **Sub-Roll** and **Roll** buttons, name search, and Detailed Skills window |
| **Powers** | Collapsible Religion panel, Shek-Pvar Convocation filter bar, and Powers list with action automation |
| **Inventory** | Carried items, currencies, and Encumbrance load/penalty calculator |
| **Combat** | Equipped/carried Armor list with coverage details, Mode toggle, and Strike Locations armor table popup |
| **Actions** | Active Injuries list (with Detailed Injuries & Heal rolls) and Weapons list with Attack/Defend/Damage/Ammo controls |
| **Notes** | Birth & Family, Physical/Medical & Mental Traits, Clerical Order, Fighting Order, Background & Holdings, and free-text Notes |

---

### Main Tab & Background Details {#main-tab}

The **Main** tab serves as the character's at-a-glance overview. Most summary blocks here are **read-only**; click any section's **Details** button (grid icon at the top-right of the section banner) to open the unified **BACKGROUND** editor window.

#### Attributes {#skills-tab-attributes}

* **Compact View:** Click the **ATTRIBUTES** banner to collapse or expand the grid. Each row displays the attribute name, a **Roll** die button (supports click or drag), and the read-only **Total** score. Hovering or viewing detailed stats shows qualitative ratings where applicable.
* **Attributes Editor (`Details` button):** Opens the **ATTRIBUTES** popup listing every attribute with:

| Column | Type | What It Shows or Does |
|---|---|---|
| **Name** | Read-only | Full attribute name. |
| **Base** | Editable | Raw starting attribute score. |
| **Mod.** | Editable | Flat adjustment (species, traits, magic, etc.). |
| **Total** | Read-only | Computed sum (`Base + Mod.`) used on rolls. |

#### Shek-Pvar, Religion & Physical Appearance Summaries

| Section | Control / Field | Type | What It Shows or Does |
|---|---|---|---|
| **SHEK-PVAR** | **Primary Conv.**, **Rank**, Convocation Icon | Read-only | Shows the character's arcane convocation, rank, and emblem; click **Details** to edit. |
| **RELIGION** | **Deity**, Deity Icon, **Main Deity** tag | Read-only | Lists each configured deity and highlights **Main Deity** when multiple deities exist. |
| **RELIGION** | **Piety** | Editable number | Adjust current piety inline without leaving the **Main** tab. |
| **PHYSICAL APPEARANCE** | **Height (in)**, **Frame**, **Weight (lbs)**, **Size**, **Eye Color**, **Hair Color**, **Comeliness**, **Voice**, **Complexion** | Read-only | Compact physical summary; **Size** is derived automatically from height/weight, and **Comeliness** / **Voice** show descriptive labels. Click **Details** to edit. |

#### Background Details Window *(Any `Details` Button on Main or Notes)*

Clicking the **Details** icon on **SHEK-PVAR**, **RELIGION**, **PHYSICAL APPEARANCE**, **BIRTH & FAMILY**, **CLERICAL ORDER**, **FIGHTING ORDER**, or **BACKGROUND & HOLDINGS** opens the single-column **BACKGROUND** editor:

* **Religion Section:** Click **`+`** on the **RELIGION** header to add a deity row, type with autofill support, set **Piety**, toggle the **Primary Deity** checkbox beside the name, or click the delete button to remove an entry. Entering a deity in **Cleric of** (under **Clerical Order**) automatically adds/highlights that deity on the **Powers** tab.
* **Autofill Fields:** Many fields (Primary Convocation, Rank, Frame, Eye/Hair Color, Complexion, Species, Gender, Culture, Social Class, and Deity) offer autofill suggestions as you type.
* **Recalculate Weight Button *(inside `Weight` field)*:** Clicking this icon computes the character's optimum weight from the current **Height** and **Frame**.
* **Birthdate Helper Button *(inside `Birthdate` field)*:**
  * **How to Trigger:** Click the details icon on the right side of the **Birthdate** field.
  * **What Opens:** Opens the **BIRTHDATE** helper dialog with editable **Day (1–30)**, **Month (1–12)**, and **Year (TR)** inputs and read-only previews.
  * **On Update:** Automatically formats the Harnic birthdate and calculates **Derived Sunsign & Cusp**, which in turn applies Sunsign bonuses to matching skills on the **Skills** tab.

---

### Skills Tab & Skill Sub-Rolls {#skills-tab}

The **Skills** tab provides category filtering, standard percentile rolls, situational sub-roll pickers, and full skill editing.

#### SKILL GROUPS Filter Bar

At the top of the tab, **SKILL GROUPS** displays monochrome etched category icons for **Physical**, **Comm.** (Communication), **Language**, **Religion**, **Combat**, **Craft/Lore**, and **Convoc.** (Shek-Pvar Wheel):

* Click any icon to filter the **SKILLS** list to that group (the active icon highlights).
* Click the active icon again to clear the filter and show **All Skills**.

#### Compact Skills List

| Column / Control | Type | What It Shows or Does |
|---|---|---|
| **Name** | Read-only | Skill name (with speciality appended if set). Hover for a tooltip listing any available sub-rolls. |
| **SB** | Read-only | Skill Base computed from the linked attributes and Sunsign bonus. |
| **Sub-Roll** *(light die left of standard die)* | Button | Opens the **SUB-ROLLS** picker for skills that have specialized rolls. Skills without sub-rolls show blank space so columns stay aligned. |
| **Roll** *(dark die right of Sub-Roll)* | Button | Makes a standard percentile roll against the skill's effective ML (click or drag to chat/hotbar). |
| **ML** | Read-only | Current Mastery Level rolled against. |
| **Filter Box** *(bottom)* | Editable search | Type part of a skill name to filter the list live. |

#### Sub-Roll Picker (`SUB-ROLLS`) *(Secondary Die Icon / NPC Shift+Roll)*

* **How to Trigger:** Click the **Sub-Roll** light die icon on a PC skill row, or hold **Shift** while double-clicking or dragging an eligible skill on an **NPC** sheet.
* **What Opens:** Opens the **SUB-ROLLS** window titled with the skill name and listing each situational roll (for example: **Physician** — *Diagnose*, *Treat Injury*, *Veterinary Medicine (-10)*; **Rhetoric**; **Foraging**; **Herblore**; **Lockcraft** Complexity 1–9; **Weatherlore**; and Craft **Assess** checks). Hover any row or roll button for its description.
* **Interactive Choice:** Click a row's **Roll** button (or drag it to chat / a hotbar slot) to roll with that scenario's modifier applied.
* **On Resolution:**
  * Posts the scenario-tagged EML, d100 roll, Degree of Success (**CS / MS / MF / CF**), and automated table outcome (such as foraging yields) to chat.
  * For **Physician → Diagnose** and **Treat Injury**, automatically hands the rolled result to the Game Master and opens the **Medical Resolution Window (MRW)** pre-filled with the check result.

#### Detailed Skills Window (`Details` Button on `SKILLS` Header)

Click **Details** on the **SKILLS** header to open the expanded skill editor:

| Column | Type | What It Shows or Does |
|---|---|---|
| **Name** | Editable | Base skill name. |
| **Speciality** | Editable | Optional specialization (e.g., *Broadsword*, *Kaldoric*). |
| **Skill Group** | Editable / Autofill | Category used by the Skill Groups filter bar. |
| **Attributes** | Editable | Linked attributes used to calculate SB (up to three). |
| **Sunsigns** | Editable | Sunsign affinities granting bonus ranks when matching the character's birthdate. |
| **OML** | Editable | Opening Mastery Level multiplier/formula or fixed base. |
| **SB** | Read-only | Computed Skill Base. |
| **Dev.** | Editable | Development ranks gained through play. |
| **ML** | Read-only | Computed Mastery Level (`OML + Dev`). |
| **Development Roll** *(dice icon)* | Button | Rolls a Skill Development check (if enabled in GM Options, warns when weapon skill limits are reached). |

---

### Powers Tab — Magic, Invocations & Psionics {#powers-tab-magic-invocations-psionics}

The **Powers** tab manages Shek-Pvar spells, clerical rituals/invocations, and psionic talents. Drag spells or powers directly from library modules onto the tab to add them.

#### Collapsible Top Panels

* **RELIGION Panel:** Appears automatically once **Cleric of** is set in Background Details; click the **RELIGION** banner to expand or collapse. Shows the deity emblem, editable **Deity** (autofill) and **Piety** counter, read-only linked Ritual **ML**, and a **Roll** die button to test the matching Ritual skill directly.
* **SHEK-PVAR Filter Bar:** Click the **SHEK-PVAR** banner to expand or collapse. Shows **Neutral** plus all six Convocation medallions ordered around the character's **Primary Convocation** (shown larger). Hover any medallion to see its name, wheel relationship, and OML; click a medallion to filter **POWERS** to that convocation, and click it again to show all.

#### Powers List & Action Automation

Click the **POWERS** banner to collapse/expand the list, or click **Details** (top-right of **POWERS**) to open the full Detailed Powers & Power Group editor.

| Control | Type | What It Shows or Does |
|---|---|---|
| **Delete** | Button | Two-step delete when sheet is unlocked. |
| **Link** *(spell icon)* | Button | Opens the underlying power/spell reference record. |
| **Cast / Use** *(star/hand icon)* | Button | Quick-casts or activates the power; hover for a summary tooltip. |
| **ML** | Read-only | Linked Convocation, Ritual, or Psionic Talent Mastery Level. |
| **Name** | Editable | Power or spell name. |
| **Expand Details** *(magnifying glass)* | Toggle | Shows or hides the embedded modular action rows (**Cast**, **Attack**, **Save**, **Damage**, **Heal**, **Effect**) and mini quick-action icons. |

#### Cast & Modular Action Flow

* **How to Trigger:** Click **Cast** on an expanded power row (or use the mini **Cast** icon on a collapsed row). If the power has configurable options, click the **`?` (Choices)** button first to choose variants, and use the **Target** button or Combat Tracker targeting to pick targets.
* **What It Reads:** Evaluates the linked Convocation, Ritual, or Psionic ML, active UP, and any group modifiers.
* **On Resolution:**
  * Posts the cast result (**CS / MS / MF / CF**) to chat and automatically increments **Fatigue** when the power carries a fatigue cost.
  * Synchronizes the rolled **Degree of Success (DoS)** across sibling action rows (**Damage**, **Save**, **Effect**) so follow-up clicks automatically use the CS/MS/MF/CF outcome.
  * **Attack** actions feed directly into the **Combat Resolution Window (CRW)**; **Effect** buttons apply HarnMaster conditions or modifiers directly onto targeted Combat Tracker tokens.

#### Power Group Detail Window

Accessible via **Details** (next to **POWERS**) and group detail buttons: configure **Group Name**, **Group Type** (Spell / Ritual / Psionic), linked **Skill**, **Piety (current / max)**, Attack Stat/Modifier, Uses per period, and Prepared count.

---

### Inventory Tab {#inventory-tab}

Manages carried equipment, monetary wealth, and automated encumbrance.

#### Carried Items (`INVENTORY`)

* Click **`+`** on the **INVENTORY** header (when unlocked) or drag items from the **Items** sidebar onto the list to add gear.
* Each row provides: **Delete**, item **Link**, **`#` Count** (editable), **Name** (editable), **Location** (container/stowage slot; editable), **Weight** (editable per-unit/item weight), and **Carried State** icon:

| Carried State | Behavior |
|---|---|
| **Not Carried** | Stored away; excluded from load calculations and Combat/Actions lists. |
| **Carried** | Stowed in pack/location; counts toward **Carried** and **Total** load. |
| **Equipped** | Worn or ready; feeds armor protection into **Combat → ARMOR / STRIKE LOCATIONS** and keeps weapons ready on **Actions**. |

#### Currencies & Encumbrance

* **CURRENCIES:** Click **`+`** to add currency rows, edit **Amount** (supports dropping numeric values onto the field to add) and **Name**, or delete rows when unlocked.
* **ENCUMBRANCE:** Displays read-only **Carried**, **Equipped**, and **Total** weight, a **Penalty Base** cycler (**`Equipped`** vs. **`Carried`**), and read-only **Penalty**. The calculated Encumbrance Penalty feeds automatically into **Physical Penalty (PP)** on the sheet header.

---

### Combat Tab — Armor & Strike Locations {#combat-tab-armor-penalties}

The **Combat** tab shows your armor inventory, hit-location coverage, and overall body protection. Drag armor records directly onto this tab to add them.

#### Mode Bar & Armor List

* **Mode Cycler *(bottom bar)*:** Cycles between **Standard** (displays all carried/equipped armor and **WT**) and **Combat** (compact view hiding weight and focusing on worn protection).
* **ARMOR Header & List:** Click **Details** (grid icon at top-right of **ARMOR**) to open the **STRIKE LOCATIONS** window. Each armor row shows:

| Control / Column | Type | What It Shows or Does |
|---|---|---|
| **Armor Artwork** | Clickable image | Shows the item picture (or material fallback icon). Click to open the full artwork preview if assigned, or the item sheet otherwise. |
| **Link** | Button | Opens the item record. |
| **Carried Toggle** *(below link)* | Button | Cycles Not Carried / Carried / Equipped directly from the armor list. |
| **NAME / COVERAGE** | Read-only | Item name plus wrapped list of covered body locations (hover for full tooltip). |
| **WT** *(Standard mode only)* | Read-only | Item weight. |
| **B / E / P / F** | Read-only | Armor Blunt, Edge, Point, and Fire protection values. |

#### Strike Locations Window (`Details` Button on `ARMOR` Header) {#combat-tab-strike-locations}

Opens the **STRIKE LOCATIONS** helper window showing:

1. **Encumbrance Summary:** Displays **Carried**, **Equipped**, **Total**, **Penalty Base** cycler, and **Penalty** at the top for quick tuning while adjusting armor.
2. **STRIKE LOCATIONS Table:** Two-column body map displaying the total combined **B / E / P / F** protection at every body location (*Skull*, *Face*, *Neck*, *Thorax*, *Shoulder*, *Upper Arm*, *Elbow*, *Forearm*, *Hand*, *Abdomen*, *Groin*, *Hip*, *Thigh*, *Knee*, *Calf*, *Foot*), updating live whenever armor is equipped, unequipped, or modified.

---

### Actions Tab — Injuries & Weapons {#actions-tab-weapons}

The **Actions** tab combines active wound tracking with weapon combat controls.

#### Injuries Sub-Panel {#combat-tab-injuries}

Click the **INJURIES** banner to collapse/expand, click **`+`** to add an injury manually, or click **Details** to open the expanded clinical table.

* **Compact Row:** Shows **Delete** (unlocked), **Location** (wound description & struck location), **Aspect** (*Blunt*, *Edge*, *Point*, *Fire*, *Frost*), and **IL** (Injury Level `1–5`). Active Injury Levels automatically sum into **UP** and the Combat Tracker **Wounds** column.
* **Detailed Injuries Window (`Details` button):** Lists **Location**, **Aspect**, **IL**, **HR** (Healing Rate), **Date**, **Notes**, delete control, and a **Heal** die button per row:
  * Clicking **Heal** (or dragging it to chat) performs a single-wound healing progression roll for that injury.

#### Weapons List (`WEAPONS`)

Click the **WEAPONS** banner to collapse/expand. The bottom bar provides the **Mode** cycler (**`Standard`** vs. **`Combat`**) and the **Add Weapon** sword button (adds a blank weapon entry; you can also drag weapons from **Items** onto the list).

##### Weapon Header Row

| Control | Type | What It Shows or Does |
|---|---|---|
| **Delete** | Button | Removes the weapon (when unlocked). |
| **Weapon Artwork** | Clickable image | Displays weapon artwork or category fallback icon. Click to open the full artwork preview or weapon sheet. |
| **Link** | Button | Opens the underlying Inventory item record. |
| **Carried** *(Standard mode)* | Button | Syncs Carried / Equipped state with Inventory. |
| **Weapon Type** | Cycler | Switches displayed attack rows between **Melee**, **Ranged**, and **Thrown**. |
| **Handling** | Cycler | Cycles hand mode / weapon handling state. |
| **Name** | Editable | Weapon name (when unlocked). |
| **Roll Strike Location on Target** *(crosshair icon)* | Button | **Complex trigger:** Rolls `d100` against the currently targeted combatant's hit location table in the Combat Tracker (or falls back to the default humanoid table if no target is set) and posts the struck location to chat. |
| **Details** *(grid icon)* | Button | Opens the **Weapon Editor** popup. |

Right-click a weapon entry for its radial menu: **Add Attack Entry → Add Melee / Add Ranged / Add Throwing**.

##### Weapon Action Row Controls

| Control / Field | Type | What It Shows or Does |
|---|---|---|
| **Aim Zone** | Cycler | Cycles **High**, **Mid**, and **Low**; applies aim modifier and informs CRW location rolls. |
| **Attack** *(sword icon)* & **AML** | Button + Read-only | Click or drag to roll Attack against current effective **AML** (opens CRW for the GM). |
| **Defend** *(shield icon)* & **DML** | Button + Read-only | Click or drag to roll Block/Parry defense against current effective **DML**. |
| **Range Bracket** & **Range** *(Ranged/Thrown)* | Cycler + Read-only | Cycles **Short**, **Medium**, **Long**, and **Extreme** range brackets, updating effective AML and displayed metre distance. |
| **Damage Aspect** | Cycler | Cycles **Blunt**, **Edge**, and **Point** for the next damage roll. |
| **Damage** *(fist icon)* & **B/E/P** | Button + Read-only | Click or drag to roll weapon damage for the active aspect (updates an open CRW if targeted). |
| **Reorder** *(bars icon)* | Drag handle | Drag to reorder attack entries within the weapon. |
| **Ammo** *(Ranged/Thrown)* | Number + Pip tracker | Set max ammo count and click pips to mark/restore spent ammunition. |

##### Weapon Editor (`Details` Button on Weapon Row)

Displays a larger clickable **Weapon Artwork** thumbnail, editable **Weapon** name, **WQ / Current** weapon quality counters, and weapon-level **Properties**, followed by three dedicated lists (**MELEE**, **RANGED**, **THROWN**). Each section has its own **`+`** add button, **Edit/Delete** toggle, and per-row fields: **Note**, **Skill** (with weapon-skill autofill), **A** (Attack mod), **D** (Defense mod), **HM** (Hand Mode), **B** / **E** / **P** (Blunt / Edge / Point impact), **Range S/M/L/E** (Ranged/Thrown), and per-action **Properties** (merged with weapon properties on rolls).

---

### Notes Tab {#notes-tab}

Organizes character biography, orders, traits, and free-form notes:

* **Read-Only Biographical Summaries:** **BIRTH & FAMILY**, **CLERICAL ORDER**, **FIGHTING ORDER**, and **BACKGROUND & HOLDINGS** mirror the character's biographical record cleanly; click any section's **Details** button to edit fields in the **BACKGROUND** window.
* **PHYSICAL / MEDICAL TRAITS & MENTAL TRAITS:** Dedicated interactive trait lists. Drag entries directly from the **Traits** sidebar library onto either list, click a trait link to open its description, or unlock the sheet to add, edit, or delete entries.
* **NOTES:** Scroll-free multi-line free-text field at the bottom of the tab.

---

### Exporting & Printing Character Profiles {#exporting-printing-characters}

The ruleset includes an automated print generator that exports an **8-page print-ready HTML character dossier** matching the canonical HârnMaster 3.5E sheet layout:

1. Open the character sheet (or right-click the character in the **Characters** sidebar list) and select **Export Character**.
2. Choose a destination file and save. Alongside the XML export, FGU writes a companion `.html` dossier covering:
   * **Page 1:** Character Profile, Portrait (supports in-browser drag-and-drop photo replacement), and Attributes.
   * **Page 2:** Skills, Skill Bases, Sunsign affinities, Development, and Mastery Levels.
   * **Page 3:** Combat Armor Coverage (32-location B/E/P/F map), Weapons (with weapon & armor artwork), Aim Zones, and Range Brackets.
   * **Page 4:** Trauma, Injuries, Healing Rates, UP/PP, and Shock data.
   * **Page 5:** Inventory, Containers, Coinage, and Encumbrance.
   * **Page 6:** Psionics & Esoteric Talents.
   * **Page 7:** Shek-Pvar Magic & Clerical Rituals.
   * **Page 8:** Background, Orders, and Family History.
3. Open the `.html` file in any browser and press **Ctrl+P** to print or save as PDF.

---

## Making Rolls & The Modifier Box

All percentile tests compare `d100` against effective Mastery Level (**ML**), outputting **Critical Success (CS)**, **Marginal Success (MS)**, **Marginal Failure (MF)**, or **Critical Failure (CF)** directly to chat.

* Click any **Roll** die icon to roll immediately, or **drag** any die icon onto the chat window, the dice tower, or a hotbar slot for quick access.

### The Modifier Box

The floating **Modifier Box** above chat modifies your next roll:

| Control | Function |
|---|---|
| **Numeric Box & `+2` / `-2` / `+5` / `-5`** | Adds a flat bonus or penalty to the next roll's EML (or damage total). |
| **Multipliers (`x2` – `x7`)** | Overrides the default `x5` Skill Base multiplier on attribute/skill checks (e.g., `x2` Very Hard through `x7` Trivial), or multiplies damage dice on weapon damage rolls. |
| **Low Cover / High Cover / Full Cover** | Applies incoming ranged/cover EML modifiers (`-10` / `-20`) and tells the Combat Resolution Window to test covered strikes against obstacle protection. |
| **Prone** | Applies the Prone tactical modifier on the next attack/defense check. |

---

## Combat Flow Overview

Combat resolves through **Attack → Defense → Damage → Trauma Prompts**:

1. **Attack:** Target an opponent on the map or Combat Tracker, choose your **Aim Zone** (*High*, *Mid*, *Low*) and **Range Bracket** (if ranged/thrown), and click **Attack**. The ruleset applies UP, Aim Zone, Range, Prone, Cover, and Creature Size differences automatically and opens the **Combat Resolution Window (CRW)** for the GM.
2. **Defense:** The defender rolls **Block**, **Dodge**, or **Counterstrike** (or selects **Ignore**). The CRW compares both rolls on the matrix immediately.
3. **Damage & Injury:** If a hit multiplier applies, roll **Damage** (weapon or CRW prompt); the CRW applies armor/cover mitigation and generates the resulting wound upon **Apply Result**.
4. **Automatic Trauma Prompts:** Applying an injury updates **Wounds** and **UP** and posts required **Shock** checks—or triggers **Kill Roll** / **Amputation** buttons on the sheet and Combat Tracker when severe trauma occurs.

👉 **See [Combat Resolution](combat-resolution.md) for the complete interactive walkthrough of the Combat Resolution Window.**

---

## Game Master Guide

### The Combat Tracker

The **Combat Tracker** displays HârnMaster-specific columns and expandable drawers per combatant:

| Control / Section | Visibility | Function |
|---|---|---|
| **Wounds**, **FT** (Fatigue), **HP** | Header row | **Wounds** totals active Injury Levels (and accepts dropped damage rolls); **FT** edits Fatigue inline. |
| **Reopen Combat Resolution** *(crossed swords)* | GM | Reopens the Combat Resolution Window for an active/pending attack against that combatant. |
| **Active** *(sword toggle)* | Host / Player | Shows **Initiative**, **Speed**, and clickable NPC Traits, Actions, and Spells. |
| **Defense** *(fist toggle)* | GM (NPCs) | Quick attribute scores plus **Fumble**, **Stumble**, **Shock**, **Kill Roll**, and **Amputation** roll buttons; strike location list (accepts damage/injury drops); and inline **Injuries** list (`+` add and edit toggle). |
| **Effects** *(person/aura toggle)* | Host / Player | Active status conditions, numerical modifiers, and durations (accepts drags from the **Effects** presets window). |

**Initiative Radial Menu:** Right-click a Combat Tracker entry (or menu button) and choose **Set Initiative → Set All / NPC / PC Initiatives**.

---

### Medical Resolution Window (MRW) {#medical-resolution-window}

The **Medical Resolution Window** coordinates Diagnosis, Treatment, Healing Cycles, Infection checks, Shock Watch recovery, Tourniquet/Cauterize stabilization, Surgical Amputation, and Bloodloss tracking.

* **How to Trigger:**
  * Opens automatically for the GM whenever a **Player Character** or **NPC** rolls **Physician → Diagnose** or **Treat Injury** from the **SUB-ROLLS** picker (PC Sub-Roll icon or NPC `Shift+Double-Click` / `Shift+Drag`).
  * Can also be opened from medical/healing workflow actions.
* **Window Controls & Flow:**
  1. **Patient & Wound Selectors:** Choose the **Patient** from the dropdown (campaign PCs and Combat Tracker actors), or choose **"Other"** for an ad-hoc NPC not stored in the database. When a sheet-backed patient is chosen, pick the specific injury in the **Wound** dropdown. (With **Other**, no DB wound selection is required.)
  2. **Physician & EML Override:** Review or adjust **Physician** name and **EML Override** (`0` = automatic lookup from rolled skill or sheet).
  3. **Wound Summary:** Read-only snapshot displaying **Wound**, **Severity**, **Aspect**, **IL**, **HR**, **Diagnosis Bonus**, **Infected**, and **Bleeder**.
  4. **Roll & Re-Roll:** Shows calculated **Target (TL)** (editable if GM override is needed), **Roll**, and **Result** degree (`CS / MS / MF / CF`). Click **Re-Roll** to roll again inside the window.
  5. **Proposed Outcome:** Pre-fills editable results (**Proposed Outcome** text, **New HR**, **New IL**, **Is Diagnosed**, **Diagnosis Bonus**, **Attr. Reduction \***, **Infected**, **Bleeder**).
  6. **Confirm / Cancel:** Click **Confirm** to apply all approved outcome fields to the patient's wound record and broadcast to chat (if **Other** is selected, **Confirm** finishes cleanly without requiring a database node), or click **Cancel** to close without saving.

---

### Effects Presets Window

Open the **Effects** sidebar button (running figure icon) to drag and drop ready-made tags onto Combat Tracker entries without memorizing syntax:

* **LIGHTS:** Token vision light presets (*Torch*, *Lantern*, *Candle*, etc.).
* **LIGHT CONDITIONS:** Ambient darkness conditions (*Moonlight*, *Starlight*, *Near Darkness*).
* **CONDITIONS:** Standard automated and informational conditions.

👉 **See [Status Effects & Conditions](status-effects-reference.md) for automated vs. informational condition behavior and effect syntax.**

---

### NPCs

Manage NPCs from the **NPCs** sidebar across four tabs: **Main**, **Locations**, **Notes**, and **Pictures**.

#### Main Tab

* **Summary Banner:** **Size** and **Type** (collapse/expand).
* **Attributes Grid:** Compact editable attribute grid; click any **Roll** die button to roll an attribute check.
* **Skills Field:** Comma-separated multi-roll text field (e.g., `Sword 65, Physician 58`).
  * **`Double-Click` / `Drag`:** Rolls a standard percentile check for the highlighted skill.
  * **`Shift+Double-Click` / `Shift+Drag`:** Opens the **SUB-ROLLS** picker when the hovered skill has specialized sub-rolls (hover any skill for a tooltip showing its available sub-rolls).
* **Senses:** Free-text sense notes.
* **ACTIONS:** Click **`+`** to add narrative/parsed actions, click **Edit** to delete or reorder rows, or drag weapon items directly into the list to generate combat lines automatically.

#### Locations Tab

* **Worn Armor & Details:** Shows equipped armor summary; click **Details** to open the NPC armor/location detail window.
* **Header Action Row:**
  * **Roll Strike Location** *(die icon)* & **Show/Hide Roll** *(eye icon)*: Rolls an NPC strike location and toggles whether results appear publicly in chat or remain GM-hidden.
  * **Natural Armor (`B / E / P / F`)**: Editable base natural armor values.
  * **Refresh Armor Values** *(circular arrows)*: Recomputes per-location **B/E/P/F** from natural armor plus worn armor (skips rows marked with **Manual Override**).
  * **Add default Strike Locations** *(table icon)*: Populates standard humanoid `d100` hit locations; prompts for confirmation before overwriting existing rows.
* **Strike Location Rows:** Editable range (`From–To`), **`L/R`** lateral checkbox, **Strike Locations** name, **B / E / P / F** values, plus (when unlocked) **`Loc`** shorthand ID and **`Man`** (**Manual Override**) checkbox to protect custom row armor during refreshes.

---

### Sidebar Libraries & GM Options

* **Traits Library:** Create or browse Traits (formerly Feats) and drag them directly onto character **Physical / Medical Traits** or **Mental Traits** lists.
* **Items Grouped View:** Includes a **Vendor** column alongside Weight, Weapon Quality, Attack/Defense/Hand Mode, Damage, and Armor B/E/P/F columns.
* **Encounters:** Build encounter groups and push all NPCs directly to the Combat Tracker.

#### GM Options (`Settings → Options → HarnMaster Rules`)

| Option | Effect |
|---|---|
| **Combat: Knockbacks** | Enables automatic knockback checks on qualifying high-impact hits. |
| **Combat: Limb injuries** | Tracks impaired / unusable limb conditions on severe extremity wounds. |
| **Combat: Amputations** | Enables pending **Amputation** checks on grievous extremity edge/blunt wounds. |
| **Combat: Bleeders** | Enables active arterial/venous bleeder flags and bloodloss tracking. |
| **Skills: Weapon SBx5 experience cap** | Displays a warning when developing weapon skills at or above `SB × 5`. |
| **Skills: Weapon Initiative+10 cap** | Displays a warning when developing weapon skills at or above `Initiative ML + 10`. |
