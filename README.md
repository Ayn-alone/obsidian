# obsidian-life-template

这是一个 Obsidian「记录生活」模板包，包含每日记录、心情热力图、周复盘、月复盘和年度 Fox 模板。

## 目录结构

```text
00-home/
03-daily/
  daily/
  week/
  month/
  year/
  assets/
04-template/
  daily/
.obsidian/
  snippets/
```

## 需要安装的插件

- Calendar
- Daily Notes（Obsidian 核心插件）
- Templater
- Dataview
- Heatmap Calendar

可选：

- Tasks
- QuickAdd

## Daily Notes 设置

在 Obsidian 设置里配置：

```text
New file location: 03-daily/daily
Template file location: 04-template/daily/dailyTemp.md
```

## Templater 设置

```text
Template folder location: 04-template
```

创建周复盘、月复盘、年度模板时建议使用：

```text
Templater: Create new note from template
```

## 心情字段

每日笔记 frontmatter 中使用：

```yaml
mood: 一般
```

支持值：

- 开心
- 一般
- 不开心
- 重要

颜色映射：

- 开心：粉色
- 一般：蓝色
- 不开心：黄色
- 重要：紫色

## 文件命名约定

每日笔记：

```text
03-daily/daily/YYYY-MM-DD.md
```

周复盘：

```text
03-daily/week/Weekly Review YYYY-W.md
```

月复盘：

```text
03-daily/month/YYYY-M.md
```

年度 Fox：

```text
03-daily/year/Yearly Fox YYYY.md
```

## CSS snippet

复制后在 Obsidian 中打开：

```text
设置 -> 外观 -> CSS 代码片段 -> heatmap-calendar-fix
```

这个 CSS 用于：

- 修复 Heatmap Calendar 色块高度
- 隐藏热力图色块文字但保留点击区域
- 隐藏嵌入文件的标题

## 说明

这个仓库只包含模板和样式，不包含私人日记正文、图片、workspace 布局缓存或个人主页。
