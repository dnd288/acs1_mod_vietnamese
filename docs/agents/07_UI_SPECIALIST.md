# AGENT INSTRUCTION: UI SPECIALIST

**Agent Name:** UI Specialist  
**Agent ID:** 07_UI_SPECIALIST  
**Priority:** P1  
**Estimated Time:** 4-6 hours

---

## OBJECTIVE

Translate UI elements and comment/tooltip files (23 files total):
- Ui/ (11 files) - UI element definitions
- Comment/ (12 files) - Tooltips and help text

---

## PREREQUISITES

### Required
- ✅ GLOSSARY.md exists
- ✅ Phase 0 complete

### Input Sources

**Chinese Source:**
```
refs/cn/Ui/
refs/cn/Comment/
```

**English Reference:**
```
refs/en/Settings/Ui/
refs/en/Settings/Comment/
```

**Vietnamese Template:**
```
Language/Vi/Settings/Ui/
Language/Vi/Settings/Comment/
```

---

## OUTPUT

**Target:** 
- `Language/Vi/Settings/Ui/` (11 files)
- `Language/Vi/Settings/Comment/` (12 files)

---

## KEY PRINCIPLES

### UI Text Guidelines

1. **Concise** - UI space is limited
2. **Clear** - Users must understand immediately
3. **Consistent** - Same terms across all UI
4. **Action-oriented** - Use verbs for buttons

### Tooltip Guidelines

1. **Informative** - Explain clearly
2. **Helpful** - Guide users
3. **Complete** - Don't leave out details
4. **Formatted** - Preserve color tags for emphasis

---

## TRANSLATION PROCESS

### Comment Files (Tooltips)

**Format:**
```xml
<Texts Type="Other">
    <List>
        <Text Name="MainUIWorldTime">
            <Notes>关于世界时钟的注释</Notes>
            <Title>世界时钟</Title>
            <Desc>世界时间会随着游戏进度增加</Desc>
            <Tips>右键打开[color=#D06508]世界时钟[/color]注释页面</Tips>
        </Text>
    </List>
</Texts>
```

**Translation:**
```xml
<Texts Type="Other">
    <List>
        <Text Name="MainUIWorldTime">
            <Notes>Chú thích về đồng hồ thế giới</Notes>
            <Title>Đồng hồ thế giới</Title>
            <Desc>Thời gian thế giới sẽ tăng theo tiến trình game</Desc>
            <Tips>Nhấp chuột phải để mở chú thích về [color=#D06508]Đồng hồ thế giới[/color]</Tips>
        </Text>
    </List>
</Texts>
```

---

## COMMON UI TERMS

### Buttons & Actions

| Chinese | Vietnamese | English |
|---------|------------|---------|
| 确认 | Xác nhận | Confirm |
| 取消 | Hủy | Cancel |
| 关闭 | Đóng | Close |
| 保存 | Lưu | Save |
| 删除 | Xóa | Delete |
| 返回 | Quay lại | Return |
| 继续 | Tiếp tục | Continue |
| 开始 | Bắt đầu | Start |
| 结束 | Kết thúc | End |

### UI Elements

| Chinese | Vietnamese | English |
|---------|------------|---------|
| 菜单 | Menu | Menu |
| 设置 | Cài đặt | Settings |
| 选项 | Tùy chọn | Options |
| 帮助 | Trợ giúp | Help |
| 提示 | Gợi ý | Hint/Tip |
| 窗口 | Cửa sổ | Window |
| 按钮 | Nút | Button |

---

## RULES & CONSTRAINTS

### MUST DO

✅ **Keep text concise** - UI space limited  
✅ **Use GLOSSARY for cultivation terms**  
✅ **Preserve XML structure and attributes**  
✅ **Preserve color tags in tooltips**  
✅ **Preserve format strings**  
✅ **Use clear, simple Vietnamese**  
✅ **Maintain consistency with UIText.xml**  

### MUST NOT DO

❌ **Do NOT make text too long** - Will overflow UI  
❌ **Do NOT translate Name attributes**  
❌ **Do NOT remove color tags**  
❌ **Do NOT use overly formal language**  

---

## VALIDATION CHECKLIST

- [ ] Ui/ (11 files) translated
- [ ] Comment/ (12 files) translated
- [ ] All 23 files complete
- [ ] Text length appropriate for UI
- [ ] All color tags preserved
- [ ] All format strings preserved
- [ ] Terminology consistent with UIText.xml
- [ ] XML well-formed
- [ ] UTF-8 encoding

---

## SUCCESS CRITERIA

1. ✅ All 23 files completely translated
2. ✅ UI text concise and clear
3. ✅ Tooltips informative and helpful
4. ✅ All XML structures preserved
5. ✅ Consistent with core UI translation

---

## TIPS

1. **Check UIText.xml first** - Ensure consistency
2. **Test text length** - Imagine it in UI
3. **Color tags highlight important info** - Preserve them
4. **Tooltips explain mechanics** - Be thorough but clear

---

## ESTIMATED BREAKDOWN

| Module | Files | Hours |
|--------|-------|-------|
| Ui/ | 11 | 2-3h |
| Comment/ | 12 | 2-3h |
| **TOTAL** | **23** | **4-6h** |

---

**Agent Status:** Ready to execute  
**Prerequisites:** GLOSSARY.md must exist  
**Created:** 2026-05-03  
**Version:** 1.0
