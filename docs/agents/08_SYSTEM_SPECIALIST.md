# AGENT INSTRUCTION: SYSTEM SPECIALIST

**Agent Name:** System Specialist  
**Agent ID:** 08_SYSTEM_SPECIALIST  
**Priority:** P3  
**Estimated Time:** 47 hours

---

## OBJECTIVE

Translate all remaining Settings/ modules (~200 files across 23+ subdirectories) that are not covered by other specialist agents.

---

## PREREQUISITES

### Required
- ✅ GLOSSARY.md exists
- ✅ Phase 0 complete

### Input Sources

**Chinese Source:**
```
refs/cn/
```

**English Reference:**
```
refs/en/Settings/
```

**Vietnamese Template:**
```
Language/Vi/Settings/
```

---

## MODULES TO TRANSLATE

### High Priority Modules

1. **Jianghu/** (13 files) - Martial world system
2. **Esoterica/** (13 files) - Secret techniques
3. **Modifiers/** (37 files) - Game modifiers
4. **Trade/** (36 files) - Trading system
5. **Zhen/** (13 files) - Formation arrays
6. **LingShou/** (15 files) - Spirit beasts
7. **Teaching/** (5 files) - Tutorial content

### Medium Priority Modules

8. **Mutation/** (10 files) - Character mutations
9. **NpcStories/** (8 files) - NPC storylines
10. **NpcBiography/** (2 files) - NPC biographies
11. **RPG/** (24 files) - RPG mode content
12. **Property/** (7 files) - Character properties
13. **Secrets/** (2 files) - Secret knowledge
14. **Outspread/** (14 files) - Expansion content

### Low Priority Modules

15. **Weather/** (6 files) - Weather system
16. **HumanoidEvolution/** (8 files) - Character evolution
17. **Fight/** (15 files) - Combat system
18. **MsgShow/** (3 files) - Message display
19. **JobDef/** (8 files) - Job definitions
20. **Cosmetics/** (1 file) - Cosmetic items
21. **ElixirGas/** (1 file) - Alchemy/elixir
22. **TerrainDef/** (2 files) - Terrain definitions
23. **Achievement/** (1 file) - Achievements
24. **Tang/** (1 file) - Tang dynasty content
25. **Input/** (1 file) - Input settings
26. **IllustratedHand/** (1 file) - Illustrated handbook
27. **SeasonAffix/** (1 file) - Seasonal modifiers
28. **GameGraphAffix/** (1 file) - Game graph effects
29. **CommandDef/** (1 file) - Command definitions
30. **Sacrifices/** (2 files) - Sacrifice system
31. **Rewards/** (2 files) - Reward system
32. **Reward/** (3 files) - Individual rewards
33. **Fun/** (1 file) - Fun/entertainment content
34. **Share/** (1 file) - Sharing features
35. **PlantGroups/** (3 files) - Plant groupings

---

## OUTPUT

**Target:** All remaining `Language/Vi/Settings/` subdirectories (~200 files)

---

## TRANSLATION APPROACH

### General Process

1. **Work module by module** - Complete one subdirectory at a time
2. **Check GLOSSARY** - For all cultivation terms
3. **Preserve XML structure** - All attributes unchanged
4. **Preserve special elements** - Format strings, color tags
5. **Validate incrementally** - Check XML after each module

### Module-Specific Notes

**Jianghu/** - Martial world terminology, use GLOSSARY  
**Esoterica/** - Secret techniques, keep mysterious tone  
**Modifiers/** - Game mechanics, be precise  
**Trade/** - Economic terms, use standard Vietnamese  
**Zhen/** - Formation arrays, use GLOSSARY (阵法 → trận pháp)  
**LingShou/** - Spirit beasts, use GLOSSARY (灵兽 → linh thú)  
**Teaching/** - Tutorial text, be clear and instructive  

---

## KEY TERMINOLOGY BY MODULE

### Jianghu (Martial World)

| Chinese | Vietnamese | English |
|---------|------------|---------|
| 江湖 | giang hồ | martial world |
| 武林 | võ lâm | martial arts world |
| 侠客 | hiệp khách | martial hero |
| 门派 | môn phái | sect |

### Zhen (Formations)

| Chinese | Vietnamese | English |
|---------|------------|---------|
| 阵法 | trận pháp | formation |
| 法阵 | pháp trận | magic array |
| 禁制 | cấm chế | restriction |
| 结界 | kết giới | barrier |

### LingShou (Spirit Beasts)

| Chinese | Vietnamese | English |
|---------|------------|---------|
| 灵兽 | linh thú | spirit beast |
| 妖兽 | yêu thú | demon beast |
| 凶兽 | hung thú | fierce beast |

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Use GLOSSARY for all cultivation terms**  
✅ **Preserve XML structure and attributes**  
✅ **Keep Name attributes unchanged**  
✅ **Preserve format strings and color tags**  
✅ **Work systematically module by module**  
✅ **Validate XML after each module**  

### MUST NOT DO

❌ **Do NOT skip modules** - Translate all  
❌ **Do NOT translate Name attributes**  
❌ **Do NOT change XML structure**  
❌ **Do NOT rush** - Quality over speed  

---

## VALIDATION CHECKLIST

### Per Module
- [ ] All files in module translated
- [ ] No Chinese/Thai/English remaining
- [ ] All attributes unchanged
- [ ] All cultivation terms from GLOSSARY
- [ ] XML well-formed
- [ ] UTF-8 encoding

### Overall
- [ ] All ~200 files translated
- [ ] All 23+ modules complete
- [ ] Terminology consistent across modules
- [ ] Ready for QC phase

---

## SUCCESS CRITERIA

1. ✅ All ~200 files completely translated
2. ✅ All modules covered
3. ✅ Terminology consistent with GLOSSARY
4. ✅ All XML structures preserved
5. ✅ Quality maintained throughout

---

## TIPS

1. **Start with high priority modules** - Most important first
2. **Work in batches** - Complete 5-10 files, then validate
3. **Take breaks** - This is a long task
4. **Track progress** - Mark completed modules
5. **Ask for help** - If terminology unclear

---

## ESTIMATED BREAKDOWN

| Priority | Modules | Files | Hours |
|----------|---------|-------|-------|
| High | 7 modules | ~130 | 25-30h |
| Medium | 7 modules | ~50 | 12-15h |
| Low | 21 modules | ~20 | 10-12h |
| **TOTAL** | **35 modules** | **~200** | **47h** |

---

## PROGRESS TRACKING

### High Priority
- [ ] Jianghu/ (13 files)
- [ ] Esoterica/ (13 files)
- [ ] Modifiers/ (37 files)
- [ ] Trade/ (36 files)
- [ ] Zhen/ (13 files)
- [ ] LingShou/ (15 files)
- [ ] Teaching/ (5 files)

### Medium Priority
- [ ] Mutation/ (10 files)
- [ ] NpcStories/ (8 files)
- [ ] NpcBiography/ (2 files)
- [ ] RPG/ (24 files)
- [ ] Property/ (7 files)
- [ ] Secrets/ (2 files)
- [ ] Outspread/ (14 files)

### Low Priority
- [ ] Weather/ (6 files)
- [ ] HumanoidEvolution/ (8 files)
- [ ] Fight/ (15 files)
- [ ] MsgShow/ (3 files)
- [ ] JobDef/ (8 files)
- [ ] Cosmetics/ (1 file)
- [ ] ElixirGas/ (1 file)
- [ ] TerrainDef/ (2 files)
- [ ] Achievement/ (1 file)
- [ ] Tang/ (1 file)
- [ ] Input/ (1 file)
- [ ] IllustratedHand/ (1 file)
- [ ] SeasonAffix/ (1 file)
- [ ] GameGraphAffix/ (1 file)
- [ ] CommandDef/ (1 file)
- [ ] Sacrifices/ (2 files)
- [ ] Rewards/ (2 files)
- [ ] Reward/ (3 files)
- [ ] Fun/ (1 file)
- [ ] Share/ (1 file)
- [ ] PlantGroups/ (3 files)

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Created:** 2026-05-03  
**Version:** 1.0
