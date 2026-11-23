# cardlink-question-clipper

从教材、习题册、试卷 PDF 或文本摘题，在 MarginNote 中生成 CardLink 可匹配的题目卡和答案卡。

前提：MarginNote 已启用 CardLink 插件，Agent 可调用 MN Bridge。

**版本** 1.0.0 · [变更记录](./CHANGELOG.md) · [MIT](./LICENSE)

## 安装

复制 `.agents/skills/cardlink-question-clipper/` 到所用工具的 skills 根。以 DeepSeek Harness 的全局位置为例：

```powershell
git clone https://github.com/sinner7620/cardlink-question-clipper
New-Item -ItemType Directory -Force "$HOME\.dsh\skills" | Out-Null
Copy-Item .\cardlink-question-clipper\.agents\skills\cardlink-question-clipper "$HOME\.dsh\skills\" -Recurse
```

`.dsh\skills` 换成其它工具的 skills 根同样可用。

## 内容

单一文件 `SKILL.md`，六节：结构选择 → 任务包准备 → 摘题与配对 → 生成 `result.md` → 提交核对 → 交付后的 CardLink 配置。
