# AGENT INSTRUCTION: CORE TRANSLATION

**Agent Name:** Core Translation Agent  
**Agent ID:** 02_CORE_TRANSLATION  
**Priority:** P1 - HIGH (Blocks Phase 3)  
**Estimated Time:** 18-23 hours

---

## OBJECTIVE

Translate the 3 most critical files that form the foundation of the game's user interface and system messages:
1. UIText.xml (3,583 lines)
2. CodeDictionary.txt (4,435 lines)
3. MapStoryDictionary.txt (1,897 lines)

**Total:** 9,915 lines of text

---

## WHY THESE FILES ARE CRITICAL

1. **UIText.xml** - All UI strings users see first (buttons, menus, labels)
2. **CodeDictionary.txt** - System messages and game mechanics text
3. **MapStoryDictionary.txt** - Story events and narrative content

**These files provide foundation for understanding game terminology before translating specialized modules.**

---

## PREREQUISITES

### Required
- ✅ Phase 1 complete: `GLOSSARY.md` exists
- ✅ Phase 0 complete: `Language/Vi/` structure ready

### Input Files

**English Source:**
- `refs/en/UIText.xml`
- `refs/en/CodeDictionary.txt`
- `refs/en/MapStoryDictionary.txt`

**Vietnamese Template:**
- `Language/Vi/UIText.xml` (currently Thai text)
- `Language/Vi/CodeDictionary.txt` (currently Thai text)
- `Language/Vi/MapStoryDictionary.txt` (currently Thai text)

**Reference:**
- `GLOSSARY.md` (cultivation terminology)

---

## OUTPUT FILES

- `Language/Vi/UIText.xml` (3,583 lines translated)
- `Language/Vi/CodeDictionary.txt` (4,435 lines translated)
- `Language/Vi/MapStoryDictionary.txt` (1,897 lines translated)

---

## TASK 1: TRANSLATE UIText.xml (6-8 hours)

### File Format

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="0xrxw6g7qkn8ovp3-n143_bpyo" mz="confirm">Combine</string>
    <string name="0xrxw6g7rz8yjt-n18_izp4" mz="title">Lost Childhood</string>
    ...
</resources>
```

### Translation Process

**For each `<string>` entry:**

1. **Read English text**
   ```xml
   <string name="0xrxw6g7qkn8ovp3-n143_bpyo" mz="confirm">Combine</string>
   ```

2. **Translate to Vietnamese**
   - Check GLOSSARY for cultivation terms
   - Translate English → Vietnamese
   - Keep concise (UI space limited)

3. **Preserve attributes**
   - `name` attribute: KEEP UNCHANGED
   - `mz` attribute: KEEP UNCHANGED
   - Only translate text content

4. **Preserve special elements**
   - Format strings: `{0}`, `{1}`, `{1:N0}`, `{0:F2}`
   - Placeholders: `[NAME]`, `[PLACE]`, `[IT]`, `[ITS]`
   - Color tags: `[color=#D06508]...[/color]`
   - Escape sequences: `\n`, `\t`

5. **Write to Vietnamese file**
   ```xml
   <string name="0xrxw6g7qkn8ovp3-n143_bpyo" mz="confirm">Hợp nhất</string>
   ```

### Examples

**Example 1: Simple UI Label**
```xml
<!-- English -->
<string name="0xrxw6g7snc6ovpc-n8_snc6" mz="n8">Cancel</string>

<!-- Vietnamese -->
<string name="0xrxw6g7snc6ovpc-n8_snc6" mz="n8">Hủy</string>
```

**Example 2: With Format String**
```xml
<!-- English -->
<string name="0xrxw6g7h4ds2ovss-n24_t8dw" mz="daohang">Manual Pavilion Capacity: 150/5000</string>

<!-- Vietnamese -->
<string name="0xrxw6g7h4ds2ovss-n24_t8dw" mz="daohang">Sức chứa Các Kinh Các: 150/5000</string>
```

**Example 3: With Placeholder**
```xml
<!-- English -->
<string name="..." mz="...">You will lose all unsaved progress. Are you sure you want to load saved game {0}?</string>

<!-- Vietnamese -->
<string name="..." mz="...">Bạn sẽ mất toàn bộ tiến trình chưa lưu. Bạn có chắc muốn tải game đã lưu {0}?</string>
```

**Example 4: With Color Tag**
```xml
<!-- English -->
<string name="..." mz="...">[color=#D06508]This bottleneck is harder for high comprehension.[/color]</string>

<!-- Vietnamese -->
<string name="..." mz="...">[color=#D06508]Bình cổ này khó hơn với ngộ tính cao.[/color]</string>
```

### Validation

After translation:
- [ ] All 3,583 lines translated
- [ ] All `name` attributes unchanged
- [ ] All `mz` attributes unchanged
- [ ] All format strings preserved
- [ ] All color tags preserved
- [ ] XML well-formed (validate with parser)
- [ ] UTF-8 encoding

---

## TASK 2: TRANSLATE CodeDictionary.txt (8-10 hours)

### File Format

```
Key<TAB>Value
看天花板	Looking At The Ceiling
神修在心境为"灵"时，心境已然圆满，将持续上升，不收任何外部条件影响。	When the mental state is 'spiritual', it will be fulfilled and raised at a steady pace, not affected by outside factors.
```

### Translation Process

**For each line:**

1. **Split by TAB**
   - Column 1: Chinese Key (看天花板)
   - Column 2: English Value (Looking At The Ceiling)

2. **Keep Column 1 UNCHANGED**
   - This is the Chinese key - DO NOT TRANSLATE
   - DO NOT MODIFY

3. **Translate Column 2**
   - English → Vietnamese
   - Check GLOSSARY for cultivation terms
   - Preserve format strings and color tags

4. **Join with TAB**
   - MUST use TAB character (not space)
   - Format: `Key<TAB>Vietnamese_Translation`

5. **Write to Vietnamese file**

### Examples

**Example 1: Simple Message**
```
<!-- English -->
看天花板	Looking At The Ceiling

<!-- Vietnamese -->
看天花板	Nhìn lên trần nhà
```

**Example 2: With Format String**
```
<!-- English -->
门派弟子数量达到上限:{0}。\n你可以扩大门派规模或者将其他弟子踢出门派。	The number of disciples has reached the cap: {0}.\nYou can increase the size of your sect or kick another disciple.

<!-- Vietnamese -->
门派弟子数量达到上限:{0}。\n你可以扩大门派规模或者将其他弟子踢出门派。	Số lượng đệ tử đã đạt giới hạn: {0}.\nBạn có thể mở rộng quy mô môn phái hoặc trục xuất đệ tử khác.
```

**Example 3: With Cultivation Term (Use GLOSSARY)**
```
<!-- English -->
神修在心境为"灵"时，心境已然圆满，将持续上升，不收任何外部条件影响。	When the mental state is 'spiritual', it will be fulfilled and raised at a steady pace, not affected by outside factors.

<!-- Vietnamese -->
神修在心境为"灵"时，心境已然圆满，将持续上升，不收任何外部条件影响。	Khi tâm cảnh ở trạng thái 'linh', tâm cảnh đã viên mãn, sẽ tiếp tục tăng đều đặn, không bị ảnh hưởng bởi yếu tố bên ngoài.
```
*(Note: 心境 → tâm cảnh from GLOSSARY)*

**Example 4: With Color Tag**
```
<!-- English -->
{2}\n灵气值：{0:N0}/{1:N0}\n法宝在空闲时，或灵气耗完后会从角色身上吸取灵气。	{2}\nQi: {0:N0}/{1:N0}\nWhen an artifact is idle or has used up its Qi, it will absorb Qi from the character.

<!-- Vietnamese -->
{2}\n灵气值：{0:N0}/{1:N0}\n法宝在空闲时，或灵气耗完后会从角色身上吸取灵气。	{2}\nLinh khí: {0:N0}/{1:N0}\nKhi pháp bảo nhàn rỗi hoặc đã dùng hết linh khí, nó sẽ hấp thụ linh khí từ nhân vật.
```

### Validation

After translation:
- [ ] All 4,435 lines translated
- [ ] Column 1 (Chinese Key) UNCHANGED
- [ ] Column 2 (Value) translated to Vietnamese
- [ ] TAB separator used (not space)
- [ ] All format strings preserved
- [ ] All color tags preserved
- [ ] All escape sequences preserved
- [ ] UTF-8 encoding

---

## TASK 3: TRANSLATE MapStoryDictionary.txt (4-5 hours)

### File Format

Same as CodeDictionary.txt:
```
Key<TAB>Value
目标对玩家发起攻击	Target is attacking
计时器，fParam1为秒数	Timer fParam1 (seconds)
```

### Translation Process

**Same as Task 2:**
1. Column 1 (Chinese Key) - KEEP UNCHANGED
2. Column 2 (English Value) - TRANSLATE to Vietnamese
3. Use TAB separator
4. Preserve format strings and special elements

### Examples

**Example 1: Story Event**
```
<!-- English -->
你竟敢闯入这里，但你可知道，这份荣耀需要你付出生命为代价！	You dare to intrude here. Do you know that this honor requires you to pay with your life?

<!-- Vietnamese -->
你竟敢闯入这里，但你可知道，这份荣耀需要你付出生命为代价！	Ngươi dám xâm nhập nơi này. Ngươi có biết rằng vinh dự này đòi hỏi ngươi phải trả giá bằng mạng sống?
```

**Example 2: With Placeholder**
```
<!-- English -->
{0}只将少量食物分给了路人，几乎没人通过这次活动认识我们。	{0} distributed a small amount of food to passersby, but almost no one got to know us through this activity.

<!-- Vietnamese -->
{0}只将少量食物分给了路人，几乎没人通过这次活动认识我们。	{0} đã phát một lượng nhỏ thức ăn cho người qua đường, nhưng hầu như không ai biết đến chúng ta qua hoạt động này.
```

### Validation

After translation:
- [ ] All 1,897 lines translated
- [ ] Column 1 (Chinese Key) UNCHANGED
- [ ] Column 2 (Value) translated to Vietnamese
- [ ] TAB separator used
- [ ] All format strings preserved
- [ ] UTF-8 encoding

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Translate all text** - No English/Thai remaining  
✅ **Use GLOSSARY** - Check for cultivation terms  
✅ **Preserve attributes** - `name`, `mz` in XML  
✅ **Preserve format strings** - `{0}`, `{1:N0}`, etc.  
✅ **Preserve placeholders** - `[NAME]`, `[PLACE]`, etc.  
✅ **Preserve color tags** - `[color=#...]...[/color]`  
✅ **Preserve escape sequences** - `\n`, `\t`  
✅ **Use TAB separator** - In dictionary files  
✅ **Keep Column 1 unchanged** - Chinese keys in dictionaries  
✅ **UTF-8 encoding** - All files  
✅ **Validate XML** - Ensure well-formed  

### MUST NOT DO

❌ **Do NOT translate XML attributes** - `name`, `mz`  
❌ **Do NOT translate Chinese keys** - Column 1 in dictionaries  
❌ **Do NOT change format strings** - `{0}` must stay `{0}`  
❌ **Do NOT remove color tags** - Must preserve exactly  
❌ **Do NOT use space separator** - Must use TAB in dictionaries  
❌ **Do NOT change encoding** - Must be UTF-8  
❌ **Do NOT add/remove tags** - XML structure unchanged  

---

## SPECIAL CASES

### Format String Patterns

**Pattern:** `{N}` or `{N:FORMAT}`

**Examples:**
```
{0} → {0} (unchanged)
{1:N0} → {1:N0} (unchanged)
{0:F2} → {0:F2} (unchanged)
{0}天 → {0} ngày (add space before Vietnamese unit)
{0}个 → {0} (Vietnamese doesn't need classifier here)
```

### Color Tag Patterns

**Pattern:** `[color=#RRGGBB]text[/color]`

**Example:**
```
[color=#D06508]此瓶颈悟性越高，越难突破。[/color]
→
[color=#D06508]Bình cổ này ngộ tính càng cao, càng khó đột phá.[/color]
```

### Escape Sequences

**Patterns:**
- `\n` - Newline (preserve)
- `\t` - Tab (preserve)
- `\\` - Backslash (preserve)

---

## VALIDATION CHECKLIST

### Per File

**UIText.xml:**
- [ ] All 3,583 entries translated
- [ ] XML well-formed (no syntax errors)
- [ ] All `name` attributes unchanged
- [ ] All `mz` attributes unchanged
- [ ] All format strings preserved
- [ ] All color tags preserved
- [ ] UTF-8 encoding

**CodeDictionary.txt:**
- [ ] All 4,435 lines translated
- [ ] Column 1 (Chinese) unchanged
- [ ] Column 2 (Vietnamese) translated
- [ ] TAB separator used
- [ ] All format strings preserved
- [ ] All color tags preserved
- [ ] UTF-8 encoding

**MapStoryDictionary.txt:**
- [ ] All 1,897 lines translated
- [ ] Column 1 (Chinese) unchanged
- [ ] Column 2 (Vietnamese) translated
- [ ] TAB separator used
- [ ] All format strings preserved
- [ ] UTF-8 encoding

### Overall

- [ ] All 9,915 lines translated
- [ ] GLOSSARY terms used consistently
- [ ] No English/Thai text remaining
- [ ] All special elements preserved
- [ ] Files ready for Phase 3

---

## DELIVERABLES

### Required
- ✅ `Language/Vi/UIText.xml` (translated)
- ✅ `Language/Vi/CodeDictionary.txt` (translated)
- ✅ `Language/Vi/MapStoryDictionary.txt` (translated)

### Optional
- ✅ Translation log (issues encountered)
- ✅ Term usage report (new terms not in GLOSSARY)

---

## SUCCESS CRITERIA

**This agent succeeds when:**

1. ✅ All 3 files completely translated
2. ✅ All format strings preserved
3. ✅ All color tags preserved
4. ✅ XML validation passed
5. ✅ Dictionary format correct
6. ✅ GLOSSARY terms used consistently
7. ✅ UTF-8 encoding verified
8. ✅ No English/Thai text remaining

---

## NEXT AGENT

After completing this agent:

**→ Phase 3: Parallel Translation**
- Multiple specialist agents can start
- Practice Specialist (highest priority)
- NPC, Item, World, UI, System, Dictionary specialists

---

## TIPS FOR SUCCESS

1. **Work file by file** - Complete UIText.xml first, then dictionaries
2. **Use find/replace carefully** - For common terms
3. **Check GLOSSARY frequently** - Especially for cultivation terms
4. **Validate incrementally** - Check XML after every 500 lines
5. **Keep format strings intact** - Copy-paste to avoid typos
6. **Test TAB separator** - Use actual TAB, not spaces
7. **Save frequently** - Don't lose progress

---

## ESTIMATED BREAKDOWN

| Task | Lines | Time |
|------|-------|------|
| UIText.xml | 3,583 | 6-8h |
| CodeDictionary.txt | 4,435 | 8-10h |
| MapStoryDictionary.txt | 1,897 | 4-5h |
| **TOTAL** | **9,915** | **18-23h** |

---

## RESOURCES

### Input Files
- `refs/en/UIText.xml`
- `refs/en/CodeDictionary.txt`
- `refs/en/MapStoryDictionary.txt`

### Reference
- `GLOSSARY.md` (terminology)
- `docs/01_SOURCE_ANALYSIS.md` (file formats)
- `docs/examples/` (translation examples)

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Created:** 2026-05-03  
**Version:** 1.0
