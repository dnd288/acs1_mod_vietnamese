# AGENT INSTRUCTION: ITEM SPECIALIST

**Agent Name:** Item Specialist  
**Agent ID:** 05_ITEM_SPECIALIST  
**Priority:** P2  
**Estimated Time:** 12-15 hours

---

## OBJECTIVE

Translate all item definitions (74 files) including buildings, items, plants, rocks, and NPC-related things.

---

## PREREQUISITES

### Required
- ✅ GLOSSARY.md exists
- ✅ Phase 0 complete

### Input Sources

**Chinese Source:**
```
refs/cn/ThingDef/
├── Building/         - Buildings (15 files)
├── Item/             - Items
├── Plant/            - Plants
├── Rock/             - Rocks/minerals
├── RSThingType/      - Thing type definitions
└── ThingNpc.xml      - NPC-related things
```

**English Reference:**
```
refs/en/Settings/ThingDef/
```

**Vietnamese Template:**
```
Language/Vi/Settings/ThingDef/
```

---

## OUTPUT

**Target:** `Language/Vi/Settings/ThingDef/` (74 files translated)

---

## KEY TERMINOLOGY

### Item Types

| Chinese | Vietnamese | English | Notes |
|---------|------------|---------|-------|
| 灵石 | linh thạch | spirit stone | Currency/energy |
| 灵草 | linh thảo | spirit herb | Spiritual plant |
| 灵药 | linh dược | spirit medicine | Medicine |
| 丹药 | đan dược | pill/elixir | Alchemy product |
| 法宝 | pháp bảo | magic treasure | Artifact |
| 法器 | pháp khí | magic tool | Implement |
| 神器 | thần khí | divine artifact | Divine treasure |
| 建筑材料 | vật liệu xây dựng | building material | Construction |

### Building Terms

| Chinese | Vietnamese | English | Notes |
|---------|------------|---------|-------|
| 建筑 | kiến trúc | building | General term |
| 房间 | phòng | room | Interior space |
| 地板 | sàn nhà | floor | Ground surface |
| 墙壁 | tường | wall | Vertical surface |
| 屋顶 | mái nhà | roof | Top surface |

---

## TRANSLATION PROCESS

### XML File Format (ThingDef)

```xml
<Texts Type="Thing">
    <List>
        <Text Name="FloorBase" sParam="Building">
            <ThingName>铺地板</ThingName>
            <Desc>可以用各种材料建造的装饰地板</Desc>
        </Text>
    </List>
</Texts>
```

**Translation:**
```xml
<Texts Type="Thing">
    <List>
        <Text Name="FloorBase" sParam="Building">
            <ThingName>Lát sàn</ThingName>
            <Desc>Sàn trang trí có thể được làm từ nhiều loại vật liệu khác nhau</Desc>
        </Text>
    </List>
</Texts>
```

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Use GLOSSARY for cultivation items**  
✅ **Preserve XML structure and all attributes**  
✅ **Keep Name and sParam attributes unchanged**  
✅ **Preserve color tags and format strings**  
✅ **Translate descriptive text naturally**  
✅ **Use proper Vietnamese terminology for items**  

### MUST NOT DO

❌ **Do NOT translate Name or sParam attributes**  
❌ **Do NOT change XML structure**  
❌ **Do NOT use Thai/English as Vietnamese**  
❌ **Do NOT skip GLOSSARY check for cultivation items**  

---

## VALIDATION CHECKLIST

- [ ] All 74 files translated
- [ ] No Chinese/Thai/English remaining
- [ ] All attributes unchanged
- [ ] All cultivation items from GLOSSARY
- [ ] XML well-formed
- [ ] UTF-8 encoding
- [ ] Item terminology consistent

---

## SUCCESS CRITERIA

1. ✅ All 74 files completely translated
2. ✅ Item terminology consistent with GLOSSARY
3. ✅ All XML structures preserved
4. ✅ Descriptions natural and accurate

---

## TIPS

1. **Start with Building/** - Most files, clear patterns
2. **Items have specific naming conventions** - Check English for consistency
3. **Plant names may need botanical terms** - Research if needed
4. **Rock/mineral names are specific** - Use geological Vietnamese terms

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Created:** 2026-05-03  
**Version:** 1.0
