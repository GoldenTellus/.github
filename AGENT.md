# GoldenTellus Organization — Agent 指引

本文件是 AI Agent（Claude Code / Codex）管理 GitHub Organization **GoldenTellus（金域）** 的公开规则：仓库、文档、内容发布、Issue/PR/Discussion、自动化和组织设置。除非另行指定，任务按 Organization 级别处理。

- 默认语言：中文；代码、仓库名、API 字段和技术术语用英文

## 1. 组织定位（已确认）

GoldenTellus 是围绕「AI 应用落地」的 FDE 社群：分享 FDE 知识、拆解脱敏的真实案例、开源可运行 Demo，用学习内容吸引 FDE，用案例让企业认识社群。

核心主张：**FDE 不是六边形战士，而是一条协作流水线。** 一个人早期可以兼任多个工位，但这是过渡状态。设计内容时体现「找到自己的工位、做好阶段交接、共同完成交付」。流水线角色（诊断 / 架构 / 开发 / 数据 / 集成 / 运营 / Lead FDE）是讨论模型，命名和数量可调整。

受众：FDE 学习者、FDE 从业者、有 AI 落地需求的企业。「AI 应用开发者」是候选扩展受众，未确认。

## 2. 公开仓库（以 GitHub 实际状态为准，2026-10 核对）

| 仓库 | 可见性 | 用途 |
|---|---|---|
| `.github` | 公开 | 组织主页 `profile/README.md`、`AGENT.md`、公共贡献约定 |
| `goldentellus-home` | 公开 | 门面、导航、新人/企业/FDE 入口；MkDocs 站点（`docs/`，部署到 Pages）；**同时承载案例与知识内容**（见第 4 节） |
| `goldentellus-community` | 公开 | 社群治理、成员、组队、活动、合作伙伴 |

另有若干私有仓库，不在此列出。

已被维护者主动删除（不要重建，也不要再作为写入目标）：`goldentellus-cases`、`goldentellus-labs`、`goldentellus-demos`、`goldentellus-knowledge`、`goldentellus-playbooks`、`goldentellus-roadmap`、`goldentellus-toolkit`、`goldentellus-reports`、`goldentellus-enterprise`、`awesome-fde`、`goldentellus-poster-skill`、`goldentellus-site`。

规则：任何文档里的仓库表与 `gh repo list GoldenTellus` 不一致时，以 GitHub 实际状态为准，并更新文档。

## 3. 操作权限分级

先读后写。每次任务开始先用 `gh` 和 `git status` 核对实际状态，再动手。

| 级别 | 示例 | 处理方式 |
|---|---|---|
| 只读 | 查看仓库、Issue、PR、Actions、设置、成员 | 直接执行 |
| 本地可逆 | 改本地文件、建分支、本地 commit、跑检查 | 直接执行，完成后汇报 |
| 外部写入 | push、开/合 PR、发 Issue/Discussion/评论、改标签、改 README、建 Project 卡片 | 先说明要写什么、写到哪，用户确认后执行（第 4 节的内容发布有单独授权规则） |
| 高风险 | 建/删/改名/归档/转移仓库、改可见性、成员与团队、权限、分支保护、Secrets、Webhook、Pages、组织设置、账单 | 说明影响和是否可逆，**每次**取得用户明确确认；一次授权不延续到下一次 |

- 默认不碰：个人账号设置、付款账单、第三方平台账号（公众号、抖音、小红书等）、客户生产系统、成员隐私。
- 密钥、Token、Cookie 只走环境变量或凭据管理器，绝不写入仓库、文档或命令历史。
- 不扩大权限；报告时不把未执行的外部动作说成已完成。
- 提交信息用 conventional commits（`feat:` / `fix:` / `docs:` / `chore:` …）。

## 4. 内容发布链路（案例与理论）

原先的 cases / knowledge 等仓库已删除。按用户决定，**案例和理论内容暂时都放进 `goldentellus-home`**，内容多了再拆分独立仓库（拆分属于高风险操作，需确认）。

| 内容 | 位置 |
|---|---|
| 案例正文 | `goldentellus-home/docs/cases/by-industry/<industry>/<id>-<slug>.md`（正文唯一存放处） |
| 案例索引 | `goldentellus-home/docs/cases/index.md`（按行业 / 流水线阶段 / 难度列链接，不复制正文） |
| 理论与角色知识 | `goldentellus-home/docs/knowledge/<dir>/`，目录：`00-pipeline-fundamentals`、`01-lead-fde`、`02-analyst`、`03-architect`、`04-builder`、`05-data-engineer`、`06-integrator`、`07-ops`、`99-general` |
| Demo、外部资源合集、行业报告 | 暂无目标仓库。需要时先提议放置方案，用户确认后再建 |

新增页面后同步更新 `mkdocs.yml` 的 `nav`，并跑一次 `mkdocs build --strict` 确认站点能构建。

### 4.1 聊天指令

识别 `/case-new`、`/case-update {id}`、`/case-status`、`/theory-new`、`/theory-extract`、`/theory-update {id}`、`/theory-status`、`/link {case-id} {knowledge-id}`、`/skip`、`/pipeline-status`，以及意思相同的自然语言。这些是对话约定，不是 CLI；状态以对话、文件 frontmatter 和索引为准，不另建日志。理论讨论每三轮或出现关键结论时，给一次当前理解摘要供用户纠正。

### 4.2 发布授权

- 用户在案例阶段明确确认「已脱敏、有授权、可公开」，或在理论阶段确认核心观点、证据和边界后，该确认即为本次内容直接推送到 `goldentellus-home` 的 `main` 的授权，不开 PR。
- 发布前先列出将写入的文件、分类和关联关系。
- 可以新建文件、目录、索引条目；可以追加内容、更新元数据。不得删除已有内容、覆盖已确认事实、虚构数据。
- 内容分类以 frontmatter 和索引为准（Label 无法附着在提交上）。

### 4.3 案例拆解

1. 素材分四类：业务背景、技术方案、实施过程、结果数据。至少有三类才开始拆解；缺的标 `[待补充]`，不涉及的阶段标 `[不适用]`。
2. 先查敏感信息：公司名、人名、联系方式、账号、订单号、截图、日志、原始数据、密钥。发现后由用户确认替换方案。他人的案例要确认授权，自己的案例要确认公开范围。
3. 按诊断、架构、开发、数据、集成、运营六段拆解，每段写关键决策和原因，区分事实、客户提供数据、估算和推断。
4. Demo 只在技术方案足够具体、用户同意时才做，标注「演示用途」，只用模拟或已授权脱敏的数据。
5. 单个案例不能当作行业趋势结论。
6. 发布后可以主动建议可提炼的理论方向，用户确认后再进入理论链路。

### 4.4 理论提炼

1. 提炼出一句话观点、论据、适用和不适用场景、前提条件、反例、实践映射。多个独立观点拆成多篇。
2. 每个结论标明是「事实」「推断」还是「观点」。只把用户确认过的内容作为公开主张。
3. 发布前扫描同目录里的标题、ID、关键词。内容重复时优先更新已有文章；新编号从现有 ID 往后顺延。

### 4.5 完成校验

frontmatter 完整、站内链接有效、`mkdocs build --strict` 通过。发布后汇报提交号、文件、关联条目和待补充项。
