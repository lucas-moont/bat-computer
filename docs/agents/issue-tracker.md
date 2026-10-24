# Issue tracker: Linear

Issues e specs deste repo vivem no **Linear**, time `LUC` (Lucas-moont-workspace), projeto `P-LUC-3` ("Bat-Computer"). Use as ferramentas MCP do Linear (`mcp__linear__*`) para todas as operações. Não há GitHub remoto e não se usa `.scratch/`.

O design do produto está no documento **"Design — Bat-Computer"** dentro do projeto `P-LUC-3` (cópia de `docs/plans/2026-10-24-bat-computer-design.md`).

## Convenções

- **Criar uma issue**: `save_issue` com `team: "LUC"`, `project: "P-LUC-3"`, `title` e `description` em Markdown. Bloqueios via `blockedBy` (identificadores como `LUC-122`).
- **Ler uma issue**: `get_issue` com o identificador (ex.: `LUC-122`), e `list_comments` para os comentários.
- **Listar issues**: `list_issues` com `project: "P-LUC-3"`, filtrando por `state` e `label` conforme necessário.
- **Comentar**: `save_comment` na issue.
- **Aplicar / remover labels**: `save_issue` com `id` e `addLabels` / `removeLabels`. Labels que ainda não existem no time são criadas com `save_issue_label` (`teamId` do time `LUC`).
- **Mudar status**: `save_issue` com `id` e `state` (`Backlog`, `Todo`, `In Progress`, `Done`, `Canceled`).
- **Fechar**: comentar o resultado com `save_comment` e depois `save_issue` com `state: "Done"` (ou `"Canceled"` se não for feito).

## Quando uma skill disser "publish to the issue tracker"

Criar uma issue no Linear, no time `LUC` e no projeto `P-LUC-3`.

## Quando uma skill disser "fetch the relevant ticket"

`get_issue <identificador>` + `list_comments`.

## Bloqueios e fronteira

- **Bloqueio**: a relação nativa do Linear (`blockedBy` / `blocks`). Uma issue está liberada quando todas as que a bloqueiam estão em `Done`.
- **Fronteira**: issues abertas do projeto, sem bloqueadora aberta e sem responsável. Na dúvida, a de menor número vence.

## Operações de wayfinding

Usadas por `/wayfinder`. O **mapa** é uma issue-mãe e os **tickets** são sub-issues dela.

- **Mapa**: uma issue com a label `wayfinder:map` no projeto `P-LUC-3`, contendo o corpo Notes / Decisions-so-far / Fog.
- **Ticket filho**: issue criada com `parentId` apontando para o mapa. Labels: `wayfinder:<tipo>` (`research`/`prototype`/`grilling`/`task`). Ao ser assumido, recebe `assignee: "me"`.
- **Bloqueio**: `blockedBy` nativo do Linear.
- **Consulta de fronteira**: sub-issues abertas do mapa, sem bloqueadora aberta e sem responsável; a primeira na ordem do mapa vence.
- **Assumir**: `save_issue` com `assignee: "me"` e `state: "In Progress"`, como primeira escrita da sessão.
- **Resolver**: `save_comment` com a resposta, `save_issue` com `state: "Done"` e depois acrescentar um ponteiro (resumo + link) em Decisions-so-far no corpo do mapa (`save_issue` com `patch`).
