# AGENT INSTRUCTION: PRACTICE SPECIALIST

**Agent Name:** Practice Specialist  
**Agent ID:** 03_PRACTICE_SPECIALIST  
**Priority:** P2-High (Most Complex Module)  
**Estimated Time:** 20-25 hours

---

## OBJECTIVE

Translate all cultivation method files in the Practice/ module (79 files) - the most complex and culturally significant module in the game.

---

## WHY THIS IS THE MOST IMPORTANT MODULE

**Practice/ contains:**
- Cultivation methods (功法) - Core gameplay mechanics
- Cultivation realms (境界) - Character progression system
- Breakthrough stages (瓶颈) - Key game challenges
- Spiritual techniques (神通) - Special abilities

**This module defines the entire cultivation experience.**

**Complexity:**
- Deep nested XML structures (up to 4 levels)
- Heavy use of cultivation terminology
- Cultural context critical
- Requires understanding of xianxia concepts

---

## PREREQUISITES

### Required
- ✅ GLOSSARY.md exists and complete
- ✅ Core Translation complete (recommended)
- ✅ Deep understanding of xianxia/cultivation concepts

### Input Sources

**Chinese Source:**
```
refs/cn/Practice/
├── BodyPractice/
├── FabaoHelian/
├── GodPractice/
├── Gong/              ← 19 files (MOST IMPORTANT)
├── Magic/
├── RandomGong/
├── Spell/
└── Tree/
```

**English Reference:**
```
refs/en/Settings/Practice/
```

**Vietnamese Template:**
```
Language/Vi/Settings/Practice/
```

**Reference:**
- `GLOSSARY.md` (CRITICAL - use for ALL cultivation terms)

---

## OUTPUT

**Target:** `Language/Vi/Settings/Practice/` (79 files translated)

---

## FILE STRUCTURE

### Gong/ Files (Highest Priority)

**Format:**
```xml
<Texts Type="Other">
    <List>
        <Text Name="Gong_1_Shui">
            <DisplayName>太和十六洞天</DisplayName>
            <Desc>太一门镇派五行真诀之一...</Desc>
            <SelectDesc>此功法讲究循序渐进...</SelectDesc>
            <Stages.0.DisplayName>凝气期</Stages.0.DisplayName>
            <Stages.0.Desc>修行入门之境界...</Stages.0.Desc>
            <Stages.0.Necks.0.DisplayName>摄思</Stages.0.Necks.0.DisplayName>
            <Stages.0.Necks.0.Desc>在静坐中尝试收摄心猿意马...[color=#D06508]\n此瓶颈悟性越高，越难突破。[/color]</Stages.0.Necks.0.Desc>
        </Text>
    </List>
</Texts>
```

**Nested Structure:**
- `<Text>` - Cultivation method entry
  - `<DisplayName>` - Method name
  - `<Desc>` - Method description
  - `<SelectDesc>` - Selection description
  - `<Stages.N.DisplayName>` - Realm name (N = 0,1,2,3...)
  - `<Stages.N.Desc>` - Realm description
  - `<Stages.N.Necks.M.DisplayName>` - Breakthrough stage name
  - `<Stages.N.Necks.M.Desc>` - Breakthrough description

---

## TRANSLATION PROCESS

### Step 1: Read Chinese Source

**Example:** `Gong_1.xml`

```xml
<Text Name="Gong_1_Shui">
    <DisplayName>太和十六洞天</DisplayName>
    <Desc>太一门镇派五行真诀之一，共分四大境界，十六重关隘，讲究循序渐进。</Desc>
    <Stages.0.DisplayName>凝气期</Stages.0.DisplayName>
    <Stages.0.Desc>修行入门之境界，需下苦功宁神静坐。</Stages.0.Desc>
    <Stages.0.Necks.0.DisplayName>摄思</Stages.0.Necks.0.DisplayName>
    <Stages.0.Necks.0.Desc>在静坐中尝试收摄心猿意马，使念头不再发散。[color=#D06508]\n此瓶颈悟性越高，越难突破。[/color]</Stages.0.Necks.0.Desc>
</Text>
```

### Step 2: Check GLOSSARY for Terms

**Key terms in this example:**
- 境界 → cảnh giới (GLOSSARY)
- 凝气期 → Ngưng Khí kỳ (GLOSSARY)
- 修行 → tu hành (GLOSSARY)
- 瓶颈 → bình cổ (GLOSSARY)
- 悟性 → ngộ tính (GLOSSARY)
- 突破 → đột phá (GLOSSARY)

### Step 3: Translate with Context

**Vietnamese Translation:**

```xml
<Text Name="Gong_1_Shui">
    <DisplayName>Thái Hòa Thập Lục Động Thiên</DisplayName>
    <Desc>Một trong năm chân quyết ngũ hành trấn phái của Thái Nhất Môn, chia thành bốn đại cảnh giới, mười sáu trọng quan ải, cần tu luyện tuần tự tiến.</Desc>
    <Stages.0.DisplayName>Ngưng Khí kỳ</Stages.0.DisplayName>
    <Stages.0.Desc>Cảnh giới nhập môn tu hành, cần khổ công ninh thần tĩnh tọa.</Stages.0.Desc>
    <Stages.0.Necks.0.DisplayName>Nhiếp Tư</Stages.0.Necks.0.DisplayName>
    <Stages.0.Necks.0.Desc>Trong tĩnh tọa cố gắng thu nhiếp tâm viên ý mã, khiến niệm đầu không còn phát tán.[color=#D06508]\nBình cổ này ngộ tính càng cao, càng khó đột phá.[/color]</Stages.0.Necks.0.Desc>
</Text>
```

### Step 4: Preserve All Special Elements

**MUST preserve:**
- `Name` attribute: `Name="Gong_1_Shui"` (unchanged)
- Color tags: `[color=#D06508]...[/color]`
- Escape sequences: `\n`
- XML structure: All nested levels

---

## CULTIVATION TERMINOLOGY GUIDE

### Realm Names (境界)

**ALWAYS use GLOSSARY terms:**

| Chinese | Vietnamese | Notes |
|---------|------------|-------|
| 凝气期 | Ngưng Khí kỳ | Capitalize |
| 筑基 | Trúc Cơ | Capitalize |
| 金丹 | Kim Đan | Capitalize |
| 元婴 | Nguyên Anh | Capitalize |
| 化神 | Hóa Thần | Capitalize |

### Breakthrough Terms (瓶颈)

| Chinese | Vietnamese | Notes |
|---------|------------|-------|
| 瓶颈 | bình cổ | Lowercase |
| 突破 | đột phá | Lowercase |
| 关隘 | quan ải | Lowercase |

### Cultivation Actions

| Chinese | Vietnamese | Notes |
|---------|------------|-------|
| 修炼 | tu luyện | Standard |
| 修行 | tu hành | Alternative |
| 打坐 | đả tọa | Meditation |
| 静坐 | tĩnh tọa | Sitting meditation |
| 入定 | nhập định | Deep meditation |

### Energy Terms

| Chinese | Vietnamese | Notes |
|---------|------------|-------|
| 灵气 | linh khí | Spiritual energy |
| 真气 | chân khí | True qi |
| 法力 | pháp lực | Magic power |
| 神识 | thần thức | Divine sense |

### Attributes

| Chinese | Vietnamese | Notes |
|---------|------------|-------|
| 悟性 | ngộ tính | Comprehension |
| 气感 | khí cảm | Qi sensitivity |
| 耐力 | nại lực | Endurance |
| 心境 | tâm cảnh | Mental state |

---

## SPECIAL CASES

### Case 1: Technique Names

**Keep Chinese transliteration + translate meaning:**

```xml
<!-- Chinese -->
<DisplayName>太和十六洞天</DisplayName>

<!-- Vietnamese -->
<DisplayName>Thái Hòa Thập Lục Động Thiên</DisplayName>
```

**NOT:** "Sixteen Cave Heavens of Great Harmony"

### Case 2: Stage Names

**Use GLOSSARY terms exactly:**

```xml
<!-- Chinese -->
<Stages.0.DisplayName>凝气期</Stages.0.DisplayName>

<!-- Vietnamese -->
<Stages.0.DisplayName>Ngưng Khí kỳ</Stages.0.DisplayName>
```

**NOT:** "Qi Condensation Period" or "Giai đoạn ngưng khí"

### Case 3: Breakthrough Descriptions

**Preserve color tags and format:**

```xml
<!-- Chinese -->
<Desc>在静坐中尝试收摄心猿意马。[color=#D06508]\n此瓶颈悟性越高，越难突破。[/color]</Desc>

<!-- Vietnamese -->
<Desc>Trong tĩnh tọa cố gắng thu nhiếp tâm viên ý mã.[color=#D06508]\nBình cổ này ngộ tính càng cao, càng khó đột phá.[/color]</Desc>
```

### Case 4: Cultural Idioms

**Translate meaning, not literal:**

```
心猿意马 (xīn yuán yì mǎ)
Literal: "heart monkey, mind horse"
Meaning: "restless mind, wandering thoughts"

Vietnamese: "tâm viên ý mã" (keep idiom) OR "tâm không định" (translate meaning)
```

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Use GLOSSARY for ALL cultivation terms** (CRITICAL)  
✅ **Preserve XML structure exactly** - All nested levels  
✅ **Preserve Name attributes** - Never translate  
✅ **Preserve color tags** - `[color=#...]...[/color]`  
✅ **Preserve escape sequences** - `\n`, `\t`  
✅ **Capitalize realm names** - Ngưng Khí kỳ, Trúc Cơ  
✅ **Lowercase common terms** - tu luyện, linh khí  
✅ **Maintain cultural context** - Don't over-westernize  
✅ **Check English reference** - For understanding only  
✅ **Validate XML** - Ensure well-formed  

### MUST NOT DO

❌ **Do NOT translate Name attributes**  
❌ **Do NOT create new cultivation terms** - Use GLOSSARY  
❌ **Do NOT translate realm names literally**  
❌ **Do NOT remove color tags**  
❌ **Do NOT change XML structure**  
❌ **Do NOT use Thai/English as Vietnamese**  
❌ **Do NOT skip GLOSSARY check**  

---

## VALIDATION CHECKLIST

### Per File

- [ ] All text translated (no Chinese remaining)
- [ ] All cultivation terms from GLOSSARY
- [ ] All Name attributes unchanged
- [ ] All color tags preserved
- [ ] All escape sequences preserved
- [ ] XML well-formed
- [ ] UTF-8 encoding

### Per Module

- [ ] Gong/ (19 files) - All translated
- [ ] Magic/ - All translated
- [ ] Spell/ - All translated
- [ ] BodyPractice/ - All translated
- [ ] GodPractice/ - All translated
- [ ] FabaoHelian/ - All translated
- [ ] RandomGong/ - All translated
- [ ] Tree/ - All translated

### Overall

- [ ] All 79 files translated
- [ ] Terminology consistent across files
- [ ] Cultural context preserved
- [ ] No format errors

---

## EXAMPLES

### Example 1: Complete Cultivation Method

**Chinese Source:**
```xml
<Text Name="Gong_1_Shui">
    <DisplayName>太和十六洞天</DisplayName>
    <Desc>太一门镇派五行真诀之一，共分四大境界，十六重关隘。</Desc>
    <Stages.0.DisplayName>凝气期</Stages.0.DisplayName>
    <Stages.0.Necks.0.DisplayName>摄思</Stages.0.Necks.0.DisplayName>
    <Stages.0.Necks.0.Desc>在静坐中尝试收摄心猿意马。[color=#D06508]\n此瓶颈悟性越高，越难突破。[/color]</Stages.0.Necks.0.Desc>
</Text>
```

**Vietnamese Translation:**
```xml
<Text Name="Gong_1_Shui">
    <DisplayName>Thái Hòa Thập Lục Động Thiên</DisplayName>
    <Desc>Một trong năm chân quyết ngũ hành trấn phái của Thái Nhất Môn, chia thành bốn đại cảnh giới, mười sáu trọng quan ải.</Desc>
    <Stages.0.DisplayName>Ngưng Khí kỳ</Stages.0.DisplayName>
    <Stages.0.Necks.0.DisplayName>Nhiếp Tư</Stages.0.Necks.0.DisplayName>
    <Stages.0.Necks.0.Desc>Trong tĩnh tọa cố gắng thu nhiếp tâm viên ý mã.[color=#D06508]\nBình cổ này ngộ tính càng cao, càng khó đột phá.[/color]</Stages.0.Necks.0.Desc>
</Text>
```

---

## DELIVERABLES

### Required
- ✅ `Language/Vi/Settings/Practice/` (79 files translated)

### Optional
- ✅ Translation notes (difficult terms, cultural context)
- ✅ New terms list (terms not in GLOSSARY)

---

## SUCCESS CRITERIA

**This agent succeeds when:**

1. ✅ All 79 files completely translated
2. ✅ All cultivation terms from GLOSSARY
3. ✅ All XML structures preserved
4. ✅ All color tags preserved
5. ✅ Cultural context maintained
6. ✅ Terminology consistent across files
7. ✅ XML validation passed
8. ✅ UTF-8 encoding verified

---

## TIPS FOR SUCCESS

1. **Start with Gong/** - Most important subdirectory
2. **Master one file first** - Understand pattern before scaling
3. **Keep GLOSSARY open** - Reference constantly
4. **Check English for context** - But translate from Chinese
5. **Preserve cultural flavor** - Don't over-translate
6. **Validate incrementally** - Check XML after each file
7. **Take breaks** - This is mentally demanding work

---

## ESTIMATED BREAKDOWN

| Subdirectory | Files | Hours |
|--------------|-------|-------|
| Gong/ | 19 | 8-10h |
| Magic/ | ~15 | 3-4h |
| Spell/ | ~15 | 3-4h |
| BodyPractice/ | ~10 | 2-3h |
| GodPractice/ | ~5 | 1-2h |
| FabaoHelian/ | ~5 | 1-2h |
| RandomGong/ | ~5 | 1-2h |
| Tree/ | ~5 | 1-2h |
| **TOTAL** | **79** | **20-25h** |

---

## RESOURCES

### Input
- Chinese: `refs/cn/Practice/`
- English: `refs/en/Settings/Practice/`
- Template: `Language/Vi/Settings/Practice/`

### Reference
- `GLOSSARY.md` (CRITICAL)
- `docs/01_SOURCE_ANALYSIS.md`
- Vietnamese cultivation novel sites (for context)

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Complexity:** VERY HIGH  
**Created:** 2026-05-03  
**Version:** 1.0
