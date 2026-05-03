# SOURCE ANALYSIS - File Structure & Content

**Document:** Source Code Analysis  
**Created:** 2026-05-03  
**Purpose:** Detailed analysis of source files and structure

---

## OVERVIEW

This document provides a comprehensive analysis of all source materials available for the Vietnamese translation project.

---

## SOURCE LOCATIONS

### 1. Chinese Source (Original Game Data)

**Location:** `refs/cn/`

**Statistics:**
- Total files: 1,748 files
- Total size: Unknown (larger than translation files)
- Format: XML, TXT, various config files
- Status: Official game data, complete

**Structure:**
```
Settings/
├── Achievement/
├── AreaTypeDef/
├── Behaviour/
├── Biomes/
├── BiomesReplaceR/
├── Blueprint/
├── Blueprint_en/
├── CommandDef/
├── Comment/
├── Display/
├── ElixirGas/
├── Esoterica/
├── Fight/
├── font.txt
├── Fun/
├── HumanoidEvolution/
├── IllustratedHand/
├── Input/
├── Jianghu/
├── JobDef/
├── Language/
│   └── OfficialEnglish/
├── LingShou/
├── MapStories/
├── Model/
├── Modifiers/
├── MsgShow/
├── Mutation/
├── Npc/
├── NpcBiography/
├── NpcRolepaint/
├── NpcStories/
├── Outspread/
├── PlantGroups/
├── Practice/
├── Property/
├── Rewards/
├── Sacrifices/
├── SeasonAffix/
├── Secrets/
├── Tang/
├── Teaching/
├── TerrainDef/
├── ThingDef/
├── Trade/
├── Ui/
├── Weather/
├── World/
└── Zhen/
```

---

### 2. English Translation (Official Reference)

**Location:** `refs/en/`

**Statistics:**
- Total files: 969 files
- Total size: ~17.3 MB
- Format: XML, Dictionary (tab-separated TXT)
- Status: Official translation, complete

**Structure:**
```
OfficialEnglish/
├── UIText.xml                  (3,583 lines)
├── CodeDictionary.txt          (4,435 lines)
├── MapStoryDictionary.txt      (1,897 lines)
├── Settings/                   (~600 files)
│   ├── Npc/
│   ├── ThingDef/
│   ├── Practice/
│   ├── World/
│   ├── Ui/
│   ├── Comment/
│   └── [... 40+ more modules]
└── SL/                         (177 files)
    ├── Assets/Resources/FightMap/
    ├── Settings/TeachFile/
    └── Settings/RPG/Maps/
```

---

### 3. Thai Translation (Community Template)

**Location:** `./Language/Th/`

**Statistics:**
- Total files: 965 files
- Total size: ~17.3 MB
- Format: XML, Dictionary (tab-separated TXT)
- Status: Community mod, complete
- Authors: ThaiByTheEmpty (Main) & Tz_TonZa (Sub)

**Structure:**
```
Th/
├── UIText.xml                  (3,547 lines)
├── CodeDictionary.txt          (4,435 lines)
├── MapStoryDictionary.txt      (1,897 lines)
├── Settings/                   (~600 files)
│   ├── font.txt                (NotoSansThai-VariableFont_wdth,wght)
│   ├── Npc/                    (55 files)
│   ├── ThingDef/               (74 files)
│   ├── Practice/               (79 files)
│   ├── World/                  (24 files)
│   ├── Ui/                     (11 files)
│   ├── Comment/                (12 files)
│   └── [... 40+ more modules]
└── SL/                         (177 files)
    ├── Assets/Resources/FightMap/      (61 folders)
    ├── Settings/TeachFile/             (43 folders)
    └── Settings/RPG/Maps/              (35 folders)
```

---

## FILE FORMAT ANALYSIS

### Format 1: UIText.xml

**Purpose:** Main UI text strings

**Format:**
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="0xrxw6g7qkn8ovp3-n143_bpyo" mz="confirm">Combine</string>
    <string name="0xrxw6g7rz8yjt-n18_izp4" mz="title">Lost Childhood</string>
    ...
</resources>
```

**Characteristics:**
- XML format
- Unique ID in `name` attribute (DO NOT CHANGE)
- Label hint in `mz` attribute (for reference only)
- Text content between tags (TRANSLATE THIS)
- May contain format strings: `{0}`, `{1:N0}`
- May contain color tags: `[color=#D06508]...[/color]`

**Translation Rules:**
- Preserve `name` attribute exactly
- Preserve `mz` attribute exactly
- Translate text content only
- Preserve all format strings
- Preserve all color tags
- Preserve escape sequences (`\n`)

---

### Format 2: Dictionary Files (CodeDictionary.txt, MapStoryDictionary.txt)

**Purpose:** System messages, story events

**Format:**
```
Key<TAB>Value
看天花板	Looking At The Ceiling
神修在心境为"灵"时，心境已然圆满，将持续上升，不收任何外部条件影响。	When the mental state is 'spiritual', it will be fulfilled and raised at a steady pace, not affected by outside factors.
```

**Characteristics:**
- Tab-separated (NOT space)
- Column 1: Chinese text (Key) - DO NOT CHANGE
- Column 2: Translation (Value) - TRANSLATE THIS
- May contain format strings
- May contain color tags
- May contain escape sequences

**Translation Rules:**
- Column 1 (Key) MUST remain unchanged
- Column 2 (Value) translate to Vietnamese
- MUST use TAB separator (not space)
- Preserve all format strings
- Preserve all color tags
- Preserve escape sequences

---

### Format 3: Settings XML Files

**Purpose:** Game content (NPCs, items, cultivation methods, etc.)

**Format:**
```xml
<Texts Type="Other">
    <List>
        <Text Name="Gong_1_Shui">
            <DisplayName>太和十六洞天</DisplayName>
            <Desc>太一门镇派五行真诀之一，共分四大境界...</Desc>
            <SelectDesc>此功法讲究循序渐进...</SelectDesc>
            <Stages.0.DisplayName>凝气期</Stages.0.DisplayName>
            <Stages.0.Desc>修行入门之境界...</Stages.0.Desc>
            <Stages.0.Necks.0.DisplayName>摄思</Stages.0.Necks.0.DisplayName>
            <Stages.0.Necks.0.Desc>在静坐中尝试收摄心猿意马...</Stages.0.Necks.0.Desc>
        </Text>
    </List>
</Texts>
```

**Characteristics:**
- Nested XML structure
- `Name` attribute identifies the entry (DO NOT CHANGE)
- Multiple text tags: `<DisplayName>`, `<Desc>`, `<SelectDesc>`, etc.
- May have nested stages/levels
- May contain format strings and color tags

**Translation Rules:**
- Preserve XML structure exactly
- Preserve all `Name` attributes
- Translate text content in all tags
- Maintain nesting levels
- Preserve format strings and color tags

---

### Format 4: SL Dictionary Files

**Purpose:** Location names, tutorial text, map-specific content

**Format:**
```
昆仑道册-神视	KunLun Manual-Divine Sight
天柱石砖	Holy Stone Block
拜祖师	Worshipping ancestors
房间	Room
```

**Characteristics:**
- Same as Format 2 (tab-separated)
- Shorter entries (names, labels)
- Often proper nouns

**Translation Rules:**
- Same as Format 2
- Consider keeping some Chinese names (e.g., 昆仑 → Côn Lôn)
- Use established Vietnamese conventions for cultivation terms

---

## CONTENT ANALYSIS BY MODULE

### Core Files (Priority P1)

#### UIText.xml
- **Lines:** 3,583
- **Content:** All UI strings (buttons, labels, menus, tooltips)
- **Complexity:** Medium (short strings, many format strings)
- **Estimated Time:** 6-8 hours

#### CodeDictionary.txt
- **Lines:** 4,435
- **Content:** System messages, notifications, game mechanics text
- **Complexity:** Medium-High (longer text, technical terms)
- **Estimated Time:** 8-10 hours

#### MapStoryDictionary.txt
- **Lines:** 1,897
- **Content:** Story events, dialogues, narrative text
- **Complexity:** High (narrative, context-dependent)
- **Estimated Time:** 4-5 hours

---

### Settings/Practice/ (Priority P2-High) ⭐ MOST COMPLEX

**Files:** 79 files in 8 subdirectories

**Subdirectories:**
- `BodyPractice/` - Body cultivation methods
- `FabaoHelian/` - Artifact refinement
- `GodPractice/` - Divine cultivation
- `Gong/` - Cultivation techniques (19 files) **CORE**
- `Magic/` - Magic abilities
- `RandomGong/` - Random cultivation methods
- `Spell/` - Spells and techniques
- `Tree/` - Skill trees

**Content:** Cultivation methods, realms, breakthroughs, techniques

**Complexity:** **VERY HIGH**
- Deep nested XML structures
- Cultivation-specific terminology
- Cultural context critical
- Requires understanding of xianxia concepts

**Key Terms:**
- 修炼 (xiū liàn) → tu luyện (cultivation)
- 境界 (jìng jiè) → cảnh giới (realm)
- 凝气期 (níng qì qī) → Ngưng Khí kỳ (Qi Condensation)
- 筑基 (zhù jī) → Trúc Cơ (Foundation Establishment)
- 金丹 (jīn dān) → Kim Đan (Golden Core)
- 元婴 (yuán yīng) → Nguyên Anh (Nascent Soul)
- 化神 (huà shén) → Hóa Thần (Soul Formation)

**Estimated Time:** 20-25 hours

---

### Settings/Npc/ (Priority P2)

**Files:** 55 files in 10 subdirectories

**Subdirectories:**
- `Backstories/` - Character backgrounds
- `Body/` - Body types (14 files)
- `Damages/` - Damage types
- `Experience/` - Experience definitions
- `Favour/` - Favor/relationship system
- `Features/` - Character features (9 files)
- `Moods/` - Mood states
- `Race/` - Races (10 files)
- `Reincarnate/` - Reincarnation system
- `Relation/` - Relationships

**Content:** NPCs, races, character attributes, relationships

**Complexity:** Medium
- Character terminology
- Personality traits
- Relationship terms

**Estimated Time:** 10-12 hours

---

### Settings/ThingDef/ (Priority P2)

**Files:** 74 files in 6 subdirectories

**Subdirectories:**
- `Building/` - Buildings (15 files)
- `Item/` - Items
- `Plant/` - Plants
- `Rock/` - Rocks/minerals
- `RSThingType/` - Thing types
- `ThingNpc.xml` - NPC-related things

**Content:** Items, buildings, plants, materials

**Complexity:** Medium
- Item names
- Material terminology
- Building descriptions

**Estimated Time:** 12-15 hours

---

### Settings/Display/ (Priority P2)

**Files:** 66 files in 7 subdirectories

**Subdirectories:**
- `ArtItem/` - Artifact names
- `EsotericaName/` - Esoteric technique names
- `FabaoName/` - Magic treasure names
- `NpcName/` - NPC name generators
- `NpcTitle/` - NPC titles
- `RandomGong/` - Random technique names
- `SpecialName/` - Special names

**Content:** Display names, titles, generated names

**Complexity:** Medium
- Naming conventions
- Title formatting
- Cultural appropriateness

**Estimated Time:** 8-10 hours

---

### Settings/World/ (Priority P2)

**Files:** 24 files

**Content:** World generation, biomes, regions, settings

**Complexity:** Medium
- Geographic terms
- World-building terminology

**Estimated Time:** 4-5 hours

---

### Settings/Ui/ (Priority P1)

**Files:** 11 files

**Content:** UI elements, interface components

**Complexity:** Low-Medium
- UI terminology
- Short labels

**Estimated Time:** 2-3 hours

---

### Settings/Comment/ (Priority P1)

**Files:** 12 files

**Content:** Tooltips, help text, explanations

**Complexity:** Medium
- Explanatory text
- Game mechanics descriptions

**Estimated Time:** 2-3 hours

---

### Other Settings Modules (Priority P3)

**Modules:**
- MapStories/ (25 files) - Story events
- Teaching/ (5 files) - Tutorials
- Jianghu/ (13 files) - Martial world system
- Esoterica/ (13 files) - Secret techniques
- Modifiers/ (37 files) - Game modifiers
- Trade/ (36 files) - Trading system
- Zhen/ (13 files) - Formation arrays
- LingShou/ (15 files) - Spirit beasts
- Mutation/ (10 files) - Mutations
- NpcStories/ (8 files) - NPC stories
- NpcBiography/ (2 files) - NPC biographies
- RPG/ (24 files) - RPG mode
- Property/ (7 files) - Properties
- Secrets/ (2 files) - Secrets
- Outspread/ (14 files) - Expansion content
- Weather/ (6 files) - Weather system
- HumanoidEvolution/ (8 files) - Evolution
- Fight/ (15 files) - Combat system
- MsgShow/ (3 files) - Message display
- JobDef/ (8 files) - Job definitions
- Cosmetics/ (1 file) - Cosmetics
- ElixirGas/ (1 file) - Alchemy
- TerrainDef/ (2 files) - Terrain
- Achievement/ (1 file) - Achievements
- Tang/ (1 file) - Tang dynasty content
- Input/ (1 file) - Input settings
- IllustratedHand/ (1 file) - Handbook
- SeasonAffix/ (1 file) - Season modifiers
- GameGraphAffix/ (1 file) - Graph effects
- CommandDef/ (1 file) - Commands
- Sacrifices/ (2 files) - Sacrifice system
- Rewards/ (2 files) - Rewards
- Reward/ (3 files) - Individual rewards
- Fun/ (1 file) - Fun content
- Share/ (1 file) - Sharing
- PlantGroups/ (3 files) - Plant groups

**Total Files:** ~200 files

**Estimated Time:** 47 hours

---

### SL/ Folder (Priority P4)

**Files:** 177 dictionary files

**Structure:**
- `SL/Assets/Resources/FightMap/` - 61 battle map locations
- `SL/Settings/TeachFile/` - 43 tutorial files
- `SL/Settings/RPG/Maps/` - 35 RPG maps
- `SL/Assets/Resources/TeachSave/` - 1 teaching save file

**Content:** Location names, tutorial text, map-specific strings

**Complexity:** Low-Medium
- Mostly short strings
- Proper nouns
- Location names

**Estimated Time:** 26-33 hours (can split among 2-3 agents)

---

## FILE MAPPING

### Chinese → English → Thai → Vietnamese

**Example 1: Practice/Gong/Gong_1.xml**

```
Chinese Source:
refs/cn/Practice/Gong/Gong_1.xml

English Reference:
refs/en/Settings/Practice/Gong/Gong_1.xml

Thai Template:
./Language/Th/Settings/Practice/Gong/Gong_1.xml

Vietnamese Output:
./Language/Vi/Settings/Practice/Gong/Gong_1.xml
```

**Example 2: UIText.xml**

```
Chinese Source:
(Not available as separate file - embedded in game code)

English Reference:
refs/en/UIText.xml

Thai Template:
./Language/Th/UIText.xml

Vietnamese Output:
./Language/Vi/UIText.xml
```

---

## SPECIAL CONSIDERATIONS

### 1. Font Configuration

**Thai uses:** `NotoSansThai-VariableFont_wdth,wght`  
**Vietnamese should use:** `NotoSans-VariableFont_wdth,wght` (supports Vietnamese)

**File:** `Settings/font.txt`

---

### 2. Encoding

**All files MUST be UTF-8**
- No BOM (unless original has BOM)
- Vietnamese diacritics must display correctly
- Test in game to verify

---

### 3. Format String Examples

**Common patterns:**
- `{0}` - Single placeholder
- `{0:N0}` - Number with thousand separator
- `{0:F2}` - Float with 2 decimals
- `{0}/{1}` - Ratio (e.g., "150/5000")
- `{0}天` - Number + unit (e.g., "5 days")

**Vietnamese adaptation:**
- `{0}天` → `{0} ngày` (add space before unit)
- `{0}个` → `{0}` (Vietnamese doesn't need classifier in this context)

---

### 4. Color Tag Examples

**Pattern:** `[color=#RRGGBB]text[/color]`

**Common colors:**
- `#D06508` - Orange (warnings, important info)
- `#880000` - Dark red (errors)
- Others as needed

**MUST preserve exactly** - do not change color codes or tag structure

---

## SUMMARY STATISTICS

| Category | Files | Size | Priority | Est. Hours |
|----------|-------|------|----------|------------|
| Core (UI + Dictionaries) | 3 | Large | P1 | 18-23h |
| Practice/ | 79 | Medium | P2-High | 20-25h |
| Npc/ | 55 | Medium | P2 | 10-12h |
| ThingDef/ | 74 | Medium | P2 | 12-15h |
| Display/ | 66 | Small | P2 | 8-10h |
| World/ | 24 | Small | P2 | 4-5h |
| Ui/ | 11 | Small | P1 | 2-3h |
| Comment/ | 12 | Small | P1 | 2-3h |
| Other Settings | ~200 | Medium | P3 | 47h |
| SL/ | 177 | Medium | P4 | 26-33h |
| **TOTAL** | **969** | **~17.3MB** | | **155-191h** |

---

## NEXT STEPS

1. **Read** `02_TRANSLATION_PLAN.md` for detailed translation strategy
2. **Read** `03_AGENT_ARCHITECTURE.md` for agent design
3. **Create** GLOSSARY.md before starting translation
4. **Start** with Phase 0 (Setup) then Phase 1 (GLOSSARY)

---

**Document Version:** 1.0  
**Last Updated:** 2026-05-03T02:45:30.211Z  
**Status:** Complete
