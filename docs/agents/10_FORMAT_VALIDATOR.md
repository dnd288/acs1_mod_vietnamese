# AGENT INSTRUCTION: FORMAT VALIDATOR

**Agent Name:** Format Validator  
**Agent ID:** 10_FORMAT_VALIDATOR  
**Priority:** P5 (Quality Control)  
**Estimated Time:** 4-5 hours

---

## OBJECTIVE

Validate all translated files (969 files) for format correctness, encoding, and preservation of special elements.

---

## PREREQUISITES

### Required
- ✅ Phase 3 complete (all files translated)
- ✅ All 969 files exist in `Language/Vi/`

---

## VALIDATION SCOPE

**Files to validate:** All 969 files in `Language/Vi/`

---

## VALIDATION CHECKS

### Check 1: XML Well-Formedness (488 XML files)

**Validate:**
- All XML files parse without errors
- All tags properly opened and closed
- No syntax errors
- Proper nesting

**Tools:**
- XML parser (built-in or library)
- Check each .xml file

**Report:**
- List of files with XML errors
- Error messages
- Line numbers

---

### Check 2: Dictionary Format (477 Dictionary files)

**Validate:**
- Tab-separated format (not space)
- Two columns per line
- No empty lines (except intentional)
- Key column unchanged from source

**Check pattern:**
```
^[^\t]+\t[^\t]+$
```

**Report:**
- Files with format errors
- Lines with incorrect separator
- Lines with missing columns

---

### Check 3: UTF-8 Encoding (All 969 files)

**Validate:**
- All files UTF-8 encoded
- Vietnamese diacritics display correctly
- No corrupted characters
- No BOM issues (unless source had BOM)

**Check:**
- Read file with UTF-8 encoding
- Verify Vietnamese characters: á, à, ả, ã, ạ, ă, ắ, ằ, ẳ, ẵ, ặ, â, ấ, ầ, ẩ, ẫ, ậ, etc.
- No � (replacement character)

**Report:**
- Files with encoding issues
- Corrupted character locations

---

### Check 4: Format String Preservation

**Validate format strings preserved:**
- `{0}`, `{1}`, `{2}`, etc.
- `{0:N0}`, `{1:F2}`, etc.
- `[NAME]`, `[PLACE]`, `[IT]`, `[ITS]`

**Method:**
1. Extract format strings from English source
2. Check same format strings exist in Vietnamese
3. Report missing or modified format strings

**Report:**
- Files with missing format strings
- Files with modified format strings
- Line numbers

---

### Check 5: Color Tag Preservation

**Validate color tags preserved:**
- Pattern: `[color=#RRGGBB]...[/color]`
- Opening and closing tags match
- Color codes unchanged

**Check:**
- Count opening tags: `[color=#`
- Count closing tags: `[/color]`
- Verify equal counts
- Verify color codes unchanged

**Report:**
- Files with mismatched color tags
- Files with missing color tags
- Line numbers

---

### Check 6: Escape Sequence Preservation

**Validate escape sequences preserved:**
- `\n` (newline)
- `\t` (tab)
- `\\` (backslash)

**Method:**
- Count escape sequences in source
- Count escape sequences in translation
- Verify counts match

**Report:**
- Files with missing escape sequences
- Line numbers

---

### Check 7: XML Attribute Preservation

**Validate XML attributes unchanged:**
- `Name="..."` attributes
- `sParam="..."` attributes
- `mz="..."` attributes
- All other attributes

**Method:**
1. Extract attributes from source
2. Extract attributes from translation
3. Compare - must be identical

**Report:**
- Files with changed attributes
- Attribute differences
- Line numbers

---

### Check 8: Dictionary Key Preservation

**Validate dictionary keys unchanged:**
- Column 1 (Chinese key) must be identical to source
- No translation of keys
- No modification of keys

**Method:**
1. Extract Column 1 from Chinese source
2. Extract Column 1 from Vietnamese translation
3. Compare - must be identical

**Report:**
- Files with changed keys
- Line numbers with differences

---

## VALIDATION PROCESS

### Step 1: Scan All Files

```
For each file in Language/Vi/:
    1. Determine file type (XML or Dictionary)
    2. Run appropriate validation checks
    3. Record results
```

### Step 2: Generate Reports

**Create reports for:**
- XML errors
- Dictionary format errors
- Encoding issues
- Format string issues
- Color tag issues
- Escape sequence issues
- Attribute changes
- Key changes

### Step 3: Categorize Issues

**Severity levels:**
- **CRITICAL** - Blocks release (XML errors, encoding issues)
- **MAJOR** - Should fix (format strings, color tags)
- **MINOR** - Nice to fix (minor formatting)

### Step 4: Create Fix List

**Prioritized list of issues to fix:**
1. Critical issues first
2. Major issues second
3. Minor issues last

---

## OUTPUT

### Validation Report

**File:** `VALIDATION_REPORT.md`

**Format:**
```markdown
# Format Validation Report

**Date:** 2026-05-03
**Files Validated:** 969
**Status:** PASS/FAIL

## Summary

- XML Files: 488 (X passed, Y failed)
- Dictionary Files: 477 (X passed, Y failed)
- Encoding: 969 (X passed, Y failed)
- Format Strings: X issues found
- Color Tags: X issues found
- Escape Sequences: X issues found

## Critical Issues (X)

### XML Errors
- File: Language/Vi/Settings/Practice/Gong/Gong_1.xml
  - Line 45: Unclosed tag <Desc>
  - Line 67: Invalid character in attribute

### Encoding Issues
- File: Language/Vi/UIText.xml
  - Line 234: Corrupted Vietnamese character

## Major Issues (X)

### Format String Issues
- File: Language/Vi/CodeDictionary.txt
  - Line 123: Missing {0} placeholder

### Color Tag Issues
- File: Language/Vi/Settings/Practice/Gong/Gong_2.xml
  - Line 34: Unclosed [color] tag

## Minor Issues (X)

[List minor issues]

## Files Requiring Fixes

1. [File path] - [Issue type] - [Severity]
2. [File path] - [Issue type] - [Severity]
...
```

---

## VALIDATION SCRIPT (Optional)

**Can create Python script for automation:**

```python
# validate_format.py
import os
import xml.etree.ElementTree as ET
import re

def validate_xml(file_path):
    try:
        ET.parse(file_path)
        return True, None
    except Exception as e:
        return False, str(e)

def validate_dictionary(file_path):
    errors = []
    with open(file_path, 'r', encoding='utf-8') as f:
        for i, line in enumerate(f, 1):
            if '\t' not in line:
                errors.append(f"Line {i}: No TAB separator")
            elif line.count('\t') != 1:
                errors.append(f"Line {i}: Multiple TABs")
    return len(errors) == 0, errors

# ... more validation functions
```

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Validate ALL 969 files**  
✅ **Check all validation points**  
✅ **Generate comprehensive report**  
✅ **Categorize by severity**  
✅ **Provide line numbers for issues**  
✅ **Create prioritized fix list**  

### MUST NOT DO

❌ **Do NOT skip files**  
❌ **Do NOT ignore critical issues**  
❌ **Do NOT fix issues** (report only)  

---

## SUCCESS CRITERIA

1. ✅ All 969 files validated
2. ✅ Comprehensive report generated
3. ✅ All issues documented
4. ✅ Issues categorized by severity
5. ✅ Fix list prioritized
6. ✅ Ready for fixes or next phase

---

## DELIVERABLES

### Required
- ✅ `VALIDATION_REPORT.md` (comprehensive report)
- ✅ Issue list (prioritized)

### Optional
- ✅ `validate_format.py` (validation script)
- ✅ Per-file validation logs

---

## TIPS

1. **Automate where possible** - Use scripts for repetitive checks
2. **Validate incrementally** - Check modules as they complete
3. **Focus on critical issues** - XML and encoding first
4. **Provide clear line numbers** - Easy to locate issues
5. **Test fixes** - Re-validate after fixes applied

---

**Agent Status:** Ready to execute  
**Prerequisites:** Phase 3 complete (all files translated)  
**Created:** 2026-05-03  
**Version:** 1.0
