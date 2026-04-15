# Tiamat Character Browser — Claude Development Log

## Project Overview
A single-file D&D campaign management web app for the "Tiamat" world.
**File:** `Tiamat_Character_Browser.html` (30,000+ lines, self-contained)
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
- Iter 190: Random Encounter Generator — 6 terrains × 10 encounters each with CR/XP ← CURRENT

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
- [ ] Spell compendium with full descriptions
- [ ] Monster stat block generator
- [ ] NPC relationship strength (like/dislike/trust meter)

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
