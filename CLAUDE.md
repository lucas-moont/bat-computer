# Bat-Computer

App desktop (Tauri 2 + React + TypeScript, Windows) que centraliza os projetos pessoais: uma lista com Start/Stop, logs e cadastro por caminho + comando. Design em `docs/plans/2026-10-24-bat-computer-design.md`.

## Agent skills

### Issue tracker

Issues vivem num projeto do Linear, via ferramentas MCP do Linear; os identificadores de time e projeto ficam em `CLAUDE.local.md` (não versionado). See `docs/agents/issue-tracker.md`.

### Triage labels

Os cinco nomes canônicos, sem alteração (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`). See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: um `CONTEXT.md` + `docs/adr/` na raiz. See `docs/agents/domain.md`.
