# PR TEMPLATE - Vietnamese Translation Mod

Copy template này khi tạo PR bằng `gh pr create`.

---

## Format: feat(vi): [Phase X] Translate [Module]

---

## PR Body Template

```markdown
## Tóm tắt
[Mô tả ngắn gọn những gì đã dịch trong PR này]

## Phase
- Phase: [Phase X - tên phase]
- Branch: `translation/phase-Xa-module-name`
- Agent: [tên agent đã dịch]

## Files thay đổi
- Module: [tên module]
- Files: [số lượng] files
- Lines translated: ~[ước tính] lines

### Danh sách thư mục:
- `Language/Vi/Settings/[Module]/` - [mô tả]

## Translation Notes
- Source: refs/cn/ (Chinese) + refs/en/ (English reference)
- GLOSSARY: Applied (GLOSSARY.md)
- [Ghi chú thêm nếu có, ví dụ: thuật ngữ đặc biệt, quyết định dịch...]

## Self-Review Checklist
- [ ] Format strings preserved: `{0}`, `{1}`, `{1:N0}`, `{0:F2}`
- [ ] Placeholders preserved: `[NAME]`, `[PLACE]`, `[IT]`, `[ITS]`
- [ ] Color tags preserved: `[color=#RRGGBB]...[/color]`
- [ ] Escape sequences preserved: `\n`, `\t`
- [ ] XML attributes unchanged: `Name=`, `sParam=`, `mz=`
- [ ] XML files well-formed (no parse errors)
- [ ] Dictionary files TAB-separated (not space)
- [ ] UTF-8 encoding
- [ ] All cultivation terms from GLOSSARY.md
- [ ] No Thai text remaining
- [ ] No untranslated Chinese (except dictionary keys)

## Reviewer Notes
[Bất kỳ điểm nào cần reviewer chú ý đặc biệt]
```

---

## Ví dụ thực tế

```bash
gh pr create \
  --title "feat(vi): Phase 1 - Create GLOSSARY.md (200+ cultivation terms)" \
  --body "## Tóm tắt
Tạo GLOSSARY.md với 247 thuật ngữ tu tiên Trung-Việt-Anh.

## Phase
- Phase: Phase 1 - GLOSSARY Builder
- Branch: \`translation/phase-1-glossary\`
- Agent: GLOSSARY Builder

## Files thay đổi
- Module: GLOSSARY
- Files: 1 file
- Lines: 247 terms

## Translation Notes
- Source: refs/cn/Practice/, refs/cn/Npc/
- Coverage: Realms, Basic Terms, Elements, Items, Characters, Locations

## Self-Review Checklist
- [x] 200+ terms included
- [x] Realm names capitalized
- [x] Common terms lowercase
- [x] Table format correct
- [x] No duplicates" \
  --base master \
  --label "translation,phase-1"
```

---

## Branch Naming Convention

```
translation/phase-[X][a-z]-[module-name]

Examples:
  translation/phase-1-glossary
  translation/phase-2-core
  translation/phase-3a-practice
  translation/phase-3b-npc-items
  translation/phase-3c-world-ui
  translation/phase-3d-system
  translation/phase-3e-sl-dict
  translation/phase-4-qc-fixes
```

---

## Commit Message Convention

```
feat(vi): [Phase X] [Action] [Subject]

[Body - bullet points mô tả chi tiết]

- Translated: [mô tả]
- Files: X files changed
- Source: refs/cn/ + refs/en/
- GLOSSARY: applied
```

Examples:
```
feat(vi): Phase 1 Create GLOSSARY with 247 cultivation terms

- Added 247 Chinese-Vietnamese-English term mappings
- Coverage: realms, techniques, items, characters, locations
- Source: refs/cn/Practice/, refs/cn/Npc/
- Template: docs/GLOSSARY_TEMPLATE.md
```

```
feat(vi): Phase 3a Translate Practice module (79 files)

- Translated all cultivation method files in Settings/Practice/
- Gong/: 19 files - core cultivation techniques
- Magic/, Spell/, Tree/: supporting files
- Files: 79 files changed
- GLOSSARY: all cultivation terms applied
```
