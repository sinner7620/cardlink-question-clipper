# cardlink-question-clipper

从教材、习题册、试卷 PDF 或用户提供的文本摘题，在 MarginNote 中生成 CardLink 可匹配的题目卡和答案卡。

这是一个 **agent skill**（`SKILL.md` 指令包）：只包含给 Agent 的作业规程，不含可执行代码、不内置任何题库或答案。

当前版本 **1.0.0** · 作者 frank · [变更记录](./CHANGELOG.md) · 许可证 [MIT](./LICENSE)

## 适用场景

- 用户要求「摘题」「制卡」「把配套答案导进 MarginNote」时使用。
- 题目和答案在同一份 PDF、分属两份 PDF，或只提供文本，都按 skill 内的三种默认结构处理。
- 不适用：单独咨询或排查 CardLink 自身的匹配行为。

## 前置条件

- MarginNote 中已安装并启用 **CardLink** 插件。
- Agent 环境中可用的 **MN Bridge** 工具（摘题、导入、读回卡片都通过它完成；skill 只给出规程，连接参数沿用工具自身配置）。
- 待处理的 PDF（或可转成 PDF 的文本）。

## 安装

通用形态是一个目录带一个 `SKILL.md`：`<skills 根>/cardlink-question-clipper/SKILL.md`。各工具扫描的根不同，按它自己的规则放即可。

以下位置是 **DeepSeek Harness** 的（本仓库当前验证过的环境，只作为示例，不代表 skill 只适用于它）：

**项目级**（仅该工作区可见）：把本仓库的 `.agents/skills/cardlink-question-clipper/` 目录复制到项目根，或直接 `git clone` 后把该目录搬到项目的 `.agents/skills/` 下。

**全局**（所有工作区可见）：

```powershell
New-Item -ItemType Directory -Force "$HOME\.dsh\skills\cardlink-question-clipper" | Out-Null
Copy-Item .agents\skills\cardlink-question-clipper\SKILL.md "$HOME\.dsh\skills\cardlink-question-clipper\SKILL.md"
```

在该环境下装好后无需重启：skill 会被扫描进会话目录，改正文保存即生效，改 frontmatter 会触发目录刷新。

## 内容结构

```
.agents/skills/cardlink-question-clipper/SKILL.md
```

skill 正文分六节：确定材料与结构 → 准备 Bridge 任务包 → 摘题并核对对应关系 → 生成 `result.md` → 提交并核对落卡 → 交付用户自行配置 CardLink。

## 版本与兼容性

版本号写在 `SKILL.md` 的 frontmatter `metadata.version` 与 [CHANGELOG.md](./CHANGELOG.md) 中，两者同步维护。

正文中的 Bridge 路由与任务包行为来自已有的 v0.93 导入记录，CardLink 匹配行为按 2.4.7 / 2.4.8-b68 源码核对。设备端版本升级后应重新核对，实际以用户界面与当前工具契约为准。

## 许可证

[MIT](./LICENSE) © 2026 frank
