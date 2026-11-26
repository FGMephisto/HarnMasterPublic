# HarnMaster Status Effects & Conditions Reference

This reference lists only the status conditions, tactical tags, numerical modifiers, and conditional keywords that actually work in the **HarnMaster 3.5E** ruleset for **Fantasy Grounds Unity**.

---

## 1. How Effects Work in HarnMaster 3.5E

Effects placed on Combat Tracker entries (via power **Effect** buttons, automated combat/trauma resolution, or drag-and-drop from the **Effects** window) behave in one of three ways:

1. **Automated Conditions & Tactical Tags**: Recognized directly by the HarnMaster roll engine, the Combat Resolution Window (CRW), or trauma recovery automation.
2. **Numerical Modifier Tags**: Explicit `TAG: [n]` expressions (`ATK:`, `@ATK:`, `DEF:`, `CHECK:`, `SKILL:`, `INIT:`, `SAVE:`, `SAVEDC:`, `DMG:`, `@DMG:`) that add or subtract flat values on matching rolls.
3. **Visual Marker Conditions**: Presets shown in the Combat Tracker and as token status widgets without changing roll totals on their own. Pair a visual condition with a numerical modifier tag whenever you want an automated EML or damage adjustment.

```text
+-----------------------------------------------------------------------+
|                       COMBAT TRACKER EFFECT                           |
+-------------------------+----------------------+----------------------+
|  Automated Conditions   |  Numerical Modifiers |    Visual Markers    |
|  (Prone, Moonlight,     |  (ATK, @ATK, DEF,    |  (Blinded, Stunned,  |
|   COVER, Unconscious)   |   CHECK, SKILL, DMG) |   Invisible, Bleed)  |
+-------------------------+----------------------+----------------------+
|  Adjust EML, CRW cover, |  Add/subtract flat   |  Token icon & CT     |
|  turn skip, or recovery |  values on matching  |  reminder; pair with |
|  states automatically.    |  rolls.              |  tags for EML mods.  |
+-------------------------+----------------------+----------------------+
```

!!! tip "Effects Presets Window"
    Open the **Effects** sidebar window to drag and drop **LIGHTS** (token vision), **LIGHT CONDITIONS** (*Moonlight*, *Starlight*, *Near Darkness*), and **CONDITIONS** directly onto Combat Tracker entries without typing syntax manually.

---

## 2. Automated Conditions & Tactical Tags

### A. Combat Stance, Lighting, Cover & Target Size

| Condition / Tag | What the Ruleset Automates |
|---|---|
| **`Prone`** | **Attacker:** `-20 EML` on melee and ranged attacks; flags **High** aim zone as out of reach. **Defender:** `-20 EML` on defense rolls (**Block**, **Dodge**, **Counterstrike**); melee attackers gain `+20 EML`; ranged attackers take `-15 EML` (unless behind Cover). Applied automatically on failed **Stumble**, **Knockback**, **Shock**, or **Amputation** rolls. |
| **`Moonlight`** | Applies `-10 EML` to attacks, defenses, and **Eyesight** attribute checks. Nocturnal creatures (such as Gargun) are automatically exempt. Other skill checks remain at GM discretion. |
| **`Starlight`** *(or `Twilight`)* | Applies `-20 EML` to attacks, defenses, and **Eyesight** attribute checks. Nocturnal creatures are automatically exempt. |
| **`Near Darkness`** *(or `Darkness`)* | Applies `-30 EML` to attacks, defenses, and **Eyesight** attribute checks. Nocturnal creatures are automatically exempt. |
| **`COVER`** | Low Cover: `-10 EML` on incoming attacks and enables obstacle Plate protection (`B6/E10/P6/F2`) on covered strike locations in the CRW. |
| **`SCOVER`** | High Cover: `-20 EML` on incoming attacks and enables obstacle Plate protection (`B6/E10/P6/F2`) on covered strike locations in the CRW. |
| **`FULLCOVER`** *(or `TCOVER`)* | Full Cover: `-20 EML` on incoming attacks and applies obstacle Plate protection (`B6/E10/P6/F2`) across all strike locations in the CRW. |
| **`SIZE: <1ft`** | Placed on target: `-20 EML` on incoming ranged attacks. |
| **`SIZE: 1-2ft`** | Placed on target: `-15 EML` on incoming ranged attacks. |
| **`SIZE: 2-4ft`** | Placed on target: `-10 EML` on incoming ranged attacks. |
| **`SIZE: 6-8ft`** | Placed on target: `+10 EML` on incoming ranged attacks. |
| **`SIZE: 8-16ft`** | Placed on target: `+15 EML` on incoming ranged attacks. |
| **`SIZE: 16-32ft`** | Placed on target: `+20 EML` on incoming ranged attacks. |

!!! warning "Do Not Stack ATK / DEF Penalties onto `Prone`"
    Because **`Prone`** already applies `-20 EML` to attacks and `-20 EML` to defenses automatically, writing `Prone; ATK: -20; DEF: -20` double-penalizes the combatant (`-40 EML`). Use **`Prone`** by itself.

### B. Automated Trauma, Recovery & Wound Conditions

| Condition | What the Ruleset Automates |
|---|---|
| **`Unconscious`** | Applied automatically with **`Prone`** when failing a **Shock** roll. Suppresses duplicate shock prompts on non-lethal hits, drives automated Shock Recovery progression, and automatically skips NPC turns in the Combat Tracker. |
| **`Incapacitated`** | Applied automatically when passing an **Unconscious** recovery roll, triggering an immediate follow-up Shock roll. Passing removes `Incapacitated`; failing replaces it with **`Shock`**. |
| **`Shock`** | Applied automatically when failing recovery from `Incapacitated` (Medical Shock state). Removed automatically when a **Shock Recovery** test succeeds in the Medical Resolution Window. |
| **`Dead`** | Applied automatically on a failed **Kill Roll** or when total Wounds reach or exceed **Endurance**. Updates the Combat Tracker health status to **Dead** and suppresses further Shock prompts. |
| **`Surprised`** | Displays the token widget and automatically clears when the combatant ends their turn in the Combat Tracker. |
| **`Bleeding; <Location>`** | Added automatically on qualifying bleeder wounds when **Combat: Bleeders** is enabled in Options, and removed automatically when staunched/treated in the Medical Resolution Window. |
| **`<Location> unusable`** / **`<Location> severed`** | Added automatically on qualifying limb injuries or amputations when **Combat: Limb injuries** / **Combat: Amputations** are enabled; `severed` replaces `unusable` and prevents repeat amputation checks on the same limb. |

---

## 3. Numerical Modifier Tags & Conditionals

Use `TAG: [n]` syntax (for example `ATK: -20` or `SKILL: 10, sword`) to modify rolls numerically. Semicolons separate multiple components in one effect line (for example `Blinded; ATK: -40; DEF: -20`).

### Working Modifier Tags

| Keyword Syntax | Affected Rolls | Filter / Targeting Notes | Example |
|---|---|---|---|
| `ATK: [n]` | Melee & ranged attack rolls (on attacker) | Optional `, melee` or `, ranged` filter | `ATK: 20` or `ATK: -10, ranged` |
| `@ATK: [n]` | Incoming attack rolls (placed on defender) | Optional `, melee` or `, ranged` filter | `@ATK: -20` |
| `DEF: [n]` | Defense rolls (**Block**, **Dodge**, **Counterstrike**) | — | `DEF: -20` or `DEF: 10` |
| `CHECK: [n]` | Attribute checks, skill checks, and initiative | Optional attribute filter (e.g. `, eyesight`) | `CHECK: -15` or `CHECK: 10, eyesight` |
| `SKILL: [n]` | Skill checks | Optional skill name filter | `SKILL: -10` or `SKILL: 10, sword` |
| `INIT: [n]` | Initiative rolls | — | `INIT: 10` or `INIT: -10` |
| `SAVE: [n]` | Power saves, **Fumble**, **Stumble**, and **Amputation** | Optional save filter; does **not** apply to Shock or Kill rolls | `SAVE: -10` or `SAVE: 10, magic` |
| `SAVEDC: [n]` | Target number of triggered saves (placed on caster) | — | `SAVEDC: 10` |
| `DMG: [n]` | Weapon/spell damage rolls (on attacker) | Optional damage type filter (`blunt`, `edge`, `point`, `fire`) | `DMG: 2` or `DMG: 2, fire` |
| `@DMG: [n]` | Incoming rolled damage (placed on defender) | Optional damage type filter | `@DMG: -2` |

!!! note "Unsupported 5E / D20 Effect Syntax"
    * Numerical modifiers must always be flat integers (e.g. `CHECK: -20`). Division or formulas such as `CHECK: /2` or `SPEED: /2` are **not supported**.
    * 5E advantage/disadvantage tags (`ADVATK`, `DISATK`, `GRANTADVATK`, `GRANTDISATK`, `ADVCHK`, `DISCHK`, `ADVINIT`, `DISINIT`) and direct attribute modifiers (`STR: 2`, `END: 1`, etc.) do **not** modify HarnMaster percentile rolls. Use explicit flat EML or damage tags (`ATK:`, `DEF:`, `CHECK:`, `SKILL:`, `INIT:`, `SAVE:`, `DMG:`) instead.

### Conditional Effects (`IF:` / `IFT:`)

You can gate modifier tags on the actor's own state (`IF:`) or the target's state (`IFT:`) using recognized conditions, health states (`healthy`, `wounded`, `bloodied`), or `CUSTOM(...)` markers:

* `IFT: Prone; ATK: 10` — Adds `+10 EML` to attacks against a `Prone` target.
* `IF: wounded; CHECK: -10` — Applies `-10 EML` to checks while the actor has wounds.
* `IFT: CUSTOM(Marked); ATK: 10` — Adds `+10 EML` against targets bearing a `Marked` effect label.

---

## 4. Visual Marker Conditions (Effects Presets)

All remaining presets in **Effects → CONDITIONS** display a token status widget and Combat Tracker label only—they do **not** apply hidden penalties automatically. Pair them with numerical tags when mechanical EML adjustments are needed:

| Preset Condition | Behavior & Optional Paired Modifier Example |
|---|---|
| **`Blinded`** | Visual token marker. Example with manual modifiers: `Blinded; ATK: -40; DEF: -20` |
| **`Charmed`** | Visual token marker (social/allegiance reminder). |
| **`Cursed`** | Visual token marker. Example: `Cursed; CHECK: -10; ATK: -10` |
| **`Deafened`** | Visual token marker. Example: `Deafened; CHECK: -30, hearing` |
| **`Encumbered`** | Visual token marker (encumbrance penalty is normally driven by Inventory **Penalty Base** → **PP**). Example for ad-hoc penalties: `Encumbered; CHECK: -10` |
| **`Frightened`** | Visual token marker. Example: `Frightened; ATK: -20; DEF: -10` |
| **`Grappled`** | Visual token marker. Example: `Grappled; ATK: -20; DEF: -20` |
| **`Intoxicated`** | Visual token marker. Example: `Intoxicated; CHECK: -10; ATK: -10` |
| **`Invisible`** | Visual token marker. Example to penalize incoming attacks: `Invisible; @ATK: -20` |
| **`Paralyzed`** | Visual token marker (reminder that actor cannot act). |
| **`Petrified`** | Visual token marker. |
| **`Poisoned`** | Visual token marker. Example: `Poisoned; CHECK: -20; ATK: -20` |
| **`Restrained`** | Visual token marker. Example: `Restrained; ATK: -20; DEF: -20` |
| **`Stable`** | Visual stabilization marker in the Combat Tracker. |
| **`Stunned`** | Visual token marker. Example: `Stunned; DEF: -20` |
| **`Bleeding`** / **`Bleed`** | Visual bleeder icon (also added automatically as `Bleeding; <Location>` when **Combat: Bleeders** is active). |

!!! tip "Fatigue & Encumbrance Are Native"
    **Fatigue (FT)** on the sheet header / Combat Tracker and **Encumbrance** on the **Inventory** tab automatically compute **Universal Penalty (UP)** and **Physical Penalty (PP)** across rolls—no manual effect tags are needed for them.

---

## 5. Working Effect Syntax Cheat Sheet

| Desired Result | Verified Working Effect String | Behavior |
|---|---|---|
| **Attack Bonus / Penalty** | `ATK: 20` / `ATK: -10` | Adds or subtracts EML on attacker's attack rolls |
| **Incoming Attack Penalty** | `@ATK: -20` | Subtracts 20 EML from attacks targeting this actor |
| **Defense Bonus / Penalty** | `DEF: 20` / `DEF: -20` | Adds or subtracts EML on Block, Dodge, and Counterstrike |
| **Attribute & Skill Check Mod** | `CHECK: -15` | Subtracts 15 EML from attribute and skill checks |
| **Specific Skill Mod** | `SKILL: 10, sword` | Adds +10 EML to Sword skill checks |
| **Initiative Modifier** | `INIT: 10` or `INIT: -10` | Adjusts initiative roll |
| **Save Modifier** | `SAVE: -10` | Adjusts power saves, Fumble, Stumble, and Amputation |
| **Damage Bonus / Mitigation** | `DMG: 2` / `@DMG: -2` | Adjusts outgoing or incoming rolled damage |
| **Prone Stance** | `Prone` | Auto-applies `-20 EML` atk/def, `+20` melee vs. target, `-15` ranged vs. target |
| **Darkness Levels** | `Moonlight` / `Starlight` / `Near Darkness` | Auto-applies `-10` / `-20` / `-30` EML on atk, def, and Eyesight (nocturnal exempt) |
| **Cover** | `COVER` / `SCOVER` / `FULLCOVER` | Auto-applies `-10` / `-20` / `-20` EML and CRW obstacle Plate protection |
| **Ranged Target Size** | `SIZE: <1ft` to `SIZE: 16-32ft` | Auto-applies `-20` to `+20` EML on incoming ranged attacks |
| **Blinded (With Penalties)** | `Blinded; ATK: -40; DEF: -20` | Displays Blinded icon and applies `-40` attack / `-20` defense EML |
| **Invisible (With Penalties)** | `Invisible; @ATK: -20` | Displays Invisible icon and imposes `-20 EML` on incoming attacks |
| **Conditional Strike Bonus** | `IFT: Prone; ATK: 10` | Grants `+10 EML` when attacking a Prone target |
