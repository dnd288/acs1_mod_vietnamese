# AGENT INSTRUCTION: WORLD SPECIALIST

**Agent Name:** World Specialist  
**Agent ID:** 06_WORLD_SPECIALIST  
**Priority:** P2  
**Estimated Time:** 17-21 hours

---

## OBJECTIVE

Translate world settings, display names, and map story content (115 files total) across three modules:
- World/ (24 files) - World generation and settings
- Display/ (66 files) - Display names and titles
- MapStories/ (25 files) - Map story events

---

## PREREQUISITES

### Required
- ✅ GLOSSARY.md exists
- ✅ Phase 0 complete

### Input Sources

**Chinese Source:**
```
refs/cn/World/
refs/cn/Display/
refs/cn/MapStories/
```

**English Reference:**
```
refs/en/Settings/World/
refs/en/Settings/Display/
refs/en/Settings/MapStories/
```

**Vietnamese Template:**
```
Language/Vi/Settings/World/
Language/Vi/Settings/Display/
Language/Vi/Settings/MapStories/
```

---

## OUTPUT

**Target:** 
- `Language/Vi/Settings/World/` (24 files)
- `Language/Vi/Settings/Display/` (66 files)
- `Language/Vi/Settings/MapStories/` (25 files)

---

## KEY TERMINOLOGY

### Location Types (from GLOSSARY)

| Chinese | Vietnamese | English | Notes |
|---------|------------|---------|-------|
| 洞天 | động thiên | cave heaven | Blessed land |
| 福地 | phúc địa | blessed land | Fortunate place |
| 秘境 | bí cảnh | secret realm | Hidden realm |
| 仙界 | tiên giới | immortal realm | Immortal world |
| 凡界 | phàm giới | mortal realm | Mortal world |
| 门派 | môn phái | sect | Cultivation sect |
| 宗门 | tông môn | sect | Sect/clan |

### Display Name Categories

**Display/ contains:**
- `ArtItem/` - Artifact names
- `EsotericaName/` - Esoteric technique names
- `FabaoName/` - Magic treasure names
- `NpcName/` - NPC name generators
- `NpcTitle/` - NPC titles
- `RandomGong/` - Random technique names
- `SpecialName/` - Special names

---

## TRANSLATION PROCESS

### World Files (XML)

```xml
<Texts Type="Other">
    <List>
        <Text Name="WorldSetting">
            <DisplayName>世界设置</DisplayName>
            <Desc>配置世界生成参数</Desc>
        </Text>
    </List>
</Texts>
```

**Translation:**
```xml
<Texts Type="Other">
    <List>
        <Text Name="WorldSetting">
            <DisplayName>Cài đặt thế giới</DisplayName>
            <Desc>Cấu hình tham số sinh thế giới</Desc>
        </Text>
    </List>
</Texts>
```

### Display Names (Name Generators)

**For NPC names, titles, and technique names:**
- Keep Chinese transliteration for proper nouns
- Translate descriptive parts
- Maintain cultural flavor

**Example:**
```
剑仙 → Kiếm Tiên (Sword Immortal)
丹师 → Đan Sư (Pill Master)
```

### MapStories (Story Events)

**Narrative text - translate naturally:**
- Maintain story tone
- Use GLOSSARY for cultivation terms
- Preserve format strings and placeholders

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Use GLOSSARY for all cultivation terms**  
✅ **Preserve XML structure and attributes**  
✅ **Keep Name attributes unchanged**  
✅ **Preserve format strings: {0}, [NAME], etc.**  
✅ **Preserve color tags**  
✅ **Translate location names appropriately**  
✅ **Maintain narrative tone in stories**  

### MUST NOT DO

❌ **Do NOT translate Name attributes**  
❌ **Do NOT change XML structure**  
❌ **Do NOT over-translate proper nouns**  
❌ **Do NOT skip GLOSSARY check**  

---

## SPECIAL CASES

### Location Names

**Chinese sect names - transliterate:**
```
昆仑 → Côn Lôn (not "Kunlun Mountain")
武当 → Vũ Đang (not "Wudang")
峨眉 → Nga Mi (not "Emei")
```

### Technique Names

**Keep Chinese + translate meaning if needed:**
```
太极剑法 → Thái Cực Kiếm Pháp (Taiji Sword Method)
```

### Story Events

**Preserve placeholders:**
```
{0}来到了{1}，发现了一个秘境。
→
{0} đến {1}, phát hiện một bí cảnh.
```

---

## VALIDATION CHECKLIST

- [ ] World/ (24 files) translated
- [ ] Display/ (66 files) translated
- [ ] MapStories/ (25 files) translated
- [ ] All 115 files complete
- [ ] No Chinese/Thai/English remaining
- [ ] All attributes unchanged
- [ ] All format strings preserved
- [ ] All cultivation terms from GLOSSARY
- [ ] XML well-formed
- [ ] UTF-8 encoding

---

## SUCCESS CRITERIA

1. ✅ All 115 files completely translated
2. ✅ Location names appropriate and consistent
3. ✅ Story narrative natural and engaging
4. ✅ All XML structures preserved
5. ✅ Cultural context maintained

---

## TIPS

1. **Start with World/** - Simpler, establishes patterns
2. **Display/ has many name generators** - Check patterns
3. **MapStories/ is narrative** - Read for context before translating
4. **Keep proper nouns Chinese** - Don't over-translate

---

## ESTIMATED BREAKDOWN

| Module | Files | Hours |
|--------|-------|-------|
| World/ | 24 | 4-5h |
| Display/ | 66 | 8-10h |
| MapStories/ | 25 | 5-6h |
| **TOTAL** | **115** | **17-21h** |

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Created:** 2026-05-03  
**Version:** 1.0
