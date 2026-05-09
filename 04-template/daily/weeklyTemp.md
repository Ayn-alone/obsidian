---
type: Fox
date: <% tp.file.creation_date("YYYY-MM-DD") %>
aliases: []
tags:
  - review/weekly
---
# 周复盘 <% tp.date.now("YYYY-ww") %>

## 本周计划

> [!question] 自查问题
> 1. 如果本周只能完成 5 件具体事情，会是哪 5 件？
> 2. 它们如何对应本月重点和年度 Fox？

- [x] 

## 周末检查清单
- [x] 清空 Inbox
- [x] 整理生活事务

## 本月重点
![[03-daily/month/<% tp.date.now("YYYY-M") %>#本月计划]]

> [!attention] 本周复盘时请注意
> 回顾本周时，重点看本周行动是否服务于本月重点和年度 Fox。

## 上周回顾
![[03-daily/week/Weekly Review <% tp.date.now("YYYY-w", -7) %>#本周计划]]

> [!question] 自查问题
> 1. 上周目标是什么？完成了吗？
> 2. 有哪些没完成？原因是什么？
> 3. 为了推进本月重点，本周要调整什么？

- 

## 本周心情热力图

```dataviewjs
const moodStyle = {
  "开心": { color: "#ec5799", text: "开心" },
  "一般": { color: "#5a9fff", text: "一般" },
  "不开心": { color: "#ffd21f", text: "不开心" },
  "重要": { color: "#9a5cff", text: "重要" },
  "重要的事情记录": { color: "#9a5cff", text: "重要" }
};

const match = dv.current().file.name.match(/(\d{4})-(\d{1,2})$/);
if (!match) {
  dv.paragraph("文件名需要类似：Weekly Review 2026-19");
} else {
  const year = Number(match[1]);
  const week = Number(match[2]);
  const pages = dv.pages('"03-daily/daily"')
    .where(p => p.mood)
    .where(p => {
      const d = dv.date(p.file.name);
      return d && d.weekYear === year && d.weekNumber === week;
    })
    .sort(p => p.file.name, "asc");

  const wrap = dv.el("div", "", { cls: "mood-heatmap-week" });
  wrap.style.display = "grid";
  wrap.style.gridTemplateColumns = "repeat(7, 28px)";
  wrap.style.gap = "6px";

  for (const page of pages) {
    const mood = Array.isArray(page.mood) ? String(page.mood[0]).trim() : String(page.mood).trim();
    const item = moodStyle[mood];
    if (!item) continue;
    const cell = wrap.createEl("a", {
      href: page.file.path,
      cls: "internal-link",
      attr: { "data-href": page.file.path, title: `${page.file.name} ${item.text}` }
    });
    cell.style.width = "28px";
    cell.style.height = "28px";
    cell.style.borderRadius = "4px";
    cell.style.backgroundColor = item.color;
    cell.style.display = "block";
  }
}
```
