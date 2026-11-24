# cardlink-question-clipper

从教材、习题册、试卷 PDF 或文本摘题，在 MarginNote 中生成 CardLink 可匹配的题目卡和答案卡。

**版本** 1.0.1 · [下载发布包][release] · [变更记录](./CHANGELOG.md) · [MIT](./LICENSE)

## 使用前提

- 在 MarginNote 中安装并启用 CardLink。
- 在所用 Agent 中配置 MN Bridge。开始前确认当前会话的工具列表中有 MN Bridge，并且能读取目标学习集。安装 skill 只添加摘题流程，Bridge 需要另外接入。
- 跨文件双册的导入、续批和截图裁切取决于当前 Bridge 能力。续批无法安全接回原分支时，保留已导入的卡并暂停写入。

## 安装与更新

从[发布页][release]下载并解压源码包，或用下列命令获取固定版本：

```powershell
git clone --branch v1.0.1 --depth 1 https://github.com/sinner7620/cardlink-question-clipper.git
cd cardlink-question-clipper
```

在解压后的仓库根目录或克隆目录中执行以下 PowerShell 命令。下面以 DeepSeek Harness 的全局安装为例。同一组命令也用于更新，从新版源码目录执行即可覆盖旧文件。

```powershell
$skillDir = Join-Path $HOME '.dsh/skills/cardlink-question-clipper'
New-Item -ItemType Directory -Path $skillDir -Force -ErrorAction Stop | Out-Null
Copy-Item -LiteralPath '.agents/skills/cardlink-question-clipper/SKILL.md' -Destination (Join-Path $skillDir 'SKILL.md') -Force -ErrorAction Stop
```

项目级安装时，把目标目录换成目标项目下的 `.agents/skills/cardlink-question-clipper`。其他 Agent 使用各自文档指定的 skills 目录，并保留 `cardlink-question-clipper/SKILL.md` 的目录结构。

## 导入后

由用户在 MarginNote 的 CardLink 界面绑定答案。子卡模式在「筛选题目」中启用制卡使用的题目颜色。双册模式从题目分支绑定答案分支，追加或修改答案后由用户点「刷新答案索引」。

摘题、配对和导入规则见 [SKILL.md](./.agents/skills/cardlink-question-clipper/SKILL.md)。

[release]: https://github.com/sinner7620/cardlink-question-clipper/releases/tag/v1.0.1
