# TRANSLATION PLAN - Detailed Strategy & Execution

**Document:** Translation Plan  
**Created:** 2026-05-03  
**Purpose:** Detailed translation strategy and execution plan

---

## TRANSLATION STRATEGY

### Core Principle

**Translate from Chinese → Vietnamese**
- Use Chinese source as primary reference
- Use English for understanding context
- Use Thai for structure/format template

### Why This Approach?

1. **Accuracy:** Direct from source language avoids "translation of translation" quality loss
2. **Cultural Preservation:** Cultivation terms are Chinese cultural concepts
3. **Community Standards:** Vietnamese cultivation novel community has established terminology
4. **Consistency:** Single source of truth for terminology

---

## PHASE BREAKDOWN

### Phase 0: SETUP (Manual - 30 minutes)

**Objective:** Prepare Vietnamese language structure

**Tasks:**

1. **Copy Thai structure to Vietnamese**
   ```bash
   cp -r Language/Th Language/Vi
   ```

2. **Update Info.json**
   ```json
   {
       "Name": "VietnameseLanguage",
       "DisplayName": "Vietnamese Language",
       "Desc": "Bản dịch tiếng Việt cho Amazing Cultivation Simulator",
       "Author": "Vietnamese Translation Team",
       "Sort": "9999999"
   }
   ```

3. **Update Language/Config.xml**
   ```xml
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
   ```

4. **Update Language/Vi/Settings/font.txt**
   ```
   NotoSans-VariableFont_wdth,wght
   ```

5. **Create Resources/viflag.png**
   - Vietnamese flag icon (similar size to thflag.png)

**Deliverable:** Vietnamese structure ready for translation

---

### Phase 1: GLOSSARY (Critical - 4-6 hours)

**Objective:** Create comprehensive cultivation terminology glossary

**Why Critical?**
- Ensures consistency across all 969 files
- Establishes standard Vietnamese terms
- Prevents rework due to inconsistent terminology
- Serves as reference for all translation agents

**Process:**

1. **Extract Terms from Source**
   - Scan `Practice/` for cultivation terms
   - Scan `Npc/` for character/race terms
   - Scan `ThingDef/` for item terms
   - Identify high-frequency terms

2. **Research Vietnamese Conventions**
   - Check Vietnamese cultivation novel translations
   - Verify with community standards
   - Ensure cultural appropriateness

3. **Create GLOSSARY.md**
   - Chinese term
   - Vietnamese translation
   - Pinyin (for reference)
   - English translation
   - Usage notes

**Deliverable:** `GLOSSARY.md` with 200-300 terms

**Agent:** Glossary Builder Agent

**Instruction File:** `docs/agents/01_GLOSSARY_BUILDER.md`

---

### Phase 2: CORE TRANSLATION (High Priority - 18-23 hours)

**Objective:** Translate the 3 most critical files

**Why These Files?**
- UIText.xml: All UI strings - users see first
- CodeDictionary.txt: System messages - game functionality
- MapStoryDictionary.txt: Story events - narrative experience

#### Task 2.1: UIText.xml (6-8 hours)

**Input:**
- English: `refs/en/UIText.xml`
- Template: `Language/Vi/UIText.xml`
- GLOSSARY: `GLOSSARY.md`

**Process:**
1. Read English source (3,583 lines)
2. For each `<string>` entry:
   - Translate English → Vietnamese
   - Preserve `name` and `mz` attributes
   - Preserve format strings (`{0}`, `{1:N0}`)
   - Preserve color tags
   - Check GLOSSARY for cultivation terms
3. Write to Vietnamese file

**Example:**
```xml
<!-- English -->
<string name="0xrxw6g7qkn8ovp3-n143_bpyo" mz="confirm">Combine</string>

<!-- Vietnamese -->
<string name="0xrxw6g7qkn8ovp3-n143_bpyo" mz="confirm">Hợp nhất</string>
```

#### Task 2.2: CodeDictionary.txt (8-10 hours)

**Input:**
- English: `refs/en/CodeDictionary.txt`
- Template: `Language/Vi/CodeDictionary.txt`
- GLOSSARY: `GLOSSARY.md`

**Process:**
1. Read English source (4,435 lines)
2. For each line:
   - Column 1 (Chinese Key): KEEP UNCHANGED
   - Column 2 (English Value): TRANSLATE to Vietnamese
   - Use TAB separator (not space)
   - Preserve format strings and color tags
   - Check GLOSSARY for terms
3. Write to Vietnamese file

**Example:**
```
<!-- English -->
看天花板	Looking At The Ceiling

<!-- Vietnamese -->
看天花板	Nhìn lên trần nhà
```

#### Task 2.3: MapStoryDictionary.txt (4-5 hours)

**Input:**
- English: `refs/en/MapStoryDictionary.txt`
- Template: `Language/Vi/MapStoryDictionary.txt`
- GLOSSARY: `GLOSSARY.md`

**Process:** Same as CodeDictionary.txt

**Deliverable:** 3 core files translated

**Agent:** Core Translation Agent

**Instruction File:** `docs/agents/02_CORE_TRANSLATION.md`

---

### Phase 3: PARALLEL TRANSLATION (100-120 hours)

**Objective:** Translate all Settings/ modules in parallel

**Strategy:** Assign specialized agents to different modules

#### Module 3.1: Practice/ ⭐ HIGHEST COMPLEXITY (20-25 hours)

**Priority:** P2-High

**Files:** 79 files in 8 subdirectories

**Input:**
- Chinese: `refs/cn/Practice/`
- English: `refs/en/Settings/Practice/`
- Template: `Language/Vi/Settings/Practice/`
- GLOSSARY: `GLOSSARY.md`

**Special Requirements:**
- **MUST use GLOSSARY** for all cultivation terms
- Deep understanding of xianxia concepts
- Nested XML structure handling
- Context-aware translation

**Key Challenges:**
- Cultivation realms (境界)
- Breakthrough stages (瓶颈)
- Technique names (功法)
- Spiritual concepts (灵气, 心境)

**Agent:** Practice Specialist Agent

**Instruction File:** `docs/agents/03_PRACTICE_SPECIALIST.md`

#### Module 3.2: Npc/ (10-12 hours)

**Priority:** P2

**Files:** 55 files in 10 subdirectories

**Content:** NPCs, races, features, moods, relationships

**Agent:** NPC Specialist Agent

**Instruction File:** `docs/agents/04_NPC_SPECIALIST.md`

#### Module 3.3: ThingDef/ (12-15 hours)

**Priority:** P2

**Files:** 74 files in 6 subdirectories

**Content:** Items, buildings, plants, rocks

**Agent:** Item Specialist Agent

**Instruction File:** `docs/agents/05_ITEM_SPECIALIST.md`

#### Module 3.4: World/Display/MapStories (17-21 hours)

**Priority:** P2

**Files:** 
- World/ (24 files)
- Display/ (66 files)
- MapStories/ (25 files)

**Content:** World settings, display names, story events

**Agent:** World Specialist Agent

**Instruction File:** `docs/agents/06_WORLD_SPECIALIST.md`

#### Module 3.5: Ui/Comment (4-6 hours)

**Priority:** P1

**Files:**
- Ui/ (11 files)
- Comment/ (12 files)

**Content:** UI elements, tooltips, help text

**Agent:** UI Specialist Agent

**Instruction File:** `docs/agents/07_UI_SPECIALIST.md`

#### Module 3.6: System Modules (47 hours)

**Priority:** P3

**Files:** ~200 files across 23+ modules

**Content:** All remaining Settings/ modules

**Agent:** System Specialist Agent

**Instruction File:** `docs/agents/08_SYSTEM_SPECIALIST.md`

#### Module 3.7: SL/ Dictionaries (26-33 hours)

**Priority:** P4

**Files:** 177 dictionary files

**Content:** Location names, tutorial text, map strings

**Agent:** Dictionary Specialist Agents (2-3 agents)

**Instruction File:** `docs/agents/09_DICTIONARY_SPECIALIST.md`

**Deliverable:** All 969 files translated

---

### Phase 4: QUALITY CONTROL (10-13 hours)

**Objective:** Validate all translated files

#### Task 4.1: Format Validation (4-5 hours)

**Checks:**
1. **XML Validation**
   - All XML files well-formed
   - No unclosed tags
   - Attributes preserved

2. **Dictionary Format**
   - Tab-separated (not space)
   - Key column unchanged
   - No empty lines

3. **Encoding**
   - All files UTF-8
   - Vietnamese diacritics correct
   - No corrupted characters

4. **Format Strings**
   - All `{0}`, `{1:N0}` preserved
   - All `[NAME]`, `[PLACE]` preserved
   - All `\n` preserved

5. **Color Tags**
   - All `[color=#...]...[/color]` preserved
   - Tags properly closed

**Agent:** Format Validator Agent

**Instruction File:** `docs/agents/10_FORMAT_VALIDATOR.md`

#### Task 4.2: Consistency Validation (6-8 hours)

**Checks:**
1. **Terminology Consistency**
   - All cultivation terms match GLOSSARY
   - Same Chinese term = same Vietnamese term
   - No inconsistent translations

2. **Context Appropriateness**
   - Translations fit context
   - Cultural concepts preserved
   - Tone appropriate

3. **Completeness**
   - No untranslated text
   - No missing files
   - All entries translated

**Agent:** Consistency Validator Agent

**Instruction File:** `docs/agents/11_CONSISTENCY_VALIDATOR.md`

**Deliverable:** QC Report + Fixed files

---

### Phase 5: FINALIZATION (1-2 hours)

**Objective:** Prepare for release

**Tasks:**

1. **Create README.md**
   - Installation instructions
   - Credits
   - License

2. **Update AGENTS.md**
   - Mark all phases complete
   - Update statistics

3. **Git Commit**
   ```bash
   git add .
   git commit -m "feat: Complete Vietnamese translation
   
   - Translated all 969 files from Chinese to Vietnamese
   - Created comprehensive GLOSSARY with 200+ terms
   - Validated format and consistency
   - Total translation: ~17.3 MB"
   ```

4. **Git Push**
   ```bash
   git push origin master
   ```

5. **Create GitHub Release** (optional)
   - Tag: v1.0.0
   - Title: Vietnamese Language Pack v1.0.0
   - Attach GLOSSARY.md

**Deliverable:** Released Vietnamese Language Pack

---

## TRANSLATION GUIDELINES

### General Rules

1. **Preserve Structure**
   - Never change XML structure
   - Never change attribute names/values
   - Never change Key column in dictionaries

2. **Preserve Special Elements**
   - Format strings: `{0}`, `{1}`, `{1:N0}`, `{0:F2}`
   - Placeholders: `[NAME]`, `[PLACE]`, `[IT]`, `[ITS]`
   - Color tags: `[color=#RRGGBB]...[/color]`
   - Escape sequences: `\n`, `\t`

3. **Use GLOSSARY**
   - Always check GLOSSARY for cultivation terms
   - Use exact Vietnamese term from GLOSSARY
   - Do not create new translations for glossary terms

4. **Maintain Consistency**
   - Same source text = same translation
   - Consistent terminology across files
   - Consistent style and tone

5. **Cultural Sensitivity**
   - Preserve Chinese names where appropriate
   - Use Vietnamese cultivation novel conventions
   - Maintain xianxia cultural context

### Cultivation Terminology Guidelines

**Realms (境界):**
- Keep Chinese pinyin + Vietnamese translation
- Example: 筑基 → Trúc Cơ (not "xây nền móng")

**Techniques (功法):**
- Translate meaning, keep cultural flavor
- Example: 太和十六洞天 → Thái Hòa Thập Lục Động Thiên

**Concepts (概念):**
- Use established Vietnamese terms
- Example: 修炼 → tu luyện (not "tu hành" or "luyện tập")

**Items (物品):**
- Translate descriptively
- Example: 灵石 → linh thạch (spirit stone)

### Format String Guidelines

**Pattern:** `{N}` or `{N:FORMAT}`

**Examples:**
```
{0}天 → {0} ngày
{0:N0}/{1:N0} → {0:N0}/{1:N0}
{0}个 → {0}
```

**Rules:**
- Always preserve the placeholder
- Add space before Vietnamese unit if needed
- Never translate the placeholder itself

### Color Tag Guidelines

**Pattern:** `[color=#RRGGBB]text[/color]`

**Rules:**
- Preserve color code exactly
- Translate text inside tags
- Keep opening and closing tags

**Example:**
```
[color=#D06508]此瓶颈悟性越高，越难突破。[/color]
→
[color=#D06508]Bình cổ này ngộ tính càng cao, càng khó đột phá.[/color]
```

---

## QUALITY METRICS

### Success Criteria

**Must Have (P0):**
- ✅ 100% files translated (969/969)
- ✅ 100% format strings preserved
- ✅ 100% XML files valid
- ✅ 100% UTF-8 encoding
- ✅ GLOSSARY created and followed
- ✅ Game loads without errors

**Should Have (P1):**
- ✅ 100% terminology consistency
- ✅ 95%+ context appropriateness
- ✅ All QC checks passed
- ✅ Documentation complete

**Nice to Have (P2):**
- ✅ Community review positive
- ✅ Example translations provided
- ✅ Contribution guidelines created

### Validation Checklist

**Per File:**
- [ ] All text translated (no Chinese/Thai/English remaining)
- [ ] Format strings preserved
- [ ] Color tags preserved
- [ ] XML structure valid (if XML)
- [ ] Dictionary format correct (if Dictionary)
- [ ] UTF-8 encoding
- [ ] Terminology matches GLOSSARY

**Per Module:**
- [ ] All files in module translated
- [ ] Terminology consistent within module
- [ ] Context appropriate
- [ ] No missing files

**Overall:**
- [ ] All 969 files translated
- [ ] GLOSSARY followed consistently
- [ ] QC reports clean
- [ ] Game tested and working

---

## TIMELINE ESTIMATES

### Sequential Execution

| Phase | Hours | Days (8h/day) |
|-------|-------|---------------|
| Phase 0: Setup | 0.5 | 0.1 |
| Phase 1: GLOSSARY | 4-6 | 0.5-0.75 |
| Phase 2: Core | 18-23 | 2.25-2.9 |
| Phase 3: Modules | 100-120 | 12.5-15 |
| Phase 4: QC | 10-13 | 1.25-1.6 |
| Phase 5: Final | 1-2 | 0.1-0.25 |
| **TOTAL** | **155-191** | **19-24** |

### Parallel Execution (7-8 agents)

| Day | Phase | Agents | Hours |
|-----|-------|--------|-------|
| 1 | GLOSSARY | 1 | 4-6 |
| 2-3 | Core | 1 | 18-23 |
| 4-10 | Modules | 7-8 | 20-25 each |
| 11 | QC | 2 | 10-13 |
| 12 | Final | 1 | 1-2 |
| **TOTAL** | | | **10-12 days** |

---

## RISK MITIGATION

### High Risks

**Risk:** Inconsistent terminology  
**Mitigation:** Create GLOSSARY first, validate consistency

**Risk:** Format corruption  
**Mitigation:** Automated validation, preserve rules

**Risk:** XML structure damage  
**Mitigation:** XML validation, careful editing

### Medium Risks

**Risk:** Cultural context loss  
**Mitigation:** Use cultivation conventions, preserve names

**Risk:** Encoding issues  
**Mitigation:** UTF-8 validation, test in game

### Low Risks

**Risk:** File size increase  
**Mitigation:** Acceptable, monitor if needed

---

## NEXT STEPS

1. **Read** `03_AGENT_ARCHITECTURE.md` for agent design
2. **Read** `04_WORKFLOW.md` for workflow details
3. **Execute** Phase 0 (Setup)
4. **Execute** Phase 1 (GLOSSARY) - **CRITICAL FIRST STEP**

---

**Document Version:** 1.0  
**Last Updated:** 2026-05-03T02:47:30.445Z  
**Status:** Complete
