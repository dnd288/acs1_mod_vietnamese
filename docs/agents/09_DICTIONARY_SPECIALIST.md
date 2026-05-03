# AGENT INSTRUCTION: DICTIONARY SPECIALIST

**Agent Name:** Dictionary Specialist  
**Agent ID:** 09_DICTIONARY_SPECIALIST  
**Priority:** P4  
**Estimated Time:** 26-33 hours (split among 2-3 agents)

---

## OBJECTIVE

Translate all dictionary files in the SL/ folder (177 files) containing location names, tutorial text, and map-specific strings.

---

## PREREQUISITES

### Required
- ✅ GLOSSARY.md exists
- ✅ Phase 0 complete

### Input Sources

**English Source:**
```
refs/en/SL/
├── Assets/Resources/FightMap/     (61 folders)
├── Settings/TeachFile/             (43 folders)
├── Settings/RPG/Maps/              (35 folders)
└── Assets/Resources/TeachSave/     (1 file)
```

**Vietnamese Template:**
```
Language/Vi/SL/
```

---

## OUTPUT

**Target:** `Language/Vi/SL/` (177 dictionary files)

---

## FILE STRUCTURE

### Dictionary Format

**All files use tab-separated format:**
```
Key<TAB>Value
昆仑道册-神视	KunLun Manual-Divine Sight
天柱石砖	Holy Stone Block
拜祖师	Worshipping ancestors
房间	Room
```

**Translation:**
```
Key<TAB>Value
昆仑道册-神视	Côn Lôn Đạo Sách - Thần Thị
天柱石砖	Gạch Đá Thiên Trụ
拜祖师	Thờ tổ sư
房间	Phòng
```

---

## MODULES

### Module 1: FightMap/ (61 folders)

**Location:** `SL/Assets/Resources/FightMap/`

**Content:** Battle map location names and objects

**Examples:**
- `School_KunLun/map/_Dictionary.txt` - Kunlun Sect map
- `Place_BaiMan1_Cave_QianShi/map/_Dictionary.txt` - Thousand Stone Cave
- `School_WuDang/map/_Dictionary.txt` - Wudang Sect map

**Translation approach:**
- Location names: Transliterate Chinese (昆仑 → Côn Lôn)
- Object names: Translate descriptively
- Keep cultivation terms from GLOSSARY

---

### Module 2: TeachFile/ (43 folders)

**Location:** `SL/Settings/TeachFile/`

**Content:** Tutorial text and instructions

**Examples:**
- `JJ-01/_Dictionary.txt` - Basic tutorial
- `JY-01/_Dictionary.txt` - Advanced tutorial
- `XL-01/_Dictionary.txt` - Expert tutorial

**Translation approach:**
- Instructional text: Clear and simple
- Item names: Use GLOSSARY
- Actions: Use standard Vietnamese verbs

---

### Module 3: RPG/Maps/ (35 folders)

**Location:** `SL/Settings/RPG/Maps/`

**Content:** RPG mode map strings

**Examples:**
- `Rpg_Tower_0/map/_Dictionary.txt` - Tower level 0
- `Rpg_Arena/map/_Dictionary.txt` - Arena map
- `test1/map/_Dictionary.txt` - Test map

**Translation approach:**
- Map names: Keep English/transliterate
- Object names: Translate
- Use GLOSSARY for cultivation items

---

### Module 4: TeachSave/ (1 file)

**Location:** `SL/Assets/Resources/TeachSave/_Dictionary.txt`

**Content:** Teaching save file strings (386 lines)

**Translation approach:**
- Same as TeachFile/
- Comprehensive tutorial content

---

## TRANSLATION PROCESS

### Step-by-Step

1. **Read English source file**
2. **For each line:**
   - Split by TAB
   - Column 1 (Chinese Key): KEEP UNCHANGED
   - Column 2 (English Value): TRANSLATE to Vietnamese
3. **Check GLOSSARY** for cultivation terms
4. **Join with TAB** (not space)
5. **Write to Vietnamese file**

### Examples

**Example 1: Location Name**
```
<!-- English -->
昆仑道册-神视	KunLun Manual-Divine Sight

<!-- Vietnamese -->
昆仑道册-神视	Côn Lôn Đạo Sách - Thần Thị
```

**Example 2: Object Name**
```
<!-- English -->
天柱石砖	Holy Stone Block

<!-- Vietnamese -->
天柱石砖	Gạch Đá Thiên Trụ
```

**Example 3: Tutorial Text**
```
<!-- English -->
拜祖师	Worshipping ancestors

<!-- Vietnamese -->
拜祖师	Thờ tổ sư
```

**Example 4: Item Name (Use GLOSSARY)**
```
<!-- English -->
灵石	Spirit Stone

<!-- Vietnamese -->
灵石	Linh thạch
```

---

## SPLITTING WORK (2-3 Agents)

### Agent 9A: FightMap/ (61 folders, 10-12 hours)
- All battle map dictionaries
- Focus on location names

### Agent 9B: TeachFile/ (43 folders, 8-10 hours)
- All tutorial dictionaries
- Focus on instructional clarity

### Agent 9C: RPG/Maps/ + TeachSave/ (36 files, 8-11 hours)
- RPG map dictionaries (35 folders)
- TeachSave dictionary (1 file)

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Keep Column 1 (Chinese Key) UNCHANGED**  
✅ **Translate Column 2 (English Value) to Vietnamese**  
✅ **Use TAB separator** (not space)  
✅ **Use GLOSSARY for cultivation terms**  
✅ **Transliterate Chinese location names**  
✅ **Preserve format strings if any**  
✅ **UTF-8 encoding**  

### MUST NOT DO

❌ **Do NOT translate Chinese keys (Column 1)**  
❌ **Do NOT use space separator** - Must be TAB  
❌ **Do NOT skip GLOSSARY check**  
❌ **Do NOT over-translate location names**  

---

## VALIDATION CHECKLIST

### Per File
- [ ] All lines translated
- [ ] Column 1 (Chinese) unchanged
- [ ] Column 2 (Vietnamese) translated
- [ ] TAB separator used
- [ ] UTF-8 encoding

### Per Module
- [ ] FightMap/ (61 folders) complete
- [ ] TeachFile/ (43 folders) complete
- [ ] RPG/Maps/ (35 folders) complete
- [ ] TeachSave/ (1 file) complete

### Overall
- [ ] All 177 files translated
- [ ] Location names consistent
- [ ] Tutorial text clear
- [ ] GLOSSARY terms used

---

## SUCCESS CRITERIA

1. ✅ All 177 files completely translated
2. ✅ Dictionary format correct (tab-separated)
3. ✅ Location names appropriately transliterated
4. ✅ Tutorial text clear and instructive
5. ✅ Cultivation terms from GLOSSARY

---

## TIPS

1. **Work folder by folder** - Complete one location at a time
2. **Location names pattern** - Learn transliteration rules
3. **Tutorial text is instructional** - Be clear and simple
4. **Check TAB separator** - Use actual TAB character
5. **Batch similar content** - All School_* together, etc.

---

## ESTIMATED BREAKDOWN

| Module | Files | Hours | Agent |
|--------|-------|-------|-------|
| FightMap/ | 61 | 10-12h | 9A |
| TeachFile/ | 43 | 8-10h | 9B |
| RPG/Maps/ | 35 | 7-9h | 9C |
| TeachSave/ | 1 | 1-2h | 9C |
| **TOTAL** | **177** | **26-33h** | **2-3** |

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Can split:** Yes (2-3 agents recommended)  
**Created:** 2026-05-03  
**Version:** 1.0
