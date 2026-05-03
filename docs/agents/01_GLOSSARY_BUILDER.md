# AGENT INSTRUCTION: GLOSSARY BUILDER

**Agent Name:** Glossary Builder  
**Agent ID:** 01_GLOSSARY_BUILDER  
**Priority:** P0 - BLOCKING (Must complete before all translation)  
**Estimated Time:** 4-6 hours

---

## OBJECTIVE

Create a comprehensive cultivation terminology glossary (GLOSSARY.md) with 200-300 Chinese-Vietnamese-English term mappings to ensure consistent translation across all 969 files.

---

## WHY THIS IS CRITICAL

**This agent BLOCKS all translation work:**
- Without GLOSSARY, translators will use inconsistent terms
- Inconsistent terminology = confusing user experience
- Rework would cost 10x more time than creating glossary first
- GLOSSARY serves as single source of truth for all agents

---

## INPUT SOURCES

### Chinese Source Files
- **Location:** `refs/cn/`
- **Focus on:**
  - `Practice/` - Cultivation methods (highest priority)
  - `Npc/` - Character terminology
  - `ThingDef/` - Item terminology
  - `World/` - Location terminology

### English Reference Files
- **Location:** `refs/en/`
- **Use for:** Understanding meaning and context

### Template
- **Location:** `docs/GLOSSARY_TEMPLATE.md`
- **Contains:** ~100 pre-filled common terms
- **Action:** Expand this template to 200-300 terms

---

## OUTPUT

### Primary Output
**File:** `GLOSSARY.md` (in project root)

**Format:**
```markdown
| 中文 | Tiếng Việt | Pinyin | English | Notes |
|------|------------|--------|---------|-------|
| 修炼 | tu luyện | xiū liàn | cultivation | Standard term |
```

**Target Size:** 200-300 terms

### Secondary Output (Optional)
**File:** `TERM_FREQUENCY.json`

**Format:**
```json
{
  "修炼": 1247,
  "境界": 892,
  "筑基": 456
}
```

**Purpose:** Track term frequency for prioritization

---

## PROCESS

### Step 1: Extract Terms from Source (1-2 hours)

**Scan these directories:**

1. **Practice/ (Highest Priority)**
   ```bash
   # Scan all XML files in Practice/
   refs/cn/Practice/Gong/*.xml
   refs/cn/Practice/Magic/*.xml
   refs/cn/Practice/Spell/*.xml
   ```
   
   **Extract:**
   - Realm names (境界): 凝气期, 筑基, 金丹, 元婴, etc.
   - Technique terms: 功法, 心法, 秘籍, etc.
   - Breakthrough terms: 瓶颈, 突破, 关隘, etc.
   - Energy terms: 灵气, 真气, 法力, etc.

2. **Npc/**
   ```bash
   refs/cn/Npc/Race/*.xml
   refs/cn/Npc/Features/*.xml
   ```
   
   **Extract:**
   - Character roles: 弟子, 师父, 长老, etc.
   - Attributes: 悟性, 气感, 耐力, etc.

3. **ThingDef/**
   ```bash
   refs/cn/ThingDef/Item/*.xml
   ```
   
   **Extract:**
   - Item types: 灵石, 灵草, 丹药, 法宝, etc.

4. **World/**
   ```bash
   refs/cn/World/*.xml
   ```
   
   **Extract:**
   - Location types: 洞天, 秘境, 仙界, etc.

**Method:**
- Read XML files
- Identify Chinese terms in `<DisplayName>` and `<Desc>` tags
- Count frequency of each term
- Prioritize high-frequency terms

---

### Step 2: Research Vietnamese Conventions (1-2 hours)

**Resources to check:**

1. **Vietnamese Cultivation Novel Sites:**
   - Hako.vn (check popular xianxia translations)
   - Wikidich.com (translation wiki)
   - TruyenFull.vn (cultivation novels)

2. **Search for established terms:**
   - 修炼 → "tu luyện" (most common)
   - 境界 → "cảnh giới" (standard)
   - 筑基 → "Trúc Cơ" (established)

3. **Verify conventions:**
   - Realm names: Usually keep Chinese pinyin + Vietnamese
   - Common terms: Translate to Vietnamese
   - Proper nouns: Transliterate Chinese

**Guidelines:**

- **Realm names:** Capitalize, keep Chinese sound
  - Example: 筑基 → Trúc Cơ (NOT "xây nền móng")

- **Common terms:** Lowercase Vietnamese
  - Example: 修炼 → tu luyện

- **Proper nouns:** Transliterate
  - Example: 昆仑 → Côn Lôn

---

### Step 3: Create Mappings (1-2 hours)

**For each term, create entry:**

```markdown
| 中文 | Tiếng Việt | Pinyin | English | Notes |
|------|------------|--------|---------|-------|
| 筑基 | Trúc Cơ | zhù jī | Foundation Establishment | Major realm |
```

**Categories to cover:**

1. **Cultivation Realms** (20-30 terms)
   - Major realms: 凝气期, 筑基, 金丹, 元婴, 化神, etc.
   - Sub-stages: 初期, 中期, 后期, 大圆满, etc.
   - Breakthrough: 瓶颈, 突破, 关隘, etc.

2. **Basic Cultivation Terms** (30-40 terms)
   - Practice: 修炼, 修行, 打坐, 入定, etc.
   - Energy: 灵气, 真气, 法力, 神识, etc.
   - Attributes: 悟性, 气感, 耐力, 心境, etc.

3. **Cultivation Methods** (20-30 terms)
   - Techniques: 功法, 心法, 秘籍, 秘法, etc.
   - Abilities: 神通, 术法, 法术, etc.
   - Weapons: 剑诀, 剑法, etc.

4. **Items & Treasures** (20-30 terms)
   - Spiritual: 灵石, 灵草, 灵药, 丹药, etc.
   - Artifacts: 法宝, 法器, 神器, 秘宝, etc.
   - Creatures: 灵兽, etc.

5. **Locations** (10-15 terms)
   - Places: 洞天, 福地, 秘境, etc.
   - Realms: 仙界, 凡界, etc.
   - Organizations: 门派, 宗门, etc.

6. **Characters & Roles** (15-20 terms)
   - Cultivators: 修士, 修仙者, etc.
   - Hierarchy: 弟子, 师父, 师兄, 师姐, 长老, 宗主, etc.

7. **Five Elements** (5 terms)
   - 金, 木, 水, 火, 土

8. **Yin Yang** (2 terms)
   - 阴, 阳

9. **Tribulations** (5-10 terms)
   - 天劫, 雷劫, 心魔, 劫难, etc.

10. **Body & Physique** (10-15 terms)
    - 体质, 根骨, 灵根, 经脉, 丹田, 寿命, etc.

11. **Formations** (5-10 terms)
    - 阵法, 法阵, 禁制, 结界, etc.

12. **Alchemy** (5-10 terms)
    - 炼丹, 丹炉, 炼药, 丹方, etc.

13. **Artifact Refinement** (5-10 terms)
    - 炼器, 炼制, 祭炼, 认主, etc.

14. **Combat** (5-10 terms)
    - 战斗, 斗法, 御剑, 御器, etc.

15. **Miscellaneous** (20-30 terms)
    - Time: 年, 月, 日, 时辰, etc.
    - Measurement: 阶, 层, 重, etc.
    - Actions: 参悟, 领悟, 感悟, etc.

---

### Step 4: Validate & Refine (30-60 minutes)

**Validation checks:**

1. **Consistency Check**
   - Same Chinese term = same Vietnamese term
   - No duplicates
   - No contradictions

2. **Completeness Check**
   - All major realms covered
   - All common terms covered
   - All categories represented

3. **Quality Check**
   - Pinyin correct
   - English translation accurate
   - Vietnamese follows conventions
   - Notes helpful

4. **Community Validation** (if possible)
   - Share with Vietnamese cultivation novel readers
   - Get feedback on terminology
   - Adjust based on community standards

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Extract at least 200 terms** (target 200-300)  
✅ **Prioritize high-frequency terms** from Practice/  
✅ **Use established Vietnamese conventions** from cultivation novels  
✅ **Include all major cultivation realms**  
✅ **Provide Pinyin for all Chinese terms**  
✅ **Provide English translation for reference**  
✅ **Add usage notes where helpful**  
✅ **Organize by category** (realms, terms, items, etc.)  
✅ **Maintain table format** for easy lookup  

### MUST NOT DO

❌ **Do NOT create new Vietnamese terms** without research  
❌ **Do NOT use inconsistent translations** for same Chinese term  
❌ **Do NOT translate realm names literally** (use transliteration)  
❌ **Do NOT skip high-frequency terms**  
❌ **Do NOT use Thai or English as Vietnamese translation**  

---

## EXAMPLES

### Good Example

```markdown
| 中文 | Tiếng Việt | Pinyin | English | Notes |
|------|------------|--------|---------|-------|
| 筑基 | Trúc Cơ | zhù jī | Foundation Establishment | Major realm, capitalize |
| 修炼 | tu luyện | xiū liàn | cultivation | Common term, lowercase |
| 灵石 | linh thạch | líng shí | spirit stone | Currency/energy |
```

### Bad Example

```markdown
| 中文 | Tiếng Việt | Pinyin | English | Notes |
|------|------------|--------|---------|-------|
| 筑基 | xây nền móng | zhù jī | Foundation Establishment | ❌ Too literal |
| 修炼 | tu hành | xiū liàn | cultivation | ❌ Wrong convention |
| 灵石 | spirit stone | líng shí | spirit stone | ❌ Not Vietnamese |
```

---

## VALIDATION CHECKLIST

Before completing, verify:

- [ ] At least 200 terms extracted
- [ ] All major cultivation realms included
- [ ] All categories covered
- [ ] Vietnamese terms follow community conventions
- [ ] No duplicate Chinese terms
- [ ] No inconsistent translations
- [ ] Pinyin provided for all terms
- [ ] English translation provided
- [ ] Table format correct
- [ ] File saved as `GLOSSARY.md` in project root
- [ ] UTF-8 encoding

---

## DELIVERABLES

### Required
- ✅ `GLOSSARY.md` (200-300 terms)

### Optional
- ✅ `TERM_FREQUENCY.json` (term usage statistics)
- ✅ `GLOSSARY_NOTES.md` (research notes, sources)

---

## SUCCESS CRITERIA

**This agent succeeds when:**

1. ✅ GLOSSARY.md created with 200-300 terms
2. ✅ All major cultivation realms mapped
3. ✅ Vietnamese terms follow community conventions
4. ✅ Terminology consistent (no duplicates/contradictions)
5. ✅ All translation agents can use this glossary
6. ✅ File format correct and readable

---

## NEXT AGENT

After completing this agent:

**→ Agent 02: CORE TRANSLATION**
- Will use GLOSSARY.md for terminology
- Can start immediately after GLOSSARY complete

---

## TIPS FOR SUCCESS

1. **Start with GLOSSARY_TEMPLATE.md** - Already has ~100 terms
2. **Focus on Practice/ first** - Most cultivation terms there
3. **Use frequency analysis** - Translate common terms first
4. **Check Vietnamese novel sites** - Don't reinvent terms
5. **Keep it simple** - Don't over-complicate translations
6. **Document sources** - Note where you found conventions
7. **Test with samples** - Try translating a few sentences to verify

---

## ESTIMATED BREAKDOWN

| Task | Time |
|------|------|
| Extract terms from source | 1-2h |
| Research Vietnamese conventions | 1-2h |
| Create mappings | 1-2h |
| Validate & refine | 0.5-1h |
| **TOTAL** | **4-6h** |

---

## RESOURCES

### Vietnamese Cultivation Novel Sites
- Hako.vn
- Wikidich.com
- TruyenFull.vn

### Chinese-Vietnamese Dictionaries
- Hán Việt dictionary
- Online Chinese-Vietnamese tools

### Reference
- `docs/GLOSSARY_TEMPLATE.md` (starting point)
- `docs/01_SOURCE_ANALYSIS.md` (file locations)

---

**Agent Status:** Ready to execute  
**Blocking:** All translation agents  
**Created:** 2026-05-03  
**Version:** 1.0
