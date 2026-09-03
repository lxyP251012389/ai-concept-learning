# ai-concept-learning —— AI 概念学习仓库

《大数据与人工智能》课程作业 1：用 AI 构建个人概念学习资料生成 Skill。

本仓库包含：一个可复用的**项目级概念学习 Skill**（`concept-learner`），以及由该 Skill 生成、经本人人工核查的**概念学习资料**。后续课程学习中，可以用同一个 Skill 持续生成新概念的学习资料，仓库将作为个人学习工具箱和作品集不断迭代。

## 仓库结构

```
ai-concept-learning/
├── .workbuddy/
│   └── skills/
│       └── concept-learner/      # 项目级 Skill：概念学习资料生成器
│           └── SKILL.md
├── learning-materials/           # 由 Skill 生成的学习资料（自包含 HTML）
│   ├── agent.html                # 概念一：Agent（智能体）
│   ├── llm-context.html          # 概念二：大模型的上下文（Context）
│   ├── skill.html                # 概念三：Skill（技能）
│   └── concept-relationship.html # 三者关系说明（含关系图）
├── README.md
└── .gitignore
```

## concept-learner Skill 简介

- **位置**：`.workbuddy/skills/concept-learner/SKILL.md`（项目级 Skill，随仓库共享）
- **作用**：给定任意一个学习概念，按固定流程产出八板块学习资料：学习目标 → 核心问题 → 我的解释 → 核心机制 → 应用场景 → 概念辨析 → 自测问题 → 参考来源
- **质量约束**：参考来源必须是真实可访问的链接（生成时逐一验证 HTTP 200，标注访问日期），禁止编造来源；交付前执行自检清单；HTML 自包含、离线可打开
- **可复用性**：不针对特定概念写死，换任何新概念（如 RAG、注意力机制、MapReduce）都能用同一流程生成

## 如何在 WorkBuddy 中调用

1. 用 WorkBuddy 打开本仓库文件夹（`ai-concept-learning`）；
2. 在对话中直接说，例如：
   > "用 concept-learner 学习一下『检索增强生成（RAG）』这个概念，重点关注它和大模型上下文的关系。"
3. WorkBuddy 会根据 SKILL.md 的 `description` 匹配触发，按其中定义的步骤检索来源、生成 `learning-materials/rag.html`；
4. 生成后按 SKILL.md 的自检清单核对，人工阅读修订，再提交 Git。

## 已生成的学习资料

| 文件 | 概念 | 一句话摘要 |
|------|------|-----------|
| `learning-materials/agent.html` | Agent（智能体） | LLM + 工具 + 上下文 + 规划循环，自主把多步任务做完的执行者 |
| `learning-materials/llm-context.html` | 大模型的上下文 | 模型每次推理时"眼前的草稿纸"：系统提示、对话历史、工具说明、检索资料与当前输入 |
| `learning-materials/skill.html` | Skill（技能） | 写给 AI 的 SOP 手册：把做事方法沉淀为可版本化、可复用、可自动触发的文件 |
| `learning-materials/concept-relationship.html` | 三者关系 | Skill（经验）注入上下文（信息环境）塑造 Agent（行动），行动反馈再迭代 Skill |

## AI 使用说明与人工核查记录

**AI 参与的部分**：
- 环境搭建与 Git 操作（安装 git/Python/VS Code、创建仓库、clone/add/commit/push）
- 按 concept-learner Skill 的流程检索来源、起草三份学习资料与关系说明
- 起草 README 与 .gitignore

**本人完成的部分**（按作业要求逐项核查）：
- 阅读 SKILL.md 全文，确认八板块流程与来源红线符合个人学习习惯
- 逐份打开学习资料，核对概念解释与参考来源的真实性（链接可访问、内容相关）
- 对"我的解释"等 AI 起草段落按自己的理解做了修订改写
- 核对自测问题答案，修正了发现的问题

> 详细的核查修改记录见下方"核查修订日志"，随 Git 提交历史可追溯。

**核查修订日志**：
- 2026-09-03：AI 依据 concept-learner Skill 生成全部资料初稿；本人通过 WorkBuddy 预览面板逐份浏览整体内容，确认结构与来源后首次提交推送。
- 2026-09-03（人工修订）：按本人自己的理解改写三份资料「我的解释」板块的核心表述——Agent = 懂得主动思考、调用工具、独立干完复杂事情的 AI；上下文 = AI 可以利用的信息；Skill = 为 AI 智能体提供帮助并进行约束。以独立 commit 提交，作为人工核查修订的直接记录。
- 后续：学习过程中持续修订迭代，每次修订均以独立 commit 记录。

## 版本与安全

- 全部内容通过 Git 提交并 push 到 GitHub，提交历史完整可追溯；
- `.gitignore` 排除敏感信息（`.env`、密钥、凭据等）与 WorkBuddy 会话数据（`.workbuddy/memory/` 等），仓库中**不包含**任何 API Key、密码或个人隐私文件；
- 仓库保持公开访问，供课程教学查看。

## 后续计划

- [ ] 用 concept-learner 持续生成后续课程概念的学习资料（RAG、注意力机制、数据仓库……）
- [ ] 在使用中迭代 SKILL.md（补充新发现的规则与自检项）
- [ ] 尝试设计第二个个人 Skill（如"实验报告生成器"）
