# writing-workflow

一套写给 AI 写作代理的通用写作工作流：**八段骨架、五个放行门、双审合并的审改循环**。

适用于一切要交出去的成文文本——学位论文、期刊论文、技术报告、开题/标书、专利、PPT 文案、简历、宣传稿。短文本（邮件、通知）可压缩跑。

---

## 它解决什么

写作返工很少是句子不好，是四件事没在动笔前锁死：

1. 读者拿这份东西做什么决定；
2. 每个主张的来源；
3. 图里的数和正文是不是同一份；
4. 交付格式有哪些坑（页码、目录、三线表、字体嵌入）。

这套流程把四件事变成可检查的门，而不是靠自觉。

## 流程

```
动笔前置 → S0 任务卡 → S1 证据台账 → S2 骨架 → S3 素材冻结
        → S4 成稿 → S5 审改循环 → S6 交付 → S7 归档
```

| 阶段 | 做什么 | 放行门 |
|---|---|---|
| 前置 | 加载 `anti-defensive-writing`，先定叙事骨架与取舍 | 没定叙事不动笔 |
| S0 任务卡 | 读者与决定、交付、验收、事实边界、文体语气 | 写不出"读者要做什么决定"不开写 |
| S1 证据台账 | 主张、来源、状态（定案/待补/禁用/推断） | 待补不许写成已完成；无来源的主张删掉 |
| S2 骨架 | 章节树，每节一句"本节让读者接受什么" | 每节有台账行支撑，每条台账行有落点 |
| S3 素材冻结 | 图表、数据表、引文先定稿 | 图内每个数字能指到台账；每条引用能打开原文 |
| S4 成稿 | 一节一写，同时带结构与论证两套标准 | 读完一节能说出"这节证明了什么" |
| S5 审改循环 | 去 AI 味 → 双审 → 合并裁决 → 修改 → 对账 → 终审 | 0 CRITICAL，MAJOR 全落实或书面说明，剩余只在措辞级 |
| S6 交付 | 按格式取检查单，看渲染结果 | 页数、目录、末页三项逐项核对 |
| S7 归档 | 源、成品、脚本同目录；写一条经验 | 只靠归档能复现 |

## 动笔前置

写第一句之前，必须先定叙事：这份东西最值得交付的是什么，围绕它组织，不平均展示，不写过程流水账，不主动示弱。

优先级从高到低：

1. **`anti-defensive-writing`**：叙事骨架、内容取舍、主张强度、弱点披露口径。
2. **学校 / 单位模板**：规定栏目与结构必须服从；栏目内措辞仍按第 1 条。
3. **事实边界**：要不要主动写异常值、局限、方向相反的结果，写到什么程度。
4. **文体惯例**。
5. **通用文风**（去 AI 味等表面层规则）。

数字与来源的一致性由 S1 台账和 S5 对账保证，属流程门，不参与上述排序。

## 审改循环

唯一允许反复的环节，五步：

1. **初稿去 AI 味**：白名单式清理，只改表面，不动结构、不改数字。
2. **导师审**：`pre-submission-reviewer`（结构、写作、格式）与 `nature-reviewer`（科学问题、证据强度、结论边界）并行，两份意见先合并成一张表。
3. **合并裁决与修改**：去重、判冲突、每条标采纳/部分采纳/不采纳，先结构后论证最后措辞。
4. **对账复验**：数值、引用、交叉引用三张表零差异。
5. **再去 AI 味 + 回归终审**：只查上轮意见是否落实、是否引入新问题，不全篇重审。

合并规则：同一问题两边都提就合并、严重度取高；冲突按维度归属裁决（结构/写作/格式 → `pre-submission-reviewer`，科学问题/证据强度/结论边界 → `nature-reviewer`）；不写"两边都满足"的折中句。

验收：CRITICAL 为 0；MAJOR 全部落实或有书面不采纳理由；剩余意见只在措辞级。**最多 3 轮**，超过回骨架重排或交真人裁决。

## 安装

```bash
git clone https://github.com/Bigsillymao/writing-workflow.git ~/.zcode/skills/writing-workflow
```

Windows PowerShell：

```powershell
git clone https://github.com/Bigsillymao/writing-workflow.git "$env:USERPROFILE\.zcode\skills\writing-workflow"
```

其他支持 `SKILL.md` 的代理环境，把仓库放进对应的 skills 目录即可。

## 用法

触发场景：写论文、写报告、写稿、改稿、交付文档、判断该用哪个写作技能。

短文本只跑 S0 和 S4。长篇走完整流程。

最小任务卡：

| 字段 | 示例 |
|---|---|
| 读者与决定 | 导师，判断能否送审 |
| 交付 | docx，8000 字，11-30 |
| 验收 | 数据可追溯、图与正文一致、格式合模板 |
| 事实边界 | 第二批数据未到，需注明；对照试验未做 |
| 文体与语气 | 学位论文，记录为主 |

最小台账：

| 主张 | 来源 | 状态 |
|---|---|---|
| 峰值出现在第 3 组 | 原始记录 `summary.md` 表 1 第 3 行 | 定案 |
| 第 4 组数据 | 尚未交付 | 待补 |
| 效果随参数单调增强 | 与第 3 组达峰结果不符 | 禁用 |

## 依赖

配套技能是推荐实现，不是硬依赖。没有时按能力维度降级，流程和门不变：

- 起草：`paper-writer` / `nature-writing`
- 去 AI 味：`lieflat-less-ai-tone`
- 审查：`pre-submission-reviewer` / `nature-reviewer`
- 画图：`figure-designer` + `origin-plot`
- 文献核验：`nature-ref-verifier`
- 文档交付：`documents:docx` / `presentations:pptx` / `pdf`

详见 `SKILL.md` 的「依赖与降级」。

## 文件

- `SKILL.md` —— 技能正文，八段流程、门、路由表、已知失败清单
- `LICENSE` —— MIT

## 来源与致谢

- **anti-defensive-writing**：Adkid-Zephyr，MIT。本仓库不包含其内容，仅要求先行加载。
- **Supervisor-Skills**：HKUSTDial，CC BY-NC-SA 4.0。本仓库仅引用技能名（`pre-submission-reviewer`、`nature-reviewer` 等），不包含其内容。

## License

MIT。见 `LICENSE`。

---

## English summary

A writing workflow for AI agents and human authors: eight stages, five gates, and a two-reviewer revision loop.

Core rules: choose the narrative before writing; lock every claim to a source before drafting; freeze figures and citations before prose; reconcile numbers, citations, and cross-references after every revision; and iterate only until reviewers raise no structural comments (maximum three rounds).

The workflow is tool-agnostic. Named skills are recommended implementations with graceful degradation, not dependencies.
