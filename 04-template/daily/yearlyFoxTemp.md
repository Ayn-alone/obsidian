---
type: Fox
date: <% tp.file.creation_date("YYYY-MM-DD") %>
aliases: []
tags:
  - review/Fox
---
> [!summary] 使用方法
> 1. 今年最多写 5 个 Fox。
> 2. 每个 Fox 可以单独创建一个“年度目标”页面。
> 3. 年度目标页面会回链到本年度 Fox 总表。

## 学业 / 工作
- 

## 个人成长
- 

## 生活与关系
- 

## 年度心情热力图

```dataviewjs
const year = Number(dv.current().file.name.match(/(\d{4})$/)?.[1] ?? new Date().getFullYear());
const moodMap = {
  "开心": { color: "happy" },
  "一般": { color: "normal" },
  "不开心": { color: "sad" },
  "重要": { color: "important" },
  "重要的事情记录": { color: "important" }
};

const calendarData = {
  year,
  colors: {
    happy: ["#f8c8dc", "#f5a9c8", "#f17fb0", "#ec5799", "#d93682"],
    normal: ["#cfe3ff", "#acd0ff", "#83b8ff", "#5a9fff", "#347fe0"],
    sad: ["#fff4b0", "#ffeb7a", "#ffe04a", "#ffd21f", "#e6b800"],
    important: ["#e0ccff", "#caa9ff", "#b383ff", "#9a5cff", "#7c3fd1"]
  },
  showCurrentDayBorder: true,
  defaultEntryIntensity: 4,
  intensityScaleStart: 1,
  intensityScaleEnd: 5,
  entries: []
};

for (const page of dv.pages('"03-daily/daily"').where(p => p.mood)) {
  const date = page.file.name;
  if (!date.startsWith(String(year))) continue;
  const mood = Array.isArray(page.mood) ? String(page.mood[0]).trim() : String(page.mood).trim();
  const item = moodMap[mood];
  if (!item) continue;
  calendarData.entries.push({
    date,
    color: item.color,
    intensity: 5,
    content: await dv.span(`[[${page.file.path}|${date}]]`)
  });
}

renderHeatmapCalendar(this.container, calendarData);
```
