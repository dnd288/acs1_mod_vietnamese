# AGENT SESSION RESUME POINT

**Created:** 2026-05-03T02:43:48.982Z  
**Project:** Vietnamese Translation for Amazing Cultivation Simulator  
**Status:** Planning Phase Complete - Ready for Execution

---

## CONTEXT SUMMARY

### What We've Done

1. **Analyzed source structure:**
   - Thai mod template: `./Language/Th/` (965 files)
   - Chinese source: `refs/cn/` (1,748 files)
   - English reference: `refs/en/` (969 files)

2. **Identified translation strategy:**
   - Translate from Chinese → Vietnamese
   - Use English as reference for understanding
   - Use Thai as template for structure

3. **Designed agent architecture:**
   - 14-15 specialized agents
   - Hierarchical multi-agent system
   - Task-based approach for OpenCode

4. **Created comprehensive plan:**
   - 5 phases (Setup → Core → Parallel → QC → Finalization)
   - 969 files to translate
   - Estimated 10-12 days with parallel execution

---

## CURRENT STATE

- **Phase:** Documentation Created
- **Next Step:** Create GLOSSARY or start with agent tasks
- **Blocking:** None - ready to execute

---

## PROJECT STRUCTURE

```
acs1_mod_vietnamese/
├── AGENTS.md                    # This file - session resume point
├── Info.json                    # Mod metadata
├── Preview.png                  # Mod preview image
├── Resources/                   # Mod resources
│   └── thflag.png              # Thai flag (will add viflag.png)
├── Language/
│   ├── Config.xml              # Language configuration
│   ├── Th/                     # Thai translation (template)
│   └── Vi/                     # Vietnamese translation (to create)
└── docs/                       # Documentation (NEW)
    ├── 00_PROJECT_OVERVIEW.md
    ├── 01_SOURCE_ANALYSIS.md
    ├── 02_TRANSLATION_PLAN.md
    ├── 03_AGENT_ARCHITECTURE.md
    ├── 04_WORKFLOW.md
    ├── GLOSSARY_TEMPLATE.md
    ├── agents/                 # Agent task instructions
    │   ├── 00_COORDINATOR.md
    │   ├── 01_GLOSSARY_BUILDER.md
    │   ├── 02_CORE_TRANSLATION.md
    │   ├── 03_PRACTICE_SPECIALIST.md
    │   ├── 04_NPC_SPECIALIST.md
    │   ├── 05_ITEM_SPECIALIST.md
    │   ├── 06_WORLD_SPECIALIST.md
    │   ├── 07_UI_SPECIALIST.md
    │   ├── 08_SYSTEM_SPECIALIST.md
    │   ├── 09_DICTIONARY_SPECIALIST.md
    │   ├── 10_FORMAT_VALIDATOR.md
    │   └── 11_CONSISTENCY_VALIDATOR.md
    └── examples/               # Translation examples
        ├── xml_translation_example.md
        └── dictionary_translation_example.md
```

---

## QUICK START GUIDE

### For New Session

1. **Read this file first** to understand context
2. **Check docs/00_PROJECT_OVERVIEW.md** for high-level overview
3. **Review docs/03_AGENT_ARCHITECTURE.md** to understand agent roles
4. **Start execution** with Phase 0 or Phase 1

### Execution Order

```
Phase 0: SETUP (Manual)
├─> Copy Language/Th/ to Language/Vi/
├─> Update Info.json
├─> Update Language/Config.xml
└─> Create viflag.png

Phase 1: GLOSSARY (Critical - Do First!)
└─> Follow: docs/agents/01_GLOSSARY_BUILDER.md
    Output: GLOSSARY.md

Phase 2: CORE TRANSLATION
└─> Follow: docs/agents/02_CORE_TRANSLATION.md
    Files: UIText.xml, CodeDictionary.txt, MapStoryDictionary.txt

Phase 3: PARALLEL TRANSLATION (Can run in parallel)
├─> docs/agents/03_PRACTICE_SPECIALIST.md (Priority: HIGH)
├─> docs/agents/04_NPC_SPECIALIST.md
├─> docs/agents/05_ITEM_SPECIALIST.md
├─> docs/agents/06_WORLD_SPECIALIST.md
├─> docs/agents/07_UI_SPECIALIST.md
├─> docs/agents/08_SYSTEM_SPECIALIST.md
└─> docs/agents/09_DICTIONARY_SPECIALIST.md

Phase 4: QUALITY CONTROL
├─> docs/agents/10_FORMAT_VALIDATOR.md
└─> docs/agents/11_CONSISTENCY_VALIDATOR.md

Phase 5: FINALIZATION
└─> Git commit & push
```

---

## KEY DECISIONS MADE

1. **Translation Source:** Chinese → Vietnamese (not Thai → Vietnamese)
2. **Agent Approach:** Task-based with detailed markdown instructions
3. **GLOSSARY:** Critical dependency - must create first
4. **Validation:** Two-stage (Format + Consistency)
5. **Parallel Execution:** 7-8 agents can run simultaneously

---

## IMPORTANT CONSTRAINTS

### Format Preservation Rules

**MUST preserve:**
- Format strings: `{0}`, `{1}`, `{1:N0}`, `{0:F2}`
- Placeholders: `[NAME]`, `[PLACE]`, `[IT]`, `[ITS]`
- Color tags: `[color=#D06508]...[/color]`
- Escape sequences: `\n`, `\t`
- XML attributes: `Name="..."`, `sParam="..."`
- Dictionary format: Tab-separated (NOT space)

**MUST NOT:**
- Change XML structure
- Translate attribute values
- Change encoding (must be UTF-8)
- Add/remove tags
- Change Key column in Dictionary files

### Terminology Rules

**MUST:**
- Use GLOSSARY.md for all cultivation terms
- Maintain consistency across all files
- Use proper Vietnamese diacritics
- Follow cultivation novel translation conventions

**Examples:**
- 修炼 → tu luyện (ALWAYS)
- 境界 → cảnh giới (ALWAYS)
- 筑基 → Trúc Cơ (ALWAYS)
- 金丹 → Kim Đan (ALWAYS)

---

## FILE LOCATIONS

### Source Files
- **Chinese:** `refs/cn/`
- **English:** `refs/en/`
- **Thai Template:** `./Language/Th/`

### Output Files
- **Vietnamese:** `./Language/Vi/`
- **GLOSSARY:** `./GLOSSARY.md`

### Documentation
- **All docs:** `./docs/`
- **Agent tasks:** `./docs/agents/`
- **Examples:** `./docs/examples/`

---

## STATISTICS

- **Total files to translate:** 969 files
- **Total size:** ~17.3 MB
- **File types:** XML (488), Dictionary/TXT (477), Other (4)
- **Estimated effort:** 155-191 hours sequential, 10-12 days parallel
- **Number of agents:** 14-15 specialized agents

### Breakdown by Module

| Module | Files | Priority | Estimated Hours |
|--------|-------|----------|-----------------|
| Core (UIText, Dictionaries) | 3 | P1 | 18-23h |
| Practice/ | 79 | P2-High | 20-25h |
| ThingDef/ | 74 | P2 | 12-15h |
| Display/ | 66 | P2 | 8-10h |
| Npc/ | 55 | P2 | 10-12h |
| System (various) | ~200 | P3 | 47h |
| SL/ (Dictionaries) | 177 | P4 | 26-33h |
| QC | All | P5 | 10-13h |

---

## HOW TO RESUME THIS SESSION

### Option 1: Continue with Next Phase
```
"Continue with Phase [0/1/2/3/4/5]"
or
"Start with [GLOSSARY/CORE/PRACTICE/etc.]"
```

### Option 2: Review Documentation
```
"Show me [specific doc file]"
or
"Explain [specific concept]"
```

### Option 3: Execute Specific Agent Task
```
"Execute agent task: [agent name]"
or
"Follow docs/agents/[XX_AGENT_NAME].md"
```

### Option 4: Check Progress
```
"Show translation progress"
or
"What's the current status?"
```

---

## NEXT RECOMMENDED ACTIONS

### If Starting Fresh:
1. Read `docs/00_PROJECT_OVERVIEW.md`
2. Execute Phase 0 (Setup)
3. Execute `docs/agents/01_GLOSSARY_BUILDER.md`

### If Continuing:
1. Check which phase is complete
2. Continue with next agent task
3. Update progress in this file

### If Validating:
1. Run Format Validator
2. Run Consistency Validator
3. Fix issues found

---

## CONTACT & RESOURCES

- **GitHub Repo:** git@github.com:dnd288/acs1_mod_vietnamese.git
- **Upstream (Thai):** git@github.com:GSQStudio/acs1_mod_thailandlanguage.git
- **Game:** Amazing Cultivation Simulator (了不起的修仙模拟器)
- **Platform:** PC & Mobile

---

## SESSION METADATA

- **Planning completed:** 2026-05-03T02:43:48.982Z
- **Total conversation turns:** 50+
- **Files analyzed:** 20+ files
- **Directories scanned:** 15+ directories
- **Documentation created:** 12+ files
- **Planning time:** ~2 hours

---

## NOTES FOR FUTURE SESSIONS

1. **GLOSSARY is blocking** - Cannot start translation without it
2. **Practice/ is most complex** - Needs specialized knowledge
3. **Format preservation is critical** - Many agents failed here in testing
4. **Parallel execution recommended** - Can save 80% time
5. **QC is essential** - Don't skip validation phase

---

## QUICK REFERENCE

### Most Important Files
1. `GLOSSARY.md` - Terminology reference (create first!)
2. `docs/agents/01_GLOSSARY_BUILDER.md` - Start here
3. `docs/agents/03_PRACTICE_SPECIALIST.md` - Most complex module
4. `docs/02_TRANSLATION_PLAN.md` - Detailed plan

### Most Important Rules
1. Preserve format strings: `{0}`, `[NAME]`
2. Preserve color tags: `[color=#...]...[/color]`
3. Use GLOSSARY for all cultivation terms
4. Tab-separated for Dictionary files
5. UTF-8 encoding always

---

## STATUS TRACKING

### Phase 0: Setup
- [ ] Copy Th → Vi
- [ ] Update Info.json
- [ ] Update Config.xml
- [ ] Create viflag.png

### Phase 1: GLOSSARY
- [ ] Create GLOSSARY.md

### Phase 2: Core Translation
- [ ] UIText.xml
- [ ] CodeDictionary.txt
- [ ] MapStoryDictionary.txt

### Phase 3: Module Translation
- [ ] Practice/ (79 files)
- [ ] Npc/ (55 files)
- [ ] ThingDef/ (74 files)
- [ ] Display/ (66 files)
- [ ] World/ (24 files)
- [ ] UI/ (11 files)
- [ ] Comment/ (12 files)
- [ ] System modules (~200 files)
- [ ] SL/ (177 files)

### Phase 4: QC
- [ ] Format validation
- [ ] Consistency validation

### Phase 5: Finalization
- [ ] Git commit
- [ ] Git push
- [ ] Documentation update

---

**Last Updated:** 2026-05-03T02:43:48.982Z  
**Next Update:** After completing each phase
