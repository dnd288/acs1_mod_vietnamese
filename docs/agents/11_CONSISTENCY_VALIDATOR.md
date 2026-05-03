# AGENT INSTRUCTION: CONSISTENCY VALIDATOR

**Agent Name:** Consistency Validator  
**Agent ID:** 11_CONSISTENCY_VALIDATOR  
**Priority:** P5 (Quality Control)  
**Estimated Time:** 6-8 hours

---

## OBJECTIVE

Validate terminology consistency across all 969 translated files, ensuring all cultivation terms match GLOSSARY and translations are consistent throughout.

---

## PREREQUISITES

### Required
- ✅ Phase 3 complete (all files translated)
- ✅ GLOSSARY.md exists
- ✅ Format validation passed (or in progress)

---

## VALIDATION SCOPE

**Files to validate:** All 969 files in `Language/Vi/`  
**Reference:** `GLOSSARY.md`

---

## VALIDATION CHECKS

### Check 1: GLOSSARY Term Consistency

**Validate:**
- All cultivation terms use GLOSSARY translations
- Same Chinese term = same Vietnamese term always
- No variations or alternatives

**Method:**
1. Load GLOSSARY.md
2. Extract all Chinese → Vietnamese mappings
3. Scan all translated files
4. Find Chinese terms in source
5. Verify Vietnamese translation matches GLOSSARY

**Example:**
```
GLOSSARY: 修炼 → tu luyện

✅ CORRECT: All instances use "tu luyện"
❌ WRONG: Some use "tu hành", some use "tu luyện"
```

**Report:**
- Terms not matching GLOSSARY
- Inconsistent translations
- File and line numbers

---

### Check 2: Internal Consistency

**Validate:**
- Same source text = same translation
- No contradictory translations
- Consistent terminology within files

**Method:**
1. Build translation map from all files
2. Find duplicate source texts
3. Check if translations are identical
4. Report inconsistencies

**Example:**
```
Source: "境界"

File A: "cảnh giới" ✅
File B: "cảnh giới" ✅
File C: "ranh giới" ❌ INCONSISTENT
```

**Report:**
- Inconsistent translations
- Source text
- Different translations found
- File locations

---

### Check 3: Realm Name Consistency

**Validate:**
- All realm names capitalized correctly
- Consistent across all files
- Match GLOSSARY exactly

**Key terms to check:**
- 凝气期 → Ngưng Khí kỳ (capitalized)
- 筑基 → Trúc Cơ (capitalized)
- 金丹 → Kim Đan (capitalized)
- 元婴 → Nguyên Anh (capitalized)
- 化神 → Hóa Thần (capitalized)

**Report:**
- Incorrect capitalization
- Variations in realm names
- File locations

---

### Check 4: Common Term Consistency

**Validate:**
- Common terms lowercase
- Consistent usage

**Key terms to check:**
- 修炼 → tu luyện (lowercase)
- 灵气 → linh khí (lowercase)
- 功法 → công pháp (lowercase)
- 法宝 → pháp bảo (lowercase)

**Report:**
- Incorrect capitalization
- Inconsistent usage

---

### Check 5: Completeness Check

**Validate:**
- No untranslated text remaining
- No Chinese characters in translated content
- No Thai text remaining
- No English text (except proper nouns)

**Method:**
1. Scan for Chinese characters (Unicode range)
2. Scan for Thai characters (Unicode range)
3. Scan for English words (except in proper contexts)

**Exceptions:**
- Chinese keys in Dictionary files (Column 1)
- Proper nouns (names, places)
- Technical terms (if intentional)

**Report:**
- Files with untranslated text
- Line numbers
- Text found

---

### Check 6: Context Appropriateness

**Validate:**
- Translations fit context
- Tone appropriate for game
- Cultural concepts preserved
- No awkward phrasing

**Method:**
- Sample review of translations
- Check narrative flow
- Verify cultivation context
- Test readability

**Report:**
- Awkward translations
- Context mismatches
- Suggestions for improvement

---

### Check 7: Quality Metrics

**Calculate:**
- Terminology consistency rate
- GLOSSARY adherence rate
- Completeness percentage
- Overall quality score

**Metrics:**
```
Terminology Consistency: X% (target: 100%)
GLOSSARY Adherence: X% (target: 100%)
Completeness: X% (target: 100%)
Overall Quality: X% (target: 95%+)
```

---

## VALIDATION PROCESS

### Step 1: Load GLOSSARY

```
1. Read GLOSSARY.md
2. Extract all Chinese → Vietnamese mappings
3. Create lookup dictionary
```

### Step 2: Scan All Files

```
For each file in Language/Vi/:
    1. Read file content
    2. Extract translated text
    3. Check against GLOSSARY
    4. Check internal consistency
    5. Check completeness
    6. Record issues
```

### Step 3: Analyze Results

```
1. Aggregate all issues
2. Calculate metrics
3. Identify patterns
4. Prioritize fixes
```

### Step 4: Generate Report

```
1. Create comprehensive report
2. List all inconsistencies
3. Provide recommendations
4. Create fix list
```

---

## OUTPUT

### Consistency Report

**File:** `CONSISTENCY_REPORT.md`

**Format:**
```markdown
# Consistency Validation Report

**Date:** 2026-05-03
**Files Validated:** 969
**Status:** PASS/FAIL

## Summary

- Terminology Consistency: 98.5%
- GLOSSARY Adherence: 99.2%
- Completeness: 99.8%
- Overall Quality: 97.5%

## Metrics

### GLOSSARY Term Usage
- Total cultivation terms found: 15,234
- Matching GLOSSARY: 15,112 (99.2%)
- Not matching: 122 (0.8%)

### Internal Consistency
- Unique source texts: 8,456
- Consistent translations: 8,321 (98.4%)
- Inconsistent translations: 135 (1.6%)

### Completeness
- Total text segments: 45,678
- Fully translated: 45,589 (99.8%)
- Untranslated: 89 (0.2%)

## Issues Found

### GLOSSARY Mismatches (122)

1. **修炼 (xiū liàn)**
   - GLOSSARY: "tu luyện"
   - Found: "tu hành" (15 instances)
   - Files:
     - Language/Vi/Settings/Practice/Gong/Gong_3.xml:45
     - Language/Vi/Settings/Npc/Features/Body_Features.xml:23
     - ...

2. **境界 (jìng jiè)**
   - GLOSSARY: "cảnh giới"
   - Found: "ranh giới" (8 instances)
   - Files:
     - Language/Vi/Settings/Practice/Magic/Magic_1.xml:67
     - ...

### Internal Inconsistencies (135)

1. **Source: "普通的动物：人类"**
   - Translation A: "Động vật thông thường: Con người" (45 files)
   - Translation B: "Động vật bình thường: Người" (3 files)
   - Recommendation: Use Translation A (more common)

### Untranslated Text (89)

1. **File:** Language/Vi/Settings/World/World_1.xml
   - Line 34: Contains Chinese text "世界设置"
   - Should be: "Cài đặt thế giới"

2. **File:** Language/Vi/CodeDictionary.txt
   - Line 456: Contains Thai text
   - Should be: Vietnamese translation

## Recommendations

### High Priority
1. Fix all GLOSSARY mismatches (122 instances)
2. Translate all untranslated text (89 instances)
3. Resolve major inconsistencies (top 20)

### Medium Priority
1. Standardize minor inconsistencies (115 instances)
2. Review context appropriateness (sample 50 files)

### Low Priority
1. Polish awkward phrasing (if found)
2. Optimize text length for UI

## Files Requiring Fixes

[Prioritized list of files with issues]
```

---

## VALIDATION SCRIPT (Optional)

**Can create Python script:**

```python
# validate_consistency.py
import re
from collections import defaultdict

def load_glossary(glossary_path):
    """Load GLOSSARY.md and extract mappings"""
    glossary = {}
    # Parse GLOSSARY.md
    # Extract Chinese → Vietnamese mappings
    return glossary

def check_glossary_adherence(file_path, glossary):
    """Check if file uses GLOSSARY terms correctly"""
    issues = []
    # Read file
    # Find Chinese terms
    # Check Vietnamese translation
    # Report mismatches
    return issues

def check_internal_consistency(all_files):
    """Check consistency across all files"""
    translation_map = defaultdict(set)
    # Build map of source → translations
    # Find inconsistencies
    return inconsistencies

# ... more validation functions
```

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Check ALL 969 files**  
✅ **Verify GLOSSARY adherence**  
✅ **Check internal consistency**  
✅ **Verify completeness**  
✅ **Calculate quality metrics**  
✅ **Generate comprehensive report**  
✅ **Prioritize fixes**  

### MUST NOT DO

❌ **Do NOT skip files**  
❌ **Do NOT ignore inconsistencies**  
❌ **Do NOT fix issues** (report only)  

---

## SUCCESS CRITERIA

1. ✅ All 969 files validated
2. ✅ GLOSSARY adherence verified
3. ✅ Consistency checked
4. ✅ Completeness verified
5. ✅ Quality metrics calculated
6. ✅ Comprehensive report generated
7. ✅ Fix list prioritized

---

## DELIVERABLES

### Required
- ✅ `CONSISTENCY_REPORT.md` (comprehensive report)
- ✅ Issue list (prioritized by severity)
- ✅ Quality metrics

### Optional
- ✅ `validate_consistency.py` (validation script)
- ✅ `GLOSSARY_USAGE_STATS.json` (term usage statistics)

---

## TIPS

1. **Automate term checking** - Use scripts for GLOSSARY lookup
2. **Focus on high-frequency terms** - Most impact
3. **Sample review for context** - Can't check everything manually
4. **Provide clear examples** - Help fixers understand issues
5. **Calculate metrics** - Show overall quality

---

## ESTIMATED BREAKDOWN

| Task | Hours |
|------|-------|
| Load GLOSSARY & setup | 0.5h |
| GLOSSARY adherence check | 2-3h |
| Internal consistency check | 2-3h |
| Completeness check | 1h |
| Context review (sampling) | 1-2h |
| Report generation | 0.5-1h |
| **TOTAL** | **6-8h** |

---

**Agent Status:** Ready to execute  
**Prerequisites:** Phase 3 complete, GLOSSARY.md exists  
**Created:** 2026-05-03  
**Version:** 1.0
