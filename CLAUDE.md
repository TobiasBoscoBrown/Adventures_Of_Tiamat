# Tiamat Character Browser — Claude Development Log

## Project Overview
A single-file D&D campaign management web app for the "Tiamat" world.
**File:** `Tiamat_Character_Browser.html` (42,000+ lines, self-contained)
**Goal:** Make this the ultimate DM tool — better than DND Beyond, with full user control.

## Architecture
- Single HTML file: embedded CSS + JS + character data
- No build step required — open in any browser
- localStorage for persistence (HP, conditions, notes, pins, etc.)
- Character data in `const CHARS = [...]` array starting at line ~5011
- PDF.js for character sheet rendering
- Tiamat Map.jpg in root for world map

## Character Data Structure
```js
{
  name: "Character Name",
  title: "Role · Race · Class",
  subtitle: "Born XXXX A.T. · Alignment",
  theme: "royal|warrior|arcane|nature|shadow|fire|ocean|stone|orc|pink",
  group: "royals|power|colorful|kubi|gondor|misc",
  cr: "20", hp: "262", ac: "19",
  quote: "Iconic quote",
  abilities: [["STR",18,"+4",1],["DEX",18,"+4",1],...], // [name, score, modStr, saveProficient]
  traits: ["Trait 1", "Trait 2"],
  lore: "Character backstory and DM notes",
  // Optional: spells, speed, senses, resistances, languages
}
```

## Iteration Log (what's been built)

### Iterations 1–90 (Pre-log)
Core character browser, search/filter, dark theme, tooltips, view modes.

### Iterations 91–100
- Iter 91: Rich dice roll system with crit/fumble detection
- Iter 92: Quick HP ±5 buttons  
- Iter 93: Editable characteristics (DnD Beyond style)
- Iter 94: Enhanced speed/senses from theme + custom override
- Iter 95: Weapons list render
- Iter 96: Physical description panel

### Iterations 101–110
- Iter 101: Target AC check on attack rolls
- Iter 102: Spell name detection (SPELL_LIBRARY lookup)
- Iter 103: Condition badges clickable with effect descriptions

### Iterations 111–120
- Relationship map (SVG visualization of NPC connections)
- Spell prepared tracker (toggle prepared/unprepared)

### Iterations 121–130
- Iter 121: Encounter Difficulty Calculator — XP thresholds by party level
- Iter 122: Concentration Save Helper — CON save when taking damage
- Iter 123: Action Economy Tracker — track action/bonus/reaction used
- Iter 124: NPC Dialog Generator — quick dialog from personality
- Iter 125: Quick Damage Calculator — roll attack + damage vs AC in one click
- Iter 126: Encounter difficulty button in toolbar
- Iter 127: Print Party Sheet — all party members on one printable page
- Iter 128: Dialog generator + action economy integrated into modal
- Iter 129: Damage Type Vulnerability/Resistance quick reference
- Iter 130: Keyboard shortcuts (Q=quick attack, E=encounter diff, ?=help, i/h/n/t/r)

### Iterations 131–140
- Iter 131: Interactive World Map — pin characters to Tiamat map (full-screen overlay)
- Iter 132: Relationship Sentiment Tracker — how Character A feels about Character B
- Iter 133: Per-Character XP & Level Tracker — award XP, track level progress
- Iter 134: Command Palette (Ctrl+K) — VS Code-style search over every feature
- Iter 135: Wounds & Injuries Tracker — optional gritty injury system
- Iter 136: Combat UX improvements
- Iter 137: Sort by ability score + current HP% in character grid
- Iter 138: Mass Damage/Heal — apply HP changes to multiple characters at once
- Iter 139: Overland Travel Calculator — DM tool for travel time/distance
- Iter 140: Ability Score Roller — 4d6 drop lowest for character creation

### Iterations 141–150
- Iter 141: Import Character from JSON — toolbar button + function
- Iter 142: Party Summary Panel — at-a-glance HP/conditions for all party members
- Iter 143: Improv NPC Card Generator — instant personality card for improvised NPCs
- Iter 144: Class Ability Resource Tracker — track limited-use class features
- Iter 145: Bulk Condition Apply — select multiple characters, apply/remove conditions
- Iter 147: Spell Upcast Calculator — calculate scaled spell damage at higher slots
- Iter 148: Session Timer — live duration counter in HUD (pause/resume/reset)
- Iter 149: Skill Contest Roller — opposed skill check between two characters
- Iter 150: Character Background Panel — Traits/Ideals/Bonds/Flaws tab in modal

### Iterations 151–160
- Iter 151: Magic Item Compendium — 65+ items with rarity, attunement, give-to-character
- Iter 152: Feat Compendium — 48 feats with prerequisites, stored per character
- Iter 153: Random Encounter Generator — 6 terrains × 3 CR tiers, add to initiative
- Iter 154: Appearance Tracker — Age/Height/Hair/Eyes/Skin/Features/Voice/Mannerisms
- Iter 155: Class Features Quick Reference — all 12 PHB classes, level-gated features
- Iter 156: Race Features Reference — all 10 PHB races, ASI/speed/size/traits
- Iter 157: Dungeon Room Generator — instant boxed-text room descriptions + DM notes
- Iter 158: Spell Slot Reference Table — all 3 caster types (full/half/warlock) levels 1-20
- Iter 159: Location Generator — taverns, shops, temples for improv urban play
- Iter 160: Character Level-Up Workflow — HP gain (roll/avg), prof bonus, features per level

### Iterations 161–170
- Iter 161: DM Quick Reference Screen — conditions, actions, cover, DCs in one overlay
- Iter 162: Full Spell Compendium — 80+ spells filterable by level, school, class
- Iter 163: Critical Hit & Fumble Tables — 80 dramatic effects for nat 20s and nat 1s
- Iter 164: Session Quick Facts Board — pin color-coded facts during play
- Iter 165: Roll Probability Calculator — live % chance for any DC + modifier + adv/disadv
- Iter 166: Villain Scheme Tracker — track antagonist plans, progress, minions, locations
- Iter 167: Party Role & Balance Analyzer — coverage analysis and encounter design tips
- Iter 168: Downtime Activity Tracker — log between-session activities (PHB rules)
- Iter 169: DM Secrets Panel — per-character hidden notes in BG tab + Secrets Board
- Iter 170: Character Arc Tracker — story arcs, goals, key moments, progress per NPC/PC

### Iterations 171–180
- Iter 171: Spell Range & Area Reference — cones/spheres/lines in grid squares
- Iter 172: Proficiency Checker — instantly see who has a skill/tool proficiency
- Iter 173: Encounter Morale System — group WIS saves for flee/surrender conditions
- Iter 174: Homebrew Item Builder — create/save custom magic items with full properties
- Iter 175: NPC Initial Reaction Table — d20 + CHA mod for first impressions + roleplay hints
- Iter 176: XP Split Calculator — divide XP among party with full/half/absent shares
- Iter 177: Encounter Hook Generator — narrative hooks with motive + complication + twist
- Iter 178: Caster Combat Card — per-NPC spell sheet with attack bonus, save DC, roll buttons
- Iter 179: Session Achievement Badges — award roleplay/combat badges to characters
- Iter 180: Campaign Stats Dashboard — visual overview of all campaign data and totals

### Iterations 181–190
- Iter 181: Encounter Countdown Timer — floating HUD widget with color shifts and alarm
- Iter 182: Multi-Damage-Type Roll Calculator — composite damage (e.g. 2d6fire+1d4cold) with per-type totals
- Iter 183: Party Spell Slot Panel — track all caster slots in one place with long-rest button
- Iter 184: NPC Schedule & Patrol Tracker — track where NPCs are at each time of day
- Iter 185: Encounter Hazard & Lair Effect Tracker — active effects with round countdown
- Iter 186: PC Wish List & Goals Tracker — items/spells/story-goals per character
- Iter 187: ASI & Feat History Log — log ability score improvements and feats by level
- Iter 188: Magic Item Identifier & Attunement Dashboard — identify items, track 3-slot attunement
- Iter 189: Party Concentration Tracker — one-spell limit enforced, tick-all rounds, auto-expire
- Iter 190: Random Encounter Generator — 6 terrains × 10 encounters each with CR/XP

### Iterations 191–200
- Iter 191: Curse & Blessing Tracker — persistent magical effects (13 presets) per character
- Iter 192: Session Zero Checklist — 5 category, 30+ item pre-campaign setup checklist
- Iter 193: NPC Voice & Roleplay Sheet — accent, mood, quirks, opening lines per NPC
- Iter 194: Active Spell Duration Tracker — tick rounds, concentration conflict auto-detect
- Iter 195: Encounter Combat Journal — log encounters with outcome, XP, loot, rounds, notes
- Iter 196: CR vs Party Threat Assessor — real-time DMG difficulty with visual threshold bars
- Iter 197: Faction Reputation Tracker — 7-tier standing (Hostile→Exalted) for 6 factions
- Iter 198: Party Prepared Spells Overview — tab per caster, toggle prep/unprep, prepare-all
- Iter 199: Visual Initiative Board — sorted combat order, HP bars, draggable floating HUD
- Iter 200: Campaign Milestone Tracker — record story beats by category with history log

### Iterations 201–210
- Iter 201: Monster Quick-Builder — generate DMG stat blocks from CR (AC/HP/atk/DC auto-filled), save custom monsters, add to encounter
- Iter 202: Spell Card Popup — click 📖 on any spell to see full description (cast time, range, components, duration, classes)
- Iter 203: DM Scratch Pad — floating persistent sticky notepad, draggable, tab-support, persists across sessions
- Iter 204: Combat Export to Text — copy full combat state (initiative, HP, conditions) to clipboard for Discord/notes
- Iter 205: Bloodied/Critical HP Alerts — cards pulse with animated border glow at ≤50% (bloodied) and ≤25% (critical)
- Iter 206: Party Save Roller — roll any save for ALL party members at once with adv/dis toggle (great for AOE spells)
- Iter 207: Random Tables Roller — d8–d20 tables for weather, NPC traits, motivation, shop names, tavern events, plot twists
- Iter 208: Treasure & Loot Generator — DMG individual and hoard treasure by CR tier (gold, gems, art objects, magic items)
- Iter 209: Search History — remember last 12 searches, show on focus for quick recall
- Iter 210: Post-Combat Cleanup — one-click clear temp HP, conditions, and concentration for all party members after a fight

### Iterations 211–220
- Iter 211: Full Party Skill Matrix — all characters × all 18 skills in one scrollable table, color-coded by proficiency, click-to-roll, filterable by ability score
- Iter 212: Quick-Cast Spell Row in Active Turn Bar — one-click spell casting during combat; shows all spells (cantrips green, leveled purple/blue), depleted slots grayed, concentration tracked, damage auto-rolled
- Iter 213: Target Selector + Auto Hit/Miss — click any combatant as target; attack rolls show HIT/MISS/CRIT vs target AC; auto-rolls damage on hit
- Iter 214: Monster Ability Recharge Tracker — parses "Recharge X-6" from lore/traits; roll-to-recharge d6 button in active turn bar; recharged/spent log messages
- Iter 215: AOE Damage with Save-for-Half — roll damage once, apply to multiple targets with save rolls, auto-half on pass, resistance/immunity respected; 💥 toolbar button
- Iter 216: Custom Attack Macros per Character — define named attacks (name/+hit/dice/type) stored in localStorage; quick-roll buttons in active turn bar, crit doubles dice, integrates with target selector
- Iter 217: Legendary Resistance & Actions Tracker — auto-detects legendary creatures (CR 17+ or 'legendary' keyword); pip indicators for LR (3/day) and LA (3/round); round-reset and long-rest buttons
- Iter 218: Timed Effect Duration Tracker — track effects with round countdowns (Web 10r, Stunned 3r etc); 15 presets; pulse warning at ≤2 rounds; auto-expire with toast + log; tick button in active turn bar
- Iter 219: Inspiration Tracker + Bardic Inspiration Dice — toggle D&D Inspiration per character (gold star); track Bardic Inspiration dice (d6-d12) given to characters; roll dice to consume; ✨ toolbar button
- Iter 220: Concentration Save Prompt on Damage — auto-detects when concentrating caster takes damage; floating prompt with DC calculation; Roll/Pass/Fail buttons; auto-drops concentration on fail

### Iterations 221–230
- Iter 221: Round Counter + Start-of-Round Actions — persistent round counter HUD; Next Round button in initiative; resets legendary actions per round; lair action prompts at init 20
- Iter 222: HP Undo — revert last HP change per character; Ctrl+Z shortcut for current turn's character; up to 10-step history
- Iter 223: Temp HP Tracker — track temporary HP; damage absorbs temp HP first (PHB rules); teal badges in turn bar; quick-grant dialog with presets
- Iter 224: Hit Dice Manager — track hit dice per character; spend to heal on short rest (auto-rolls die+CON); long rest recovery; ❤️ toolbar button
- Iter 225: Movement Speed Tracker per Turn — remaining movement bar in active turn bar; 5/10/15/20/30ft spend buttons; Dash action; auto-resets each turn
- Iter 226: Passive Skills Quick Panel — Passive Perception/Investigation/Insight for all characters; gold star highlights best; DM reference notes; 👁 toolbar button
- Iter 227: Combat Notes per Combatant — persistent 200-char note per initiative slot; edit modal; shown as gold pill in turn bar and initiative list
- Iter 228: Damage Resistance/Immunity Icons — parses lore/traits for immunities/resistances/vulnerabilities; color-coded badges in turn bar and on character cards
- Iter 229: Spell Upcast Slot Picker — clicking leveled spells shows slot level selector; shows remaining slots; auto-detects upcast damage scaling from SPELL_LIBRARY
- Iter 230: Full Condition Reference Popup — click any condition badge to see full PHB mechanical description; 15 conditions with icon/summary/effects list; ❓ buttons in turn bar

### Iterations 231–240
- Iter 231: Reaction Tracker — track each combatant's reaction (available/used); quick buttons (OA, Shield, Counterspell etc); green/red dot in initiative list; Reset All button
- Iter 232: Party Group Ability Check Roller — roll any skill/ability for all characters; ranked results; optional DC with pass/fail count; advantage/disadvantage toggle; 🎲 Group Check toolbar
- Iter 233: Party Initiative Auto-Roll — one-click roll initiative for all party members; ranked table with DEX mod; editable overrides; add all to tracker; New Combat reset button; ⚔ Roll Init toolbar
- Iter 234: Party Saving Throw Overview Table — all 6 saves for all characters; proficiency ● indicators; color-coded (gold=best, purple=prof, red=negative); 🛡 Saves toolbar
- Iter 235: Active Turn Bar Compact Mode Toggle — ▲/▼ button collapses all extra rows to show just essentials; state persisted; reduces screen clutter
- Iter 236: Encounter XP Tally — running XP badge bottom-right; CR→XP conversion table; award XP to party splits evenly; integrates with XP tracker; manual kill form
- Iter 237: Darkness & Vision Reference — parse DV/BS/TS from senses/traits/race; Toggle Darkness shows who is Blinded; 👁 Vision toolbar; 60ft/120ft inferred by race
- Iter 238: Creature Size & Reach Reference — parse size from text/CR; Large=2×2/5ft, Huge=3×3/10ft, Gargantuan=4×4/15ft; shown in turn bar; 📐 Sizes toolbar
- Iter 239: Short / Long Rest Menu — 💤 Rest toolbar; Short Rest recovers warlock slots + opens HD panel; Long Rest: full HP/slots/concentration/exhaustion/-1/HD recovery
- Iter 240: PC Down! Handler — auto-triggers at 0 HP; centered death save overlay with roll/stabilize; nat 20 = regain 1 HP; 3 failures = dead; auto-applies Unconscious + clears concentration

### Iterations 241–250
- Iter 241: Bardic Inspiration Tracker — per-character inspiration die (d6–d12 by level); give/use buttons; who has inspiration shown in turn bar
- Iter 242: Wild Shape Tracker — Druid wild shape HP/CR pool; separate HP bar; revert when 0; uses/long-rest reset
- Iter 243: Rage Tracker — Barbarian rages per long rest; rage damage bonus; duration rounds countdown; active rage shown in turn bar
- Iter 244: Sneak Attack Reminder — Rogue sneak attack die by level; advantage/adjacent ally checker; click to roll with full damage expression
- Iter 245: Destructible Object Tracker — add objects (doors, pillars, walls) with HP/AC; damage them in combat; "destroyed" state shown
- Iter 246: Spell AoE Calculator — sphere/cube/cone/line areas in feet and grid squares; pick spell or enter custom; quick overlay panel
- Iter 247: Grapple/Shove Contest Helper — STR(Athletics) vs STR(Athletics)/DEX(Acrobatics); pick attacker+defender; rolls both sides; declares winner
- Iter 248: Party Combat Stats Overview — post-combat summary: total damage dealt/taken, crits, kills, heals per character; session-persistent counters
- Iter 249: Multiattack Roll All — characters with Multiattack trait get ⚔⚔ button; rolls all attacks at once with separate hit/damage for each
- Iter 250: Turn Bar Sections Toggle — ⚙ config button in turn bar opens checkbox panel to show/hide any section (Spells/Attacks/Movement/Effects etc); persisted in localStorage

### Iterations 251–260
- Iter 251: Stealth vs Passive Perception Checker — enter creature stealth DC; colored pass/fail for each character; active roll buttons; roll creature stealth
- Iter 252: Spell Save DC & Attack Bonus Dashboard — all casters at a glance; enter target save mod to see pass% and "always saves/fails"; quick roll button
- Iter 253: Weather & Lighting Conditions Tracker — 10 weather + 5 lighting options; mechanical effects shown as badges; HUD strip under toolbar; persisted
- Iter 254: Terrain & Environment Effects Panel — track hazards (lava, web, darkness, etc); damage roll buttons; toggle active/inactive; 12 presets + custom
- Iter 255: Trinket & Curiosity Generator — 60 themed trinkets; reroll; give to character (saves to inventory); log to session; 🎲 Trinket toolbar button
- Iter 256: Concentration Spell Duration Timer — tracks rounds elapsed; progress bar; +1r button; auto-clears and logs on expiry; warns at 1 round left
- Iter 257: Character Sheet Quick Print Card — printable 1-page HTML summary with stats, skills, spells, traits, lore; opens in new window; 🖨 Print Card toolbar
- Iter 258: Encounter Recap Generator — scans last 60 session log entries; extracts crits/downs/heals/damage; generates narrative paragraph; copy to clipboard
- Iter 259: Spell Slot Quick-Use Widget in Turn Bar — colored pips per slot level inline in active turn bar; click pip to spend slot with full cast picker
- Iter 260: Auto-Advance Turn Timer — configurable countdown (15–120s) per turn; SVG progress ring; +10s extend; auto-calls nextTurn() on expiry

### Iterations 261–270
- (Documented in previous sessions — see git log for details)

### Iterations 271–280
- (Documented in previous sessions — see git log for details)

### Iterations 281–290
- Iter 281: NPC Morale Tracker — group WIS saves for flee/surrender; morale thresholds by CR
- Iter 282: Persistent Floating Dice Tray — always-visible collapsible dice tray with history, mod, adv/dis
- Iter 283: DM Announcement Bar — persistent session-wide status message below header (Info/Warn/Danger colors)
- Iter 284: Character Status Labels — narrative status per character (Active/Deceased/Missing/Imprisoned/Unknown); filterable
- Iter 285: Character Alias/Nickname System — searchable alternate names per character (stored in localStorage, searched alongside name/lore)
- Iter 286: Character Card Right-Click Context Menu — quick actions (Open, Initiative, Encounter, Condition, HP, Status, Notes) without opening modal
- Iter 287: Card Hover Preview — 600ms hover shows compact floating stat popup (HP, AC, init, abilities, traits, lore)
- Iter 288: Player Turn Time Tracker — auto-records initiative turn duration per combatant; ⏱ Turns button shows avg/min/max analysis
- Iter 289: NPC Quick-Pitch Summary — auto-generated 2-3 sentence DM briefing shown in modal header for rapid roleplay prep
- Iter 290: Multiclass Spell Slot Calculator — PHB-accurate slot calculation for any class combo; full/half/third-casters; Warlock Pact Magic separate

## Features Currently Implemented (What We Have)
- Character browser: search, filter by category/theme, view modes (grid/compact/list)
- Per-character: ability scores, saving throws, skills, HP tracking, conditions, death saves
- Combat: initiative tracker, encounter builder, XP calculator
- Spellcasting: spell slots, concentration tracker, spell prepared toggle
- Equipment: weapons, inventory, ammo, attunement (3 max)
- DM tools: notes, session log, campaign calendar, lore browser
- Character comparison (side-by-side)
- PDF character sheet rendering (Character Sheets/*.pdf)
- Custom NPC builder
- Favorites system
- Party health panel
- Relationship map (SVG, opens from character modal)
- Multiclass support
- Exhaustion tracker (6 levels)
- Alignment compass
- Currency tracker
- Hit dice
- Passive skills (Perception/Investigation/Insight table)
- 42 PDF character sheets
- 47+ built-in NPCs across 6 factions

## DND Beyond Features Checklist (Progress Toward Clone)
- [x] Character stat blocks
- [x] HP tracking with health bar
- [x] Ability scores with modifiers
- [x] Saving throws with proficiency
- [x] Skills with proficiency indicators
- [x] Spell slots tracker
- [x] Condition tracking
- [x] Initiative tracker
- [x] Encounter builder
- [x] Dice rolling (multiple types + formulas)
- [x] Character notes
- [x] Equipment/inventory management
- [x] Death saves tracker
- [x] Exhaustion levels
- [x] Concentration tracker
- [x] Action economy tracker
- [x] Attunement tracking (3 max)
- [x] World map with character locations (Iter 131)
- [x] Character XP & level tracking (Iter 133)
- [x] Backgrounds (Traits/Ideals/Bonds/Flaws) — Iter 150
- [x] Character progression / Level-Up workflow (Iter 160)
- [x] Magic Item Compendium (Iter 151)
- [x] Feat Compendium (Iter 152)
- [x] Race & Class Feature References (Iters 155-156)
- [x] Spell compendium with full descriptions (Iter 162 + 202 spell card popups)
- [x] Monster stat block generator (Iter 201 Quick-Builder)
- [x] NPC relationship strength (Iter 132 Relationship Sentiment Tracker)
- [x] Quick-cast spells from initiative tracker (Iter 212)

## Things Better Than DND Beyond
- NPC-first design (47+ rich NPCs with lore)
- Relationship map visualization
- Campaign lore browser (integrated markdown)
- Session combat log with export
- Custom NPC builder with personality
- Dialog generator from character personality
- Quick damage calculator
- Full campaign world context
- No subscription required
- **World map with pins** (DND Beyond doesn't do homebrew maps this well)

## Files
- `Tiamat_Character_Browser.html` — Main app (everything is here)
- `Tiamat Map.jpg` — World map image (7MB, used in Iter 131)
- `Character Sheets/*.pdf` — 42 PDF character sheets
- `Tiamat/` — Obsidian lore vault (markdown files)
- `CLAUDE.md` — This file (development log)

## Development Guidelines
- Always add new code at the END of the `<script>` section with an `// Iter NNN:` comment
- Use localStorage with `tiamat_*` prefix for all persistence
- Follow existing CSS variables: `--accent`, dark theme (#06061a bg, #c9a227 gold, #9b6dff purple)
- Test by opening the HTML in a browser
- Push to main branch after each feature batch
- After every 10 iterations, send a Telegram update via /send-telegram skill
