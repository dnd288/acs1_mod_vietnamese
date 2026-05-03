# WORKFLOW - Execution Flow & Dependencies

**Document:** Workflow & Dependencies  
**Created:** 2026-05-03  
**Purpose:** Detailed workflow, dependencies, and execution guidelines

---

## WORKFLOW OVERVIEW

### Execution Model: Phased with Dependencies

```
Phase 0: SETUP (Manual)
    ↓
Phase 1: GLOSSARY (Blocking) ← MUST complete first
    ↓
Phase 2: CORE TRANSLATION (Blocking) ← MUST complete before Phase 3
    ↓
Phase 3: PARALLEL TRANSLATION ← Can run in parallel
    ├─> Practice Specialist
    ├─> NPC Specialist
    ├─> Item Specialist
    ├─> World Specialist
    ├─> UI Specialist
    ├─> System Specialist
    └─> Dictionary Specialists (2-3 agents)
    ↓
Phase 4: QUALITY CONTROL
    ├─> Format Validator (parallel)
    └─> Consistency Validator (parallel)
    ↓
Phase 5: FINALIZATION
```

---

## PHASE 0: SETUP (Manual - 30 minutes)

### Objective
Prepare Vietnamese language structure from Thai template

### Prerequisites
- Thai mod structure exists at `Language/Th/`
- Git repository initialized

### Tasks

#### Task 0.1: Copy Structure
```bash
# Copy Thai structure to Vietnamese
cp -r Language/Th Language/Vi
```

**Verification:**
```bash
# Check structure created
ls Language/Vi/
# Should show: UIText.xml, CodeDictionary.txt, MapStoryDictionary.txt, Settings/, SL/
```

#### Task 0.2: Update Info.json
**File:** `Info.json`

**Changes:**
```json
{
    "Name": "VietnameseLanguage",
    "DisplayName": "Vietnamese Language",
    "Desc": "Bản dịch tiếng Việt cho Amazing Cultivation Simulator",
    "Author": "Vietnamese Translation Team",
    "Sort": "9999999"
}
```

#### Task 0.3: Update Language/Config.xml
**File:** `Language/Config.xml`

**Changes:**
```xml
<Languages><List>
    <Language Name="Vi">
        <DisplayName>Tiếng Việt</DisplayName>
        <Icon>viflag.png</Icon>
        <UIMode>1</UIMode>
        <Desc>Vietnamese Language Pack</Desc>
        <SpaceConnect>true</SpaceConnect>
        <FamilyPostposition>false</FamilyPostposition>
        <Labels>
            <li Label="[ENHIM]" SecondPersonF="cô ấy" SecondPersonM="anh ấy"/>
            <li Label="[ENHERS]" SecondPersonF="của cô ấy" SecondPersonM="của anh ấy"/>
            <li Label="[ENHIM2]" ThirdPersonF="cô ấy" ThirdPersonM="anh ấy"/>
            <li Label="[ENHERS2]" ThirdPersonF="của cô ấy" ThirdPersonM="của anh ấy"/>
        </Labels>
    </Language>
</List></Languages>
```

#### Task 0.4: Update Font Configuration
**File:** `Language/Vi/Settings/font.txt`

**Changes:**
```
NotoSans-VariableFont_wdth,wght
```

#### Task 0.5: Create Vietnamese Flag Icon
**File:** `Resources/viflag.png`

**Requirements:**
- PNG format
- Similar size to `thflag.png`
- Vietnamese flag design

#### Task 0.6: Update Preview Image (Optional)
**File:** `Preview.png`

**Requirements:**
- Update to show "Vietnamese Language"
- Keep similar style to original

### Deliverables
- ✅ `Language/Vi/` structure created
- ✅ `Info.json` updated
- ✅ `Language/Config.xml` updated
- ✅ `Language/Vi/Settings/font.txt` updated
- ✅ `Resources/viflag.png` created
- ✅ `Preview.png` updated (optional)

### Next Phase
**Phase 1: GLOSSARY** (BLOCKING - must complete before translation)

---

## PHASE 1: GLOSSARY (Blocking - 4-6 hours)

### Objective
Create comprehensive cultivation terminology glossary

### Prerequisites
- Phase 0 complete
- Access to Chinese source files
- Access to English reference files

### Agent
**Glossary Builder Agent**

### Instruction File
`docs/agents/01_GLOSSARY_BUILDER.md`

### Input Files
- Chinese: `refs/cn/Practice/`
- Chinese: `refs/cn/Npc/`
- English: `refs/en/`

### Output Files
- `GLOSSARY.md` (200-300 terms)

### Process

1. **Extract Terms**
   - Scan Practice/ for cultivation terms
   - Scan Npc/ for character terms
   - Identify high-frequency terms
   - Categorize by type (realms, techniques, items, etc.)

2. **Research Vietnamese Conventions**
   - Check Vietnamese cultivation novel translations
   - Verify community standards
   - Ensure cultural appropriateness

3. **Create Mappings**
   - Chinese term (simplified)
   - Vietnamese translation
   - Pinyin (for reference)
   - English translation
   - Usage notes

4. **Validate**
   - Check consistency
   - Verify accuracy
   - Test with sample translations

### Deliverables
- ✅ `GLOSSARY.md` created
- ✅ All cultivation terms mapped
- ✅ Consistency verified

### Blocking
**This phase BLOCKS all translation phases**
- No translation can start without GLOSSARY
- All agents depend on GLOSSARY for terminology

### Next Phase
**Phase 2: CORE TRANSLATION**

---

## PHASE 2: CORE TRANSLATION (Blocking - 18-23 hours)

### Objective
Translate 3 most critical files

### Prerequisites
- Phase 1 complete (GLOSSARY.md exists)
- `Language/Vi/` structure ready

### Agent
**Core Translation Agent**

### Instruction File
`docs/agents/02_CORE_TRANSLATION.md`

### Tasks

#### Task 2.1: UIText.xml (6-8 hours)

**Input:**
- English: `refs/en/UIText.xml`
- Template: `Language/Vi/UIText.xml`
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/UIText.xml` (3,583 lines translated)

**Process:**
1. Read English source line by line
2. For each `<string>` entry:
   - Translate text content
   - Preserve `name` and `mz` attributes
   - Preserve format strings
   - Preserve color tags
   - Check GLOSSARY for terms
3. Write to Vietnamese file
4. Validate XML well-formedness

#### Task 2.2: CodeDictionary.txt (8-10 hours)

**Input:**
- English: `refs/en/CodeDictionary.txt`
- Template: `Language/Vi/CodeDictionary.txt`
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/CodeDictionary.txt` (4,435 lines translated)

**Process:**
1. Read English source line by line
2. For each line:
   - Keep Column 1 (Chinese Key) unchanged
   - Translate Column 2 (English Value) to Vietnamese
   - Use TAB separator
   - Preserve format strings and color tags
   - Check GLOSSARY for terms
3. Write to Vietnamese file
4. Validate format (tab-separated)

#### Task 2.3: MapStoryDictionary.txt (4-5 hours)

**Input:**
- English: `refs/en/MapStoryDictionary.txt`
- Template: `Language/Vi/MapStoryDictionary.txt`
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/MapStoryDictionary.txt` (1,897 lines translated)

**Process:** Same as Task 2.2

### Deliverables
- ✅ `Language/Vi/UIText.xml` translated
- ✅ `Language/Vi/CodeDictionary.txt` translated
- ✅ `Language/Vi/MapStoryDictionary.txt` translated
- ✅ All format strings preserved
- ✅ All color tags preserved
- ✅ XML validation passed
- ✅ Dictionary format validated

### Blocking
**This phase BLOCKS Phase 3**
- Recommended to complete before starting specialist agents
- Provides foundation for understanding game terminology

### Next Phase
**Phase 3: PARALLEL TRANSLATION**

---

## PHASE 3: PARALLEL TRANSLATION (100-120 hours)

### Objective
Translate all Settings/ modules using specialized agents

### Prerequisites
- Phase 1 complete (GLOSSARY.md exists)
- Phase 2 complete (recommended, not strictly required)

### Execution Strategy
**Run 7-8 agents in parallel**

### Agents & Tasks

#### Agent 3.1: Practice Specialist (20-25 hours) ⭐

**Priority:** P2-High (Most complex)

**Files:** 79 files in `Settings/Practice/`

**Instruction:** `docs/agents/03_PRACTICE_SPECIALIST.md`

**Input:**
- Chinese: `refs/cn/Practice/`
- English: `refs/en/Settings/Practice/`
- Template: `Language/Vi/Settings/Practice/`
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/Settings/Practice/` (79 files translated)

**Special Requirements:**
- Deep understanding of cultivation concepts
- MUST use GLOSSARY for all cultivation terms
- Handle nested XML structures
- Preserve cultural context

---

#### Agent 3.2: NPC Specialist (10-12 hours)

**Priority:** P2

**Files:** 55 files in `Settings/Npc/`

**Instruction:** `docs/agents/04_NPC_SPECIALIST.md`

**Input:**
- Chinese: `refs/cn/Npc/`
- English: `refs/en/Settings/Npc/`
- Template: `Language/Vi/Settings/Npc/`
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/Settings/Npc/` (55 files translated)

---

#### Agent 3.3: Item Specialist (12-15 hours)

**Priority:** P2

**Files:** 74 files in `Settings/ThingDef/`

**Instruction:** `docs/agents/05_ITEM_SPECIALIST.md`

**Input:**
- Chinese: `refs/cn/ThingDef/`
- English: `refs/en/Settings/ThingDef/`
- Template: `Language/Vi/Settings/ThingDef/`
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/Settings/ThingDef/` (74 files translated)

---

#### Agent 3.4: World Specialist (17-21 hours)

**Priority:** P2

**Files:** 115 files in `Settings/World/`, `Settings/Display/`, `Settings/MapStories/`

**Instruction:** `docs/agents/06_WORLD_SPECIALIST.md`

**Input:**
- Chinese sources for World/, Display/, MapStories/
- English references
- Templates
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/Settings/World/` (24 files)
- `Language/Vi/Settings/Display/` (66 files)
- `Language/Vi/Settings/MapStories/` (25 files)

---

#### Agent 3.5: UI Specialist (4-6 hours)

**Priority:** P1

**Files:** 23 files in `Settings/Ui/`, `Settings/Comment/`

**Instruction:** `docs/agents/07_UI_SPECIALIST.md`

**Input:**
- Chinese sources for Ui/, Comment/
- English references
- Templates
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/Settings/Ui/` (11 files)
- `Language/Vi/Settings/Comment/` (12 files)

---

#### Agent 3.6: System Specialist (47 hours)

**Priority:** P3

**Files:** ~200 files across 23+ modules

**Instruction:** `docs/agents/08_SYSTEM_SPECIALIST.md`

**Input:**
- Chinese sources for all remaining Settings/ modules
- English references
- Templates
- GLOSSARY: `GLOSSARY.md`

**Output:**
- All remaining Settings/ files translated

---

#### Agent 3.7: Dictionary Specialists (26-33 hours, 2-3 agents)

**Priority:** P4

**Files:** 177 files in `SL/`

**Instruction:** `docs/agents/09_DICTIONARY_SPECIALIST.md`

**Input:**
- English: `refs/en/SL/`
- Template: `Language/Vi/SL/`
- GLOSSARY: `GLOSSARY.md`

**Output:**
- `Language/Vi/SL/` (177 files translated)

**Split Strategy:**
- Agent 3.7a: FightMap/ (61 folders) - 10-12h
- Agent 3.7b: TeachFile/ (43 folders) - 8-10h
- Agent 3.7c: RPG/Maps/ + TeachSave/ (36 files) - 8-11h

---

### Parallel Execution Timeline

**Day 4-10 (7 days):**

All agents run simultaneously:
- Practice Specialist: 20-25h → 3-4 days
- NPC Specialist: 10-12h → 1-2 days
- Item Specialist: 12-15h → 2 days
- World Specialist: 17-21h → 2-3 days
- UI Specialist: 4-6h → 1 day
- System Specialist: 47h → 6 days
- Dictionary Specialists x3: 9-11h each → 1-2 days each

**Longest:** System Specialist (6 days)

### Deliverables
- ✅ All 969 files translated
- ✅ All format strings preserved
- ✅ All color tags preserved
- ✅ GLOSSARY followed consistently
- ✅ XML structures preserved
- ✅ Dictionary formats correct

### Next Phase
**Phase 4: QUALITY CONTROL**

---

## PHASE 4: QUALITY CONTROL (10-13 hours)

### Objective
Validate all translated files for format and consistency

### Prerequisites
- Phase 3 complete (all files translated)

### Execution Strategy
**Run 2 validators in parallel**

### Validators

#### Validator 4.1: Format Validator (4-5 hours)

**Agent:** Format Validator Agent

**Instruction:** `docs/agents/10_FORMAT_VALIDATOR.md`

**Input:**
- All files in `Language/Vi/`

**Checks:**
1. **XML Validation**
   - All XML files well-formed
   - No unclosed tags
   - Attributes preserved correctly

2. **Dictionary Format**
   - Tab-separated (not space)
   - Key column unchanged
   - No empty lines or format errors

3. **Encoding**
   - All files UTF-8
   - Vietnamese diacritics display correctly
   - No corrupted characters

4. **Format Strings**
   - All `{0}`, `{1:N0}`, etc. preserved
   - All `[NAME]`, `[PLACE]`, etc. preserved
   - All `\n`, `\t` preserved

5. **Color Tags**
   - All `[color=#...]...[/color]` preserved
   - Tags properly opened and closed

**Output:**
- Format validation report
- List of format errors (if any)
- Suggested fixes

---

#### Validator 4.2: Consistency Validator (6-8 hours)

**Agent:** Consistency Validator Agent

**Instruction:** `docs/agents/11_CONSISTENCY_VALIDATOR.md`

**Input:**
- All files in `Language/Vi/`
- `GLOSSARY.md`

**Checks:**
1. **Terminology Consistency**
   - All cultivation terms match GLOSSARY
   - Same Chinese term = same Vietnamese term
   - No inconsistent translations

2. **Context Appropriateness**
   - Translations fit context
   - Cultural concepts preserved
   - Tone appropriate for game

3. **Completeness**
   - No untranslated text (Chinese/Thai/English remaining)
   - No missing files
   - All entries translated

4. **Quality**
   - Grammar correct
   - Natural Vietnamese
   - Game-appropriate language

**Output:**
- Consistency validation report
- List of inconsistencies (if any)
- Suggested corrections

---

### Issue Resolution

**If issues found:**

1. **Categorize Issues**
   - Critical (blocks release)
   - Major (should fix)
   - Minor (nice to fix)

2. **Assign Fixes**
   - Critical: Fix immediately
   - Major: Fix before release
   - Minor: Document for future

3. **Re-validate**
   - Run validators again after fixes
   - Ensure all critical issues resolved

### Deliverables
- ✅ Format validation report
- ✅ Consistency validation report
- ✅ All critical issues fixed
- ✅ All major issues fixed
- ✅ Minor issues documented

### Next Phase
**Phase 5: FINALIZATION**

---

## PHASE 5: FINALIZATION (1-2 hours)

### Objective
Prepare for release and commit to repository

### Prerequisites
- Phase 4 complete (QC passed)
- All critical issues resolved

### Tasks

#### Task 5.1: Create README.md

**File:** `README.md`

**Content:**
```markdown
# Vietnamese Language Pack for Amazing Cultivation Simulator

Bản dịch tiếng Việt cho game Amazing Cultivation Simulator

## Installation
1. Download mod from GitHub
2. Copy Language folder to game mod directory
3. In game: Settings → Language → Tiếng Việt

## Credits
- Game: GSQ Games Studio
- Thai mod template: ThaiByTheEmpty & Tz_TonZa
- Vietnamese translation: Vietnamese Translation Team

## License
MIT License
```

#### Task 5.2: Update AGENTS.md

**File:** `AGENTS.md`

**Updates:**
- Mark all phases complete
- Update statistics
- Add completion date

#### Task 5.3: Git Commit

```bash
git add .
git commit -m "feat: Complete Vietnamese translation for Amazing Cultivation Simulator

- Translated all 969 files from Chinese to Vietnamese
- Updated metadata (Info.json, Config.xml)
- Added Vietnamese flag icon (viflag.png)
- Updated font configuration for Vietnamese support
- Created comprehensive glossary for cultivation terms
- Maintained all format strings and XML structure
- Total translation: ~17.3 MB of game text

Translation breakdown:
- Core files: UIText.xml, CodeDictionary.txt, MapStoryDictionary.txt
- Settings: 45 modules (Npc, ThingDef, Practice, World, etc.)
- SL folder: 177 dictionary files (FightMap, TeachFile, RPG Maps)

All files validated for:
- XML well-formedness
- Dictionary format (tab-separated)
- UTF-8 encoding
- Format string preservation
- Color tag preservation
- Terminology consistency"
```

#### Task 5.4: Git Push

```bash
git push origin master
```

#### Task 5.5: Create GitHub Release (Optional)

**Tag:** v1.0.0  
**Title:** Vietnamese Language Pack v1.0.0  
**Description:**

```markdown
# Vietnamese Language Pack v1.0.0

Complete Vietnamese translation for Amazing Cultivation Simulator.

## What's Included
- 969 translated files
- Comprehensive cultivation terminology glossary
- Full game text translation (~17.3 MB)

## Installation
See README.md for installation instructions.

## Credits
See README.md for full credits.
```

**Attachments:**
- GLOSSARY.md
- README.md

### Deliverables
- ✅ README.md created
- ✅ AGENTS.md updated
- ✅ Git committed
- ✅ Git pushed
- ✅ GitHub release created (optional)

### Project Complete! 🎉

---

## DEPENDENCY GRAPH

```
Phase 0 (Setup)
    ↓
Phase 1 (GLOSSARY) ← BLOCKING
    ↓
Phase 2 (Core Translation) ← BLOCKING
    ↓
Phase 3 (Parallel Translation)
    ├─> Practice Specialist ──┐
    ├─> NPC Specialist ────────┤
    ├─> Item Specialist ───────┤
    ├─> World Specialist ──────┼─> All complete
    ├─> UI Specialist ─────────┤
    ├─> System Specialist ─────┤
    └─> Dictionary Specialists ┘
    ↓
Phase 4 (QC)
    ├─> Format Validator ──┐
    └─> Consistency Validator ┴─> Both complete
    ↓
Phase 5 (Finalization)
```

---

## PROGRESS TRACKING

### Checklist

**Phase 0: Setup**
- [ ] Copy Th → Vi
- [ ] Update Info.json
- [ ] Update Config.xml
- [ ] Update font.txt
- [ ] Create viflag.png
- [ ] Update Preview.png (optional)

**Phase 1: GLOSSARY**
- [ ] Extract terms from source
- [ ] Research Vietnamese conventions
- [ ] Create GLOSSARY.md
- [ ] Validate glossary

**Phase 2: Core Translation**
- [ ] Translate UIText.xml
- [ ] Translate CodeDictionary.txt
- [ ] Translate MapStoryDictionary.txt
- [ ] Validate core files

**Phase 3: Module Translation**
- [ ] Practice/ (79 files)
- [ ] Npc/ (55 files)
- [ ] ThingDef/ (74 files)
- [ ] World/Display/MapStories (115 files)
- [ ] Ui/Comment (23 files)
- [ ] System modules (~200 files)
- [ ] SL/ (177 files)

**Phase 4: QC**
- [ ] Format validation
- [ ] Consistency validation
- [ ] Fix critical issues
- [ ] Fix major issues

**Phase 5: Finalization**
- [ ] Create README.md
- [ ] Update AGENTS.md
- [ ] Git commit
- [ ] Git push
- [ ] GitHub release (optional)

---

## NEXT STEPS

1. **Execute Phase 0** - Setup structure
2. **Execute Phase 1** - Create GLOSSARY (CRITICAL)
3. **Follow agent instructions** in `docs/agents/`

---

**Document Version:** 1.0  
**Last Updated:** 2026-05-03T02:50:30.128Z  
**Status:** Complete
