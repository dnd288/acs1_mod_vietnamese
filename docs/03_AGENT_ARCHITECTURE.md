# AGENT ARCHITECTURE - Multi-Agent System Design

**Document:** Agent Architecture  
**Created:** 2026-05-03  
**Purpose:** Design and specification of the multi-agent translation system

---

## ARCHITECTURE OVERVIEW

### System Type: Hierarchical Multi-Agent System

```
                    ┌─────────────────┐
                    │  COORDINATOR    │
                    │     AGENT       │
                    └────────┬────────┘
                             │
            ┌────────────────┼────────────────┐
            │                │                │
      ┌─────▼─────┐    ┌────▼────┐    ┌─────▼─────┐
      │ GLOSSARY  │    │ TRANS-  │    │    QC     │
      │  BUILDER  │    │ LATION  │    │  MANAGER  │
      │           │    │ MANAGER │    │           │
      └───────────┘    └────┬────┘    └───────────┘
                            │
                ┌───────────┼───────────┐
                │           │           │
          ┌─────▼─────┐ ┌──▼──┐  ┌────▼────┐
          │ SPECIALIST│ │CORE │  │SPECIALIST│
          │  AGENTS   │ │AGENT│  │  AGENTS  │
          │  (Group)  │ │     │  │  (Group) │
          └───────────┘ └─────┘  └──────────┘
```

### Design Principles

1. **Separation of Concerns:** Each agent has a specific domain
2. **Hierarchical Control:** Coordinator manages workflow
3. **Parallel Execution:** Specialists can run simultaneously
4. **Dependency Management:** GLOSSARY blocks translation, translation blocks QC
5. **Task-Based:** Agents receive detailed markdown instructions

---

## AGENT TYPES

### Total Agents: 14-15

| Type | Count | Purpose |
|------|-------|---------|
| Coordinator | 1 | Project management |
| Glossary Builder | 1 | Create terminology reference |
| Translation Manager | 1 | Manage translation workflow |
| Core Translation | 1 | Translate 3 critical files |
| Specialist Agents | 7-8 | Domain-specific translation |
| QC Manager | 1 | Manage quality control |
| QC Validators | 2 | Format & consistency validation |

---

## AGENT SPECIFICATIONS

### 1. COORDINATOR AGENT

**Role:** Overall project orchestration

**Responsibilities:**
- Initialize project structure
- Assign tasks to agents
- Track progress across all phases
- Handle dependencies between phases
- Generate status reports
- Coordinate issue resolution

**Input:**
- Project plan (this documentation)
- File structure
- Agent availability

**Output:**
- Task assignments
- Progress reports
- Issue logs
- Final summary

**Tools Required:**
- File system access (read-only for scanning)
- Task queue management
- Progress tracking

**Instruction File:** `docs/agents/00_COORDINATOR.md`

**Estimated Time:** 5 hours (overhead across project)

---

### 2. GLOSSARY BUILDER AGENT

**Role:** Create comprehensive cultivation terminology glossary

**Responsibilities:**
- Scan Chinese source files for cultivation terms
- Extract high-frequency terms
- Research Vietnamese cultivation novel conventions
- Create Chinese-Vietnamese-English mappings
- Validate with community standards
- Generate GLOSSARY.md

**Input:**
- Chinese source: `refs/cn/Practice/`
- Chinese source: `refs/cn/Npc/`
- English reference: `refs/en/`
- Vietnamese cultivation novel terminology (research)

**Output:**
- `GLOSSARY.md` (200-300 terms)
- `TERM_FREQUENCY.json` (optional - term usage statistics)

**Skills Required:**
- Understanding of xianxia/cultivation concepts
- Chinese language knowledge
- Vietnamese language knowledge
- Research skills

**Priority:** **P0 - BLOCKING** (must complete before translation)

**Instruction File:** `docs/agents/01_GLOSSARY_BUILDER.md`

**Estimated Time:** 4-6 hours

---

### 3. TRANSLATION MANAGER AGENT

**Role:** Coordinate translation workflow

**Responsibilities:**
- Receive task assignments from Coordinator
- Distribute tasks to Specialist Agents
- Ensure GLOSSARY is used consistently
- Collect results from Specialist Agents
- Handle retries on failures
- Report progress to Coordinator

**Input:**
- Task queue from Coordinator
- GLOSSARY.md
- File mappings (Chinese → English → Thai → Vietnamese)

**Output:**
- Translated files
- Translation logs
- Error reports
- Progress updates

**Tools Required:**
- Task distribution system
- Result aggregation
- Error handling

**Priority:** P1

**Estimated Time:** 3 hours (overhead)

---

### 4. CORE TRANSLATION AGENT

**Role:** Translate 3 most critical files

**Responsibilities:**
- Translate UIText.xml (3,583 lines)
- Translate CodeDictionary.txt (4,435 lines)
- Translate MapStoryDictionary.txt (1,897 lines)
- Preserve all format strings and special tags
- Use GLOSSARY for terminology
- Validate output format

**Input:**
- English: `refs/en/UIText.xml`
- English: `refs/en/CodeDictionary.txt`
- English: `refs/en/MapStoryDictionary.txt`
- Template: `Language/Vi/UIText.xml`
- Template: `Language/Vi/CodeDictionary.txt`
- Template: `Language/Vi/MapStoryDictionary.txt`
- GLOSSARY.md

**Output:**
- `Language/Vi/UIText.xml` (translated)
- `Language/Vi/CodeDictionary.txt` (translated)
- `Language/Vi/MapStoryDictionary.txt` (translated)

**Skills Required:**
- UI/UX terminology
- Game mechanics understanding
- Format string handling
- XML processing
- Dictionary format handling

**Priority:** P1

**Instruction File:** `docs/agents/02_CORE_TRANSLATION.md`

**Estimated Time:** 18-23 hours

---

### 5. SPECIALIST AGENTS (7-8 agents)

#### 5.1 PRACTICE SPECIALIST AGENT ⭐

**Role:** Translate cultivation methods and techniques

**Domain:** Practice/ module (79 files)

**Responsibilities:**
- Translate all cultivation method files
- Handle nested XML structures
- Use GLOSSARY for all cultivation terms
- Maintain cultural context
- Preserve format strings and color tags

**Input:**
- Chinese: `refs/cn/Practice/`
- English: `refs/en/Settings/Practice/`
- Template: `Language/Vi/Settings/Practice/`
- GLOSSARY.md

**Output:**
- `Language/Vi/Settings/Practice/` (79 files translated)

**Skills Required:**
- **Deep understanding of xianxia/cultivation concepts** (CRITICAL)
- Nested XML processing
- Context-aware translation
- GLOSSARY adherence
- Cultural sensitivity

**Priority:** P2-High (Most complex module)

**Instruction File:** `docs/agents/03_PRACTICE_SPECIALIST.md`

**Estimated Time:** 20-25 hours

---

#### 5.2 NPC SPECIALIST AGENT

**Role:** Translate NPC-related content

**Domain:** Npc/ module (55 files)

**Responsibilities:**
- Translate character races, features, moods
- Translate backstories and relationships
- Handle character terminology
- Preserve XML structure

**Input:**
- Chinese: `refs/cn/Npc/`
- English: `refs/en/Settings/Npc/`
- Template: `Language/Vi/Settings/Npc/`
- GLOSSARY.md

**Output:**
- `Language/Vi/Settings/Npc/` (55 files translated)

**Skills Required:**
- Character terminology
- Personality/mood translation
- Relationship terms
- XML processing

**Priority:** P2

**Instruction File:** `docs/agents/04_NPC_SPECIALIST.md`

**Estimated Time:** 10-12 hours

---

#### 5.3 ITEM SPECIALIST AGENT

**Role:** Translate items, buildings, plants

**Domain:** ThingDef/ module (74 files)

**Responsibilities:**
- Translate item names and descriptions
- Translate building names and descriptions
- Translate plant and material names
- Preserve XML structure

**Input:**
- Chinese: `refs/cn/ThingDef/`
- English: `refs/en/Settings/ThingDef/`
- Template: `Language/Vi/Settings/ThingDef/`
- GLOSSARY.md

**Output:**
- `Language/Vi/Settings/ThingDef/` (74 files translated)

**Skills Required:**
- Item terminology
- Material/resource terms
- Building/architecture terms
- XML processing

**Priority:** P2

**Instruction File:** `docs/agents/05_ITEM_SPECIALIST.md`

**Estimated Time:** 12-15 hours

---

#### 5.4 WORLD SPECIALIST AGENT

**Role:** Translate world, display, and story content

**Domain:** World/, Display/, MapStories/ modules (115 files)

**Responsibilities:**
- Translate world settings and biomes
- Translate display names and titles
- Translate map story events
- Handle narrative text

**Input:**
- Chinese: `refs/cn/World/`
- Chinese: `refs/cn/Display/`
- Chinese: `refs/cn/MapStories/`
- English references
- Templates
- GLOSSARY.md

**Output:**
- `Language/Vi/Settings/World/` (24 files)
- `Language/Vi/Settings/Display/` (66 files)
- `Language/Vi/Settings/MapStories/` (25 files)

**Skills Required:**
- Geographic terminology
- Narrative translation
- Name generation understanding
- Story context

**Priority:** P2

**Instruction File:** `docs/agents/06_WORLD_SPECIALIST.md`

**Estimated Time:** 17-21 hours

---

#### 5.5 UI SPECIALIST AGENT

**Role:** Translate UI and comment files

**Domain:** Ui/, Comment/ modules (23 files)

**Responsibilities:**
- Translate UI element text
- Translate tooltips and help text
- Ensure concise, clear language
- Preserve format for UI constraints

**Input:**
- Chinese: `refs/cn/Ui/`
- Chinese: `refs/cn/Comment/`
- English references
- Templates
- GLOSSARY.md

**Output:**
- `Language/Vi/Settings/Ui/` (11 files)
- `Language/Vi/Settings/Comment/` (12 files)

**Skills Required:**
- UI/UX terminology
- Concise writing
- Tooltip best practices
- XML processing

**Priority:** P1

**Instruction File:** `docs/agents/07_UI_SPECIALIST.md`

**Estimated Time:** 4-6 hours

---

#### 5.6 SYSTEM SPECIALIST AGENT

**Role:** Translate all remaining Settings/ modules

**Domain:** ~200 files across 23+ modules

**Responsibilities:**
- Translate all remaining system modules
- Handle diverse content types
- Maintain consistency with GLOSSARY
- Preserve all formats

**Input:**
- Chinese: `refs/cn/[various]/`
- English references
- Templates
- GLOSSARY.md

**Output:**
- All remaining Settings/ files translated

**Modules:**
- Jianghu/ (13 files)
- Esoterica/ (13 files)
- Modifiers/ (37 files)
- Trade/ (36 files)
- Zhen/ (13 files)
- LingShou/ (15 files)
- Mutation/ (10 files)
- NpcStories/ (8 files)
- NpcBiography/ (2 files)
- RPG/ (24 files)
- Property/ (7 files)
- + 23 more small modules

**Skills Required:**
- General translation
- Diverse terminology
- XML/Dictionary processing
- Consistency maintenance

**Priority:** P3

**Instruction File:** `docs/agents/08_SYSTEM_SPECIALIST.md`

**Estimated Time:** 47 hours

---

#### 5.7 DICTIONARY SPECIALIST AGENTS (2-3 agents)

**Role:** Translate SL/ dictionary files

**Domain:** SL/ folder (177 files)

**Responsibilities:**
- Translate FightMap dictionaries (61 folders)
- Translate TeachFile dictionaries (43 folders)
- Translate RPG Maps dictionaries (35 folders)
- Translate TeachSave dictionary (1 file)
- Preserve dictionary format (tab-separated)

**Input:**
- English: `refs/en/SL/`
- Templates: `Language/Vi/SL/`
- GLOSSARY.md

**Output:**
- `Language/Vi/SL/` (177 files translated)

**Skills Required:**
- Dictionary format handling
- Batch processing
- Location name translation
- Tutorial text translation

**Priority:** P4

**Instruction File:** `docs/agents/09_DICTIONARY_SPECIALIST.md`

**Estimated Time:** 26-33 hours (split among 2-3 agents)

---

### 6. QC MANAGER AGENT

**Role:** Coordinate quality control process

**Responsibilities:**
- Assign validation tasks to QC Validators
- Aggregate validation results
- Generate QC reports
- Coordinate fixes with Translation Manager
- Track issue resolution

**Input:**
- All translated files
- GLOSSARY.md
- Validation rules

**Output:**
- QC Report (comprehensive)
- Issue list (prioritized)
- Fix recommendations

**Priority:** P5

**Estimated Time:** 2 hours (overhead)

---

### 7. QC VALIDATOR AGENTS (2 agents)

#### 7.1 FORMAT VALIDATOR AGENT

**Role:** Validate file formats and structure

**Responsibilities:**
- Validate XML well-formedness
- Check Dictionary format (tab-separated)
- Verify UTF-8 encoding
- Check format string preservation
- Check color tag preservation
- Check escape sequence preservation

**Input:**
- All translated files in `Language/Vi/`

**Output:**
- Format validation report
- List of format errors
- Suggested fixes

**Tools:**
- XML parser
- Regex validators
- Encoding checker
- Custom validation scripts

**Priority:** P5

**Instruction File:** `docs/agents/10_FORMAT_VALIDATOR.md`

**Estimated Time:** 4-5 hours

---

#### 7.2 CONSISTENCY VALIDATOR AGENT

**Role:** Validate terminology consistency

**Responsibilities:**
- Check terminology against GLOSSARY
- Scan for inconsistent translations
- Verify context appropriateness
- Check completeness
- Generate consistency report

**Input:**
- All translated files in `Language/Vi/`
- GLOSSARY.md

**Output:**
- Consistency validation report
- List of inconsistencies
- Suggested corrections

**Tools:**
- Text analysis
- GLOSSARY lookup
- Pattern matching
- Custom validation scripts

**Priority:** P5

**Instruction File:** `docs/agents/11_CONSISTENCY_VALIDATOR.md`

**Estimated Time:** 6-8 hours

---

## AGENT COMMUNICATION

### Task Assignment Flow

```
1. Coordinator → Translation Manager: "Translate Practice/ module"
2. Translation Manager → Practice Specialist: "Translate 79 files in Practice/"
3. Practice Specialist → Translation Manager: "Completed 79 files"
4. Translation Manager → Coordinator: "Practice/ module complete"
```

### Dependency Flow

```
Phase 0 (Setup)
    ↓
Phase 1 (GLOSSARY Builder) ← BLOCKING
    ↓
Phase 2 (Core Translation) ← BLOCKING for Phase 3
    ↓
Phase 3 (Specialist Agents) ← Can run in parallel
    ↓
Phase 4 (QC Validators) ← BLOCKING
    ↓
Phase 5 (Finalization)
```

---

## AGENT CONFIGURATION

### Configuration Template (YAML)

```yaml
agent:
  name: "practice_specialist"
  role: "Practice Module Translation Specialist"
  type: "specialist"
  domain: "Cultivation methods, realms, techniques"
  
  input:
    chinese_source: "refs/cn/Practice/"
    english_reference: "refs/en/Settings/Practice/"
    thai_template: "./Language/Vi/Settings/Practice/"
    glossary: "GLOSSARY.md"
  
  output:
    target: "./Language/Vi/Settings/Practice/"
  
  statistics:
    file_count: 79
    estimated_hours: "20-25"
  
  skills:
    - "Cultivation terminology expertise"
    - "Nested XML processing"
    - "Context-aware translation"
    - "GLOSSARY adherence"
  
  rules:
    - "MUST use GLOSSARY for all cultivation terms"
    - "MUST preserve XML structure and attributes"
    - "MUST preserve format strings: {0}, {1:N0}, [NAME], etc."
    - "MUST preserve color tags: [color=#...]...[/color]"
    - "MUST preserve escape sequences: \\n"
  
  validation:
    - "All XML files are well-formed"
    - "All cultivation terms match GLOSSARY"
    - "All format strings preserved"
    - "All color tags preserved"
    - "UTF-8 encoding correct"
  
  priority: "P2-High"
  
  dependencies:
    - "glossary_builder (must complete first)"
    - "core_translation (recommended)"
```

---

## EXECUTION STRATEGY

### Sequential Execution (Not Recommended)

**Timeline:** 19-24 days

```
Day 1: GLOSSARY
Day 2-3: Core Translation
Day 4-6: Practice Specialist
Day 7-8: NPC Specialist
Day 9-10: Item Specialist
Day 11-13: World Specialist
Day 14: UI Specialist
Day 15-21: System Specialist
Day 22-24: Dictionary Specialists
Day 25: QC
Day 26: Finalization
```

### Parallel Execution (Recommended)

**Timeline:** 10-12 days

```
Day 1:
  - GLOSSARY Builder (4-6h) [BLOCKING]

Day 2-3:
  - Core Translation (18-23h) [BLOCKING for Phase 3]

Day 4-10:
  [All running in parallel]
  - Practice Specialist (20-25h)
  - NPC Specialist (10-12h)
  - Item Specialist (12-15h)
  - World Specialist (17-21h)
  - UI Specialist (4-6h)
  - System Specialist (47h)
  - Dictionary Specialists x3 (9-11h each)

Day 11:
  [Running in parallel]
  - Format Validator (4-5h)
  - Consistency Validator (6-8h)

Day 12:
  - Fixes & Finalization (4-6h)
```

---

## AGENT SUMMARY TABLE

| Agent | Type | Files | Hours | Priority | Blocking |
|-------|------|-------|-------|----------|----------|
| Coordinator | Management | - | 5 | P0 | No |
| Glossary Builder | Builder | - | 4-6 | P0 | Yes |
| Translation Manager | Management | - | 3 | P1 | No |
| Core Translation | Translator | 3 | 18-23 | P1 | Yes |
| Practice Specialist | Specialist | 79 | 20-25 | P2-High | No |
| NPC Specialist | Specialist | 55 | 10-12 | P2 | No |
| Item Specialist | Specialist | 74 | 12-15 | P2 | No |
| World Specialist | Specialist | 115 | 17-21 | P2 | No |
| UI Specialist | Specialist | 23 | 4-6 | P1 | No |
| System Specialist | Specialist | ~200 | 47 | P3 | No |
| Dictionary Specialists | Specialist | 177 | 26-33 | P4 | No |
| QC Manager | Management | - | 2 | P5 | No |
| Format Validator | Validator | 969 | 4-5 | P5 | No |
| Consistency Validator | Validator | 969 | 6-8 | P5 | No |
| **TOTAL** | | **969** | **178-213** | | |

---

## NEXT STEPS

1. **Read** `04_WORKFLOW.md` for detailed workflow
2. **Read** agent instruction files in `docs/agents/`
3. **Execute** Phase 0 (Setup)
4. **Execute** Phase 1 (GLOSSARY) - Start here!

---

**Document Version:** 1.0  
**Last Updated:** 2026-05-03T02:48:40.052Z  
**Status:** Complete
