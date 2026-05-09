# Obsidian 配置模板

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
  app.json
  appearance.json
  community-plugins.json
  core-plugins.json
  daily-notes.json
  templates.json
  types.json
  plugins/
  snippets/
```

## 已包含的配置

这个仓库现在不只包含 CSS snippet，也包含一组可复用的 Obsidian 配置：

- 核心插件开关：`.obsidian/core-plugins.json`
- 社区插件启用清单：`.obsidian/community-plugins.json`
- Daily Notes 路径和模板：`.obsidian/daily-notes.json`
- 核心 Templates 插件目录：`.obsidian/templates.json`
- Templater 配置：`.obsidian/plugins/templater-obsidian/data.json`
- Calendar 周记配置：`.obsidian/plugins/calendar/data.json`
- Dataview 配置：`.obsidian/plugins/dataview/data.json`
- Tasks 配置：`.obsidian/plugins/obsidian-tasks-plugin/data.json`
- QuickAdd 基础配置：`.obsidian/plugins/quickadd/data.json`
- Todo 插件基础配置：`.obsidian/plugins/obsidian-plugin-todo/data.json`
- 外观和 CSS snippet 开关：`.obsidian/appearance.json`

没有包含：

- 真实日记正文
- 图片附件
- workspace 布局缓存
- 第三方插件本体代码

第三方插件本体没有放进仓库，是因为公开分发别人的插件代码会涉及许可证、版本和安全问题。使用时先按下面列表安装插件，配置文件会自动接上。

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
