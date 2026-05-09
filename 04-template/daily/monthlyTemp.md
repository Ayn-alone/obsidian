---
type: Fox
date: <% tp.file.creation_date("YYYY-MM-DD") %>
aliases: []
tags:
  - review/monthly
---
# 月复盘 <% tp.date.now("YYYY-M") %>

## 本月计划

> [!question] 自查问题
> 这个月要设定哪些重点行动？

- [x] 

## 上月回顾

### 上月重点
![[03-daily/month/<% tp.date.now("YYYY-M", "P-1M") %>#本月计划]]

> [!question] 自查问题
> 1. 上月重点完成了吗？
> 2. 完成得怎么样？
> 3. 如果没有完成，这个月需要改变什么？

- 

### 其他反思

> [!question] 自查问题
> 1. 你如何看待自己上月的产出？
> 2. 什么阻碍了你更好地工作？

- 

## 本月心情热力图

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
  dv.paragraph("文件名需要类似：2026-5");
} else {
  const year = Number(match[1]);
  const month = Number(match[2]);
  const days = new Date(year, month, 0).getDate();
  const byDate = new Map();
  for (const page of dv.pages('"03-daily/daily"').where(p => p.mood)) {
    const d = dv.date(page.file.name);
    if (d && d.year === year && d.month === month) byDate.set(page.file.name, page);
  }

  const wrap = dv.el("div", "", { cls: "mood-heatmap-month" });
  wrap.style.display = "grid";
  wrap.style.gridTemplateColumns = "repeat(7, 22px)";
  wrap.style.gap = "5px";

  for (let day = 1; day <= days; day++) {
    const date = `${year}-${String(month).padStart(2, "0")}-${String(day).padStart(2, "0")}`;
    const page = byDate.get(date);
    const mood = page ? (Array.isArray(page.mood) ? String(page.mood[0]).trim() : String(page.mood).trim()) : "";
    const item = moodStyle[mood];
    const cell = page
      ? wrap.createEl("a", {
          href: page.file.path,
          cls: "internal-link",
          attr: { "data-href": page.file.path, title: `${date} ${item.text}` }
        })
      : wrap.createEl("div", { attr: { title: date } });
    cell.style.width = "22px";
    cell.style.height = "22px";
    cell.style.borderRadius = "4px";
    cell.style.backgroundColor = item ? item.color : "var(--background-modifier-border)";
    cell.style.display = "block";
  }
}
```

## 核心原则

![[00-home/我的核心原则]]
