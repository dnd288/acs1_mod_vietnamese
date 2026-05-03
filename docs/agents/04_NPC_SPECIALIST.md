# AGENT INSTRUCTION: NPC SPECIALIST

**Agent Name:** NPC Specialist  
**Agent ID:** 04_NPC_SPECIALIST  
**Priority:** P2  
**Estimated Time:** 10-12 hours

---

## OBJECTIVE

Translate all NPC-related content (55 files) including character races, features, moods, relationships, backstories, and experience definitions.

---

## PREREQUISITES

### Required
- ✅ GLOSSARY.md exists
- ✅ Phase 0 complete (Language/Vi/ structure ready)

### Input Sources

**Chinese Source:**
```
refs/cn/Npc/
├── Backstories/      - Character backgrounds
├── Body/             - Body types (14 files)
├── Damages/          - Damage types
├── Experience/       - Experience definitions
├── Favour/           - Favor/relationship system
├── Features/         - Character features (9 files)
├── Moods/            - Mood states
├── Race/             - Races (10 files)
├── Reincarnate/      - Reincarnation system
└── Relation/         - Relationships
```

**English Reference:**
```
refs/en/Settings/Npc/
```

**Vietnamese Template:**
```
Language/Vi/Settings/Npc/
```

---

## OUTPUT

**Target:** `Language/Vi/Settings/Npc/` (55 files translated)

---

## KEY TERMINOLOGY

### Character Roles (from GLOSSARY)

| Chinese | Vietnamese | English |
|---------|------------|---------|
| 弟子 | đệ tử | disciple |
| 师父 | sư phụ | master |
| 师兄 | sư huynh | senior brother |
| 师姐 | sư tỷ | senior sister |
| 师弟 | sư đệ | junior brother |
| 师妹 | sư muội | junior sister |
| 长老 | trưởng lão | elder |
| 宗主 | tông chủ | sect leader |
| 掌门 | chưởng môn | sect head |
| 修士 | tu sĩ | cultivator |

### Races

| Chinese | Vietnamese | Notes |
|---------|------------|-------|
| 人族 | Nhân tộc | Human race |
| 妖族 | Yêu tộc | Demon/spirit race |
| 仙族 | Tiên tộc | Immortal race |
| 灵兽 | Linh thú | Spirit beast |

### Attributes (from GLOSSARY)

| Chinese | Vietnamese | English |
|---------|------------|---------|
| 悟性 | ngộ tính | comprehension |
| 气感 | khí cảm | qi sensitivity |
| 耐力 | nại lực | endurance |
| 心境 | tâm cảnh | mental state |
| 寿命 | thọ mệnh | lifespan |

---

## TRANSLATION PROCESS

### XML File Format (Race, Features, etc.)

```xml
<Texts Type="Other">
    <List>
        <Text Name="Human">
            <DisplayName>人族</DisplayName>
            <Desc>普通的动物：人类</Desc>
            <MaleName>男</MaleName>
            <FemaleName>女</FemaleName>
        </Text>
    </List>
</Texts>
```

**Translation:**
```xml
<Texts Type="Other">
    <List>
        <Text Name="Human">
            <DisplayName>Nhân tộc</DisplayName>
            <Desc>Động vật thông thường: Con người</Desc>
            <MaleName>Nam</MaleName>
            <FemaleName>Nữ</FemaleName>
        </Text>
    </List>
</Texts>
```

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Use GLOSSARY for cultivation terms**  
✅ **Preserve XML structure and attributes**  
✅ **Keep Name attributes unchanged**  
✅ **Preserve color tags and format strings**  
✅ **Translate character names descriptively**  
✅ **Use proper Vietnamese diacritics**  

### MUST NOT DO

❌ **Do NOT translate Name attributes**  
❌ **Do NOT change XML structure**  
❌ **Do NOT use Thai/English as Vietnamese**  
❌ **Do NOT skip GLOSSARY check**  

---

## VALIDATION CHECKLIST

- [ ] All 55 files translated
- [ ] No Chinese/Thai/English remaining
- [ ] All Name attributes unchanged
- [ ] All cultivation terms from GLOSSARY
- [ ] XML well-formed
- [ ] UTF-8 encoding
- [ ] Character terminology consistent

---

## SUCCESS CRITERIA

1. ✅ All 55 files completely translated
2. ✅ Character terminology consistent with GLOSSARY
3. ✅ All XML structures preserved
4. ✅ Cultural context maintained

---

## TIPS

1. **Start with Race/** - Foundational terminology
2. **Backstories have narrative text** - Read carefully for context
3. **Features are descriptive** - Keep tone appropriate
4. **Check English for relationship terms** - Ensure accuracy

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Created:** 2026-05-03  
**Version:** 1.0
