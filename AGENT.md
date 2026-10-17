# GoldenTellus Organization — Agent Guide

This file defines the public rules for AI Agents (Claude Code / Codex) managing the **GoldenTellus** GitHub organization: repositories, documentation, content publishing, Issues/PRs/Discussions, automation, and organization settings. Unless otherwise specified, tasks operate at the organization level.

- **Default language**: English for code, repo names, API fields, technical terms; Chinese for user-facing prose when the user is Chinese-speaking.

## 1. Organization Purpose (Confirmed)

**GoldenTellus deploys SNAO** (a multi-tenant agent platform) in enterprises, extracts production-tested capabilities during work, desensitizes them, and open-sources them in universal formats.

**Core value proposition**:
- **For enterprises**: Turn their deployment into an asset by extracting reusable capabilities
- **For developers**: Access production-validated AI tools, skills, and knowledge packs
- **For the ecosystem**: Universal formats (MCP/Skill/OpenAPI/standalone) that work across platforms

**Current status** (as of 2026-10):
- 0 capabilities published (first batch in progress)
- 0 production SNAO deployments (platform in development)
- Building in public: roadmap, architecture, and standards are public before the first deployment

## 2. Public Repositories (Match GitHub actual state, verified 2026-10)

| Repository | Visibility | Purpose |
|---|---|---|
| `.github` | Public | Organization profile (`profile/README.md`), `AGENT.md`, shared contributing guide |
| `goldentellus-home` | Public | Main landing site (MkDocs), SNAO overview, developer/enterprise documentation |
| `goldentellus-capabilities` | Public | Production-tested capabilities: skills, tools, knowledge packs, external roles |
| `goldentellus-community` | Public | Community governance, contributors, events, partners |

Private repos are not listed here.

**Deleted repos** (do not recreate or reference as targets): `goldentellus-cases`, `goldentellus-labs`, `goldentellus-demos`, `goldentellus-knowledge`, `goldentellus-playbooks`, `goldentellus-roadmap`, `goldentellus-toolkit`, `goldentellus-reports`, `goldentellus-enterprise`, `awesome-fde`, `goldentellus-poster-skill`, `goldentellus-site`.

**Rule**: When any documentation table conflicts with `gh repo list GoldenTellus`, GitHub's actual state is authoritative; update the documentation.

## 3. Operation Permission Levels

Read before write. Start every task by verifying actual state with `gh` and `git status`.

| Level | Examples | How to Handle |
|---|---|---|
| Read-only | View repos, issues, PRs, actions, settings, members | Execute directly |
| Local reversible | Edit local files, create branches, local commits, run checks | Execute directly, report after |
| External write | Push, open/merge PR, create issue/discussion/comment, change labels, edit README, create project cards | Describe what/where first, execute after user confirms (content publishing has separate rules in §4) |
| High-risk | Create/delete/rename/archive/transfer repos, change visibility, manage members/teams, permissions, branch protection, secrets, webhooks, Pages, org settings, billing | Explain impact and reversibility, **get explicit confirmation every time**; one authorization does not carry to the next |

- **Never touch**: Personal account settings, billing/payments, third-party platform accounts (WeChat, TikTok, Xiaohongshu), customer production systems, member privacy.
- **Secrets**: API keys, tokens, cookies only via environment variables or credential managers; never write to repos, docs, or command history.
- **Do not escalate permissions**; do not report un-executed external actions as complete.
- **Commit messages**: Use conventional commits (`feat:` / `fix:` / `docs:` / `chore:` …).

## 4. Content Publishing Flow (Capabilities)

**All capability submissions** go to `goldentellus-capabilities`. See that repo's CONTRIBUTING.md for quality standards, proposal process, and maintenance expectations.

Agent workflow when the user provides a capability:

### 4.1 Chat Commands

Recognize `/capability-new`, `/capability-update {id}`, `/capability-status`, and natural-language equivalents. These are conversation conventions, not CLI tools; state is tracked in files and conversation.

### 4.2 Publishing Authorization

- User confirms "production-tested, desensitized, authorized to publish" → this is authorization to push directly to `goldentellus-capabilities` on `main`; no PR.
- Before publishing: list files to be written, category, and manifest format.
- Can create new files, directories, index entries; can append content, update metadata. Cannot delete existing confirmed content, overwrite facts, or fabricate data.

### 4.3 Capability Extraction

1. **Collect**: Business context, technical approach, implementation notes, validation results.
2. **Desensitize**: Check for company names, personal info, credentials, logs, raw data, keys. User confirms replacement strategy.
3. **Universal format**: MCP server, Claude skill, OpenAPI tool, knowledge pack, or standalone script. Follow MANIFEST_FORMAT.md.
4. **Self-contained**: Include dependencies, example usage, test cases where applicable.
5. **Classify**: Label by domain (retail, healthcare, finance…) and capability type (skill, tool, knowledge).
6. **Authorship**: Credit original implementer (unless anonymous); mark GoldenTellus as publisher.

### 4.4 Completion Check

- Manifest complete per MANIFEST_FORMAT.md
- Dependencies listed
- Example usage included
- No sensitive information
- Build verification passes (if applicable)
- Linked from `goldentellus-capabilities/README.md` index

After publishing: report commit hash, files written, category, and any pending items.

## 5. Documentation Publishing Flow (goldentellus-home)

For documentation improvements (not capabilities):

- **Typo fixes**: Execute directly after user confirms intent
- **Content updates**: List changes first, execute after confirmation
- **New pages**: Propose structure first; after user confirms, write and update `mkdocs.yml` nav
- **Verification**: Run `mkdocs build --strict` before pushing

## 6. Current Priorities (2026-10)

1. **Pivot complete**: Organization content restructured from FDE training → SNAO + production capabilities
2. **Next milestone**: First capability batch published (0/N complete)
3. **After first batch**: Production SNAO deployment begins

All work aligns with "build in public" principle: roadmap, architecture, and standards visible before first deployment.
