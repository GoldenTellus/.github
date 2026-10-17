# GoldenTellus 贡献约定

GoldenTellus 的内容生产遵循“先确认，后发布”的原则。知识文章和案例目前统一放在 [goldentellus-home](https://github.com/GoldenTellus/goldentellus-home) 的 `docs/` 下；社群协作在 [goldentellus-community](https://github.com/GoldenTellus/goldentellus-community)。提交前请先阅读目标仓库的 README、模板与贡献说明。

## 内容边界

- 案例必须获得公开授权并完成脱敏；不得提交客户原始数据、个人信息、账号、日志截图或密钥。
- Demo 仅使用模拟数据或已授权的脱敏数据；不得声称演示代码是客户生产代码。
- 知识文章应区分事实、推断与观点，并写明适用边界和相关来源。
- 外部资源须验证链接、许可证、维护状态和重复项后再收录。

## Agent 管理流程

案例、理论和关联指令（`/case-new`、`/theory-new` 等）的完整规则见 [AGENT.md](./AGENT.md) 第 4 节。获得发布确认后，内容直接提交到 `goldentellus-home` 的 `main`，不经过 Pull Request。

## 提交信息

提交信息使用 [Conventional Commits](https://www.conventionalcommits.org/)：`feat:` 新内容、`fix:` 修正、`docs:` 文档与说明、`chore:` 维护。案例和知识文章建议写明 ID，例如 `feat(cases): add retail-001 inventory forecasting`。
