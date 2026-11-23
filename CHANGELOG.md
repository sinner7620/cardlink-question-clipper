# 变更记录

格式参考 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，版本号遵循[语义化版本](https://semver.org/lang/zh-CN/)：skill 正文（`SKILL.md`）的行为变更记 `MINOR`/`MAJOR`，措辞与文档调整记 `PATCH`。当前版本也写在 `SKILL.md` 的 frontmatter `metadata.version` 里，两处需同步。

## [未发布]

## [1.0.0] - 2026-11-23

### 新增

- 首次发布 `cardlink-question-clipper`：agent skill，从教材、习题册、试卷 PDF 或用户提供的文本摘题，在 MarginNote 中生成 CardLink 可匹配的题目卡和答案卡。
- 三种材料结构：题目与答案同一份 PDF（答案作题目卡子卡）、题目与答案两份 PDF（题目册/答案册双分支）、仅提供文本（先排版成 PDF 再走摘录流程）。
- Bridge 任务包规程：`POST /bundles/prepare` 与 `segments` 的用法、按 job/bundle 查询状态、读取 `source.json` 与 `OUTPUT-CONTRACT.md`、批次的续接与替换风险。
- 摘题与配对：`role`/`section` 只作线索、按「章节或题组 + 原书题号」维护题答对照清单、缺答与待确认的标注方式。
- `result.md` 生成规则：只用能出图的 `[block: …]` 锚点、子卡颜色元数据、双册标题「完整章节名 + 原书题号」并按 NFKC 归一化后唯一。
- 提交与核对：`POST /bundles/{bundleId}/submit`、回执警告处理、树形与批量笔记读回、快照 ID 记录。
- 第 6 节「交付用户自行配置 CardLink」：Bridge 只用于摘题/导入/读回，绑定与索引刷新由用户在 MarginNote 内完成。

### 说明

- 正文中的 Bridge 路由与任务包行为来自已有的 v0.93 导入记录，CardLink 匹配行为按 2.4.7 / 2.4.8-b68 源码核对；设备端升级后需重新核对。
- 原书缺答案或对应关系不确定时只导题目卡，答案留空并在交付清单标明。

[1.0.0]: https://github.com/sinner7620/cardlink-question-clipper/releases/tag/v1.0.0
