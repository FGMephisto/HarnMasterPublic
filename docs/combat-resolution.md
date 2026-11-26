# Combat Resolution

The **Combat Resolution Window (CRW)** is the GM's central interactive dialog for resolving HarnMaster attacks. Whenever an attack is rolled, a CRW opens automatically for the Game Master to coordinate attacker/defender outcomes, cover mitigation, multi-hit damage, strike locations, and wound application.

---

## Overview & Workflow

1. **Attack Rolled:** A PC or NPC rolls an attack (with Aim Zone and Range Bracket). The CRW opens pre-filled with attacker, defender, weapon, and rolled test level.
2. **Defense:** The defender rolls normally—or the GM clicks the CRW's one-click **Block** or **Dodge** buttons—and the matrix **Result** updates immediately.
3. **Damage:** Players roll weapon damage as usual, or the GM clicks the contextual **Roll Damage (xN)** button for NPC attackers.
4. **Review & Override:** Adjust **Defender Cover**, strike **Location**, **Face** sub-location, **Left/Right** side, damage **Aspect**, **Impact**, or **Armor** on the fly.
5. **Apply Result:** Applies wounds to the defender, updates Combat Tracker status, and triggers required Trauma/Save prompts.

---

## Window Interface Layout

```text
+-------------------------------------------------------------------+
|  Attack on: <Defender>                                            |
+-------------------------------------------------------------------+
|  [Link] <Attacker>  vs.  <Defender>  [Pending (N)]       [Link]   |
|  Defender Status: Wounds 2 | Fatigue 1 | PP 15 | Prone            |
+-------------------------------------------------------------------+
|  Attack:        Broadsword                                        |
|  Attacker Test: [ Marginal Success ▼ ]                            |
|  Defense:       [ Block ▼ ]                 [ Block ]   [ Dodge ] |
|  Defender Test: [ Marginal Failure ▼ ]                            |
|  Defender Cover:[ None ▼ ]                                        |
|  Result:        A*2 - Attacker Strike (x2)                        |
|  [ Announce to Chat ]              [ Roll Damage (x2) ]           |
+-------------------------------------------------------------------+
|  HITS                                                [Edit] [+]   |
|  Location         Aspect      Imp     Arm     Eff     IL          |
|  L. Shoulder      [Edge ▼]    [12]    [ 5]     7      S3          |
+-------------------------------------------------------------------+
|  [ Skull ]   [ Face ]   [> L. Shoulder <]   [ Thorax ]   [ Thigh ]|
|  [ Left ]    [ Right ]                                            |
+-------------------------------------------------------------------+
|  [ Apply Result ]                          [ Cancel ]             |
+-------------------------------------------------------------------+
|  ACTIONS (Defender / Attacker toggle when applicable)             |
+-------------------------------------------------------------------+
```

---

## 1. Header & Status Bar

* **Open Attacker / Defender Sheet Buttons *(link icons left & right)*:** Opens the attacker's or defender's character/NPC sheet directly for quick stat or gear checks.
* **Matchup Line:** Displays `Attacker vs. Defender`.
* **Pending (`N`) / Counterstrike Jump Button:** Appears when additional unresolved CRWs are queued or when a linked Counterstrike CRW exists. Click to jump straight to the next pending resolution window (or switch to the linked Counterstrike window).
* **Defender Status Line:** Live readout of the defender's current wounds, fatigue, Physical Penalty, and active Combat Tracker conditions.

---

## 2. Roll Results Panel

| Control / Field | Type | What It Shows or Does |
|---|---|---|
| **Attack** | Read-only | Attacking weapon, spell, or unarmed action name. |
| **Attacker Test** | Cycler | rolled degree (**Critical Success**, **Marginal Success**, **Marginal Failure**, **Critical Failure**); click to override manually. |
| **Defense** | Cycler | Defender's reaction (**Block**, **Counterstrike**, **Dodge**, **Ignore**). Selecting **Ignore** treats defense as Critical Failure automatically. |
| **One-Click `Block`** | Button | Rolls a **Block** check using the defender's highest equipped weapon/shield DML (alerts chat if no blocking weapon is equipped). |
| **One-Click `Dodge`** | Button | Rolls a **Dodge** check using the defender's Dodge skill (or Agility-based fallback). |
| **Defender Test** | Cycler | Defender's rolled degree; click to override manually. |
| **Defender Cover** | Cycler | Cycles **None**, **Low**, **High**, and **Full** cover; automatically reflects Modifier Box cover tags and recalculates covered strike-location protection. |
| **Result** | Read-only | Color-coded combat matrix outcome (`A*N` Attacker Strike, `M*N` Missile Hit, `B*N` Mutual Strike, `D*N` Defender Counterstrike, `ATA`/`DTA` Tactical Advantage, `AF`/`DF`/`BF` Fumble, `AS`/`DS`/`BS` Stumble, `Block`, `Miss`, `Wild Shot`). |
| **Announce to Chat** | Button | Broadcasts the current matchup and matrix outcome to players in chat and updates the label to **Announced**. |
| **Roll Damage (`xN`)** *(contextual)* | Button | Appears automatically beside **Announce to Chat** for NPC attackers when the matrix grants a hit multiplier (`A*N`, `M*N`, `B*N`). Click to roll the NPC's weapon/action damage directly into this CRW. |

---

## 3. Hits Table (Single & Multi-Hit Resolution)

Supports both single-strike melee/missile hits and multi-hit flurries or spells:

* **`+` (Add Hit Location) & Edit Buttons *(header right)*:** Manually append another strike row or toggle delete mode to remove extra hit rows.
* **Click Any Hit Row:** Selects that row as the active target for the Hit Location, Face Sub-Location, and Left/Right Side override grids below.

| Column | Type | What It Shows or Does |
|---|---|---|
| **Location** | Read-only | Struck body location (including *Left* / *Right* or *Face* sub-part when selected). |
| **Aspect** | Cycler | Cycles **Blunt**, **Edge**, **Point**, and **Fire** for that hit; immediately recalculates against location armor. |
| **Imp (Total Impact)** | Editable | Rolled impact (automatically incorporates matrix multiplier and creature size difference). Edit directly for manual adjustments. |
| **Arm (Armor)** | Editable | Defender's armor protection at that location (including obstacle cover protection when **Defender Cover** covers that location). Edit to override. |
| **Eff (Effective Impact)** | Read-only | Net impact after armor (`Imp - Arm`). |
| **IL (Injury Level)** | Read-only | Computed injury severity (`M1`, `S2`–`S3`, `G4`–`G5`, etc.). |

---

## 4. Hit Location, Face Sub-Location & Side Grids

* **Strike Location Buttons:** Highlights the rolled strike location in red. Hovering covered locations notes active cover protection. Click any location button to override the selected hit row and recalculate armor and Injury Level immediately.
* **Face Sub-Location Grid:** Appears automatically whenever **Face** is selected, offering clickable buttons for **Eye**, **Cheek**, **Nose**, **Mouth**, **Jaw**, and **Ear**.
* **Lateral Side Selector (`Left` / `Right`):** Appears automatically whenever a lateral body part (or *Eye* / *Ear*) is selected, highlighting the rolled side and letting the GM switch **Left** vs. **Right** with one click.

---

## 5. NPC Actions Drawer

When either combatant is an NPC, the **ACTIONS** panel at the bottom displays that NPC's Combat Tracker actions so the GM can inspect traits or trigger follow-up rolls directly from the CRW. If both combatants are NPCs, an **Attacker / Defender** toggle button in the **ACTIONS** header switches which NPC's actions are displayed.

---

## 6. Apply Result, Cancel & Counterstrike Windows

* **Apply Result:**
  * Writes each calculated injury onto the defender's **Injuries** list (updating **Wounds**, **UP**, and **PP** across the character sheet and Combat Tracker).
  * Posts the resolved injury summary and triggers required **Shock**, **Stumble**, **Knockback**, **Kill Roll**, or **Amputation** prompts/buttons when applicable.
  * Closes the CRW.
* **Cancel:** Closes the CRW without applying any wounds or status changes.
* **Counterstrike Handling:** Choosing **Counterstrike** compares both attack rolls on the matrix. When the defender wins a counterstrike (`D*N` or mutual `B*N`), the ruleset creates a linked counterstrike CRW with roles reversed; use the header's **Counterstrike** jump button to switch directly between the two linked windows.
