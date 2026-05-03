# PROJECT OVERVIEW - Vietnamese Translation Mod

**Project:** Vietnamese Language Pack for Amazing Cultivation Simulator  
**Created:** 2026-05-03  
**Status:** Planning Complete - Ready for Execution

---

## EXECUTIVE SUMMARY

This project aims to create a complete Vietnamese translation mod for the game "Amazing Cultivation Simulator" (了不起的修仙模拟器), a Chinese cultivation/xianxia simulation game.

### Key Facts

- **Total Files:** 969 files (~17.3 MB of text)
- **Source Language:** Chinese (Simplified)
- **Target Language:** Vietnamese
- **Reference Languages:** English (official), Thai (template)
- **Estimated Effort:** 155-191 hours (sequential) or 10-12 days (parallel)
- **Complexity:** High (cultivation terminology, nested XML, multiple formats)

---

## PROJECT GOALS

### Primary Goals

1. **Complete Translation:** Translate all 969 files from Chinese to Vietnamese
2. **Quality:** Maintain high translation quality with proper cultivation terminology
3. **Consistency:** Ensure terminology consistency across all files
4. **Format Preservation:** Maintain all XML structures, format strings, and special tags
5. **Usability:** Create a fully functional Vietnamese language pack for the game

### Secondary Goals

1. **Documentation:** Create comprehensive documentation for future maintenance
2. **Glossary:** Build a reusable cultivation terminology glossary (Chinese-Vietnamese-English)
3. **Validation:** Implement quality control processes
4. **Community:** Enable community contributions through clear structure

---

## PROJECT SCOPE

### In Scope

✅ **Translation:**
- All UI text (UIText.xml - 3,583 lines)
- All system messages (CodeDictionary.txt - 4,435 lines)
- All story events (MapStoryDictionary.txt - 1,897 lines)
- All game content in Settings/ (~600 files)
- All dictionary files in SL/ (177 files)

✅ **Metadata:**
- Mod information (Info.json)
- Language configuration (Config.xml)
- Font configuration
- Icon/preview images

✅ **Documentation:**
- Translation glossary
- Agent instructions
- Examples and guidelines

✅ **Quality Control:**
- Format validation
- Consistency checking
- Encoding verification

### Out of Scope

❌ **Not Included:**
- Game code modification
- New features or gameplay changes
- Graphics/art assets (except language flag)
- Audio/voice translation
- Mobile-specific optimizations beyond text

---

## SOURCE MATERIALS

### Available Resources

1. **Chinese Source (Original)**
   - Location: `refs/cn/`
   - Files: 1,748 files
   - Status: Complete, official game data

2. **English Translation (Official)**
   - Location: `refs/en/`
   - Files: 969 files
   - Status: Complete, official translation
   - Use: Reference for understanding meaning

3. **Thai Translation (Community)**
   - Location: `./Language/Th/`
   - Files: 965 files
   - Status: Complete, community mod
   - Use: Template for structure and format

---

## TRANSLATION STRATEGY

### Approach

**Primary:** Chinese → Vietnamese (direct translation)  
**Reference:** English (for understanding context)  
**Template:** Thai (for structure and format)

### Why This Approach?

1. **Accuracy:** Direct translation from source language (Chinese) is most accurate
2. **Cultural Preservation:** Cultivation terms are Chinese cultural concepts
3. **Community Standards:** Vietnamese cultivation novel community has established terminology
4. **Quality:** Avoid "translation of translation" quality loss

### Terminology Strategy

1. **Create GLOSSARY first** - Establish standard terms before translation
2. **Use established conventions** - Follow Vietnamese cultivation novel translations
3. **Maintain consistency** - Same Chinese term = same Vietnamese term always
4. **Preserve cultural context** - Keep Chinese names/concepts where appropriate

---

## TECHNICAL REQUIREMENTS

### File Formats

1. **XML Files** (488 files)
   - Must be well-formed
   - Preserve all attributes
   - Maintain structure

2. **Dictionary Files** (477 files)
   - Tab-separated format (NOT space)
   - Key column (Chinese) unchanged
   - Value column (translation) updated

3. **Text Files** (4 files)
   - UTF-8 encoding
   - Preserve line endings

### Critical Constraints

**MUST Preserve:**
- Format strings: `{0}`, `{1}`, `{1:N0}`, `{0:F2}`
- Placeholders: `[NAME]`, `[PLACE]`, `[IT]`, `[ITS]`
- Color tags: `[color=#D06508]...[/color]`
- Escape sequences: `\n`, `\t`
- XML attributes: `Name="..."`, `sParam="..."`

**MUST NOT:**
- Change XML structure
- Translate attribute values
- Change encoding
- Add/remove tags
- Change Key column in Dictionary files

---

## PROJECT PHASES

### Phase 0: Setup (Manual - 0.5 hour)
- Copy Thai structure to Vietnamese
- Update metadata files
- Create Vietnamese flag icon

### Phase 1: Glossary (Critical - 4-6 hours)
- Extract cultivation terms from source
- Create Chinese-Vietnamese-English glossary
- Validate with community standards

### Phase 2: Core Translation (High Priority - 18-23 hours)
- UIText.xml (3,583 lines)
- CodeDictionary.txt (4,435 lines)
- MapStoryDictionary.txt (1,897 lines)

### Phase 3: Module Translation (Parallel - 100-120 hours)
- Practice/ (79 files) - Cultivation methods ⭐ Most Complex
- Npc/ (55 files) - Characters and races
- ThingDef/ (74 files) - Items and buildings
- Display/ (66 files) - Display names
- World/ (24 files) - World settings
- UI/ (11 files) - UI elements
- Comment/ (12 files) - Tooltips
- System modules (~200 files) - Various systems
- SL/ (177 files) - Dictionary files

### Phase 4: Quality Control (10-13 hours)
- Format validation
- Consistency checking
- Encoding verification
- Terminology validation

### Phase 5: Finalization (1-2 hours)
- Git commit
- Documentation update
- Release preparation

---

## SUCCESS CRITERIA

### Must Have (P0)

✅ All 969 files translated  
✅ All format strings preserved  
✅ All XML files valid  
✅ UTF-8 encoding correct  
✅ GLOSSARY created and followed  
✅ Game loads without errors

### Should Have (P1)

✅ Terminology 100% consistent  
✅ All tooltips/comments translated  
✅ Quality control passed  
✅ Documentation complete

### Nice to Have (P2)

✅ Community review completed  
✅ Example translations provided  
✅ Contribution guidelines created

---

## RISKS & MITIGATION

### High Risk

**Risk:** Inconsistent terminology across files  
**Impact:** Confusing user experience  
**Mitigation:** Create GLOSSARY first, validate consistency

**Risk:** Format string corruption  
**Impact:** Game crashes or display errors  
**Mitigation:** Automated validation, careful review

**Risk:** XML structure damage  
**Impact:** Game fails to load  
**Mitigation:** XML validation, preserve structure

### Medium Risk

**Risk:** Cultural context lost in translation  
**Impact:** Reduced immersion  
**Mitigation:** Use cultivation novel conventions, preserve Chinese names

**Risk:** Encoding issues  
**Impact:** Garbled text display  
**Mitigation:** UTF-8 validation, test in game

### Low Risk

**Risk:** File size increase  
**Impact:** Slightly larger mod size  
**Mitigation:** Acceptable, Vietnamese text is similar length to Thai

---

## TEAM & RESOURCES

### Roles

1. **Coordinator** - Overall project management
2. **Glossary Builder** - Create terminology reference
3. **Translation Specialists** - Domain-specific translation (7-8 agents)
4. **QC Validators** - Quality control (2 agents)

### Tools

- **OpenCode** - Primary development environment
- **Git** - Version control
- **Text Editors** - For manual review
- **XML Validators** - For format checking

---

## TIMELINE

### Sequential Execution
- **Total:** 155-191 hours
- **Calendar:** ~19-24 working days (8h/day)

### Parallel Execution (Recommended)
- **Total:** 10-12 days
- **Agents:** 7-8 running simultaneously
- **Bottleneck:** GLOSSARY (must complete first)

### Milestones

- **Day 1:** GLOSSARY complete
- **Day 2-3:** Core files complete
- **Day 4-10:** Module translation complete
- **Day 11:** QC complete
- **Day 12:** Finalization & release

---

## DELIVERABLES

### Primary Deliverables

1. **Vietnamese Language Pack**
   - Location: `Language/Vi/`
   - Files: 969 translated files
   - Format: Ready for game integration

2. **GLOSSARY.md**
   - Chinese-Vietnamese-English terminology
   - ~200-300 terms
   - Reusable for future projects

3. **Documentation**
   - Project overview
   - Translation guidelines
   - Agent instructions
   - Examples

### Secondary Deliverables

1. **Validation Scripts**
   - Format checker
   - Consistency validator
   - Encoding verifier

2. **Contribution Guidelines**
   - How to contribute
   - Style guide
   - Review process

---

## REFERENCES

- **Game:** Amazing Cultivation Simulator (了不起的修仙模拟器)
- **Developer:** GSQ Games Studio
- **Platform:** PC (Steam) & Mobile
- **Genre:** Simulation, Strategy, Cultivation/Xianxia
- **Original Language:** Chinese (Simplified)
- **Official Languages:** Chinese, English
- **Community Languages:** Thai, (Vietnamese - this project)

---

## NEXT STEPS

1. **Read** `01_SOURCE_ANALYSIS.md` for detailed source structure
2. **Read** `02_TRANSLATION_PLAN.md` for detailed translation plan
3. **Read** `03_AGENT_ARCHITECTURE.md` for agent design
4. **Execute** Phase 0 (Setup)
5. **Execute** `agents/01_GLOSSARY_BUILDER.md` (Critical first step)

---

**Document Version:** 1.0  
**Last Updated:** 2026-05-03T02:44:43.412Z  
**Status:** Complete
