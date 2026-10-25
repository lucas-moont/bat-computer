# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

App desktop para Windows: Tauri 2 empacota uma interface React rodando no WebView2. A linguagem visual é de web dentro de uma janela nativa, não a do Windows (Fluent).

## Users

Um desenvolvedor (o autor) com poucos projetos pessoais, até uns 10, que hoje abre o cmd, entra na pasta e digita `npm run dev` para cada um. A intenção é publicar o app depois, para outros devs com o mesmo problema.

## Product Purpose

Um "quadro de luz" para projetos locais: cada projeto vira uma linha com Start/Stop, status e logs, sem janelas de cmd espalhadas. Sucesso é nunca mais precisar abrir um terminal só para ligar ou desligar um projeto, e saber num relance o que está rodando e o que quebrou.

## Positioning

Não é um gerenciador de processos genérico nem um painel de DevOps. É pequeno, pessoal e com personagem: o "Batcomputador" do desenvolvedor. Fechar o app encerra tudo o que ele ligou, inclusive em crash (Job Object do Windows).

## Operating Context

- Janela pequena ou média, aberta ao lado do editor.
- Poucos projetos (até ~10): a lista cabe sem rolar; busca e filtro não são prioridade.
- Três telas: lista principal, detalhes com logs ao vivo, formulário de adicionar/editar.
- Logs ficam só na tela de detalhes, com buffer de 1000 linhas por projeto.

## Capabilities and Constraints

- Cadastro: nome, pasta, comando (scripts do `package.json` ou comando livre), URL opcional.
- Status: PARADO, RODANDO, ERRO. RODANDO significa "processo vivo", não "servidor respondendo".
- Botão "Abrir no navegador" só quando há URL e o projeto está rodando.
- A edição fica bloqueada enquanto o projeto roda; apagar pede confirmação e para o processo antes.
- Fora da v1: bandeja do sistema, iniciar com o Windows, abrir pasta/VS Code, detecção de URL nos logs, health check.
- Stack: Tauri 2 + React + TypeScript + Vite (ver `docs/plans/2026-10-24-bat-computer-design.md`).

## Brand Commitments

- Nome do projeto: Bat-Computer. Tema "Batcomputador".
- Sem marcas registradas da DC: nada de símbolo do morcego, das palavras "Batman", "Batmobile", "Gotham City", de logos de filmes ou empresas fictícias, nem dos glifos da cifra do Charada (ver `docs/research/2026-10-24-referencias-visuais-batcomputador.md`).
- **Em aberto:** como o app deve ser publicado, o nome "Bat-Computer" precisa ser revisto antes do lançamento público. Não foi verificado se "Batcomputer" é marca registrada.

## Evidence on Hand

- Design: `docs/plans/2026-10-24-bat-computer-design.md`.
- Pesquisa de referências visuais: `docs/research/2026-10-24-referencias-visuais-batcomputador.md`.
- Protótipo descartável com três direções: `prototypes/luc-119-identidade-visual/index.html` (só no galho `prototype/luc-119-identidade-visual`).
- Não há usuários, depoimentos nem métricas. Não inventar.

## Product Principles

1. Um relance basta: o estado de todos os projetos se lê sem clicar.
2. O tema serve à ferramenta: identidade nos detalhes, nunca à custa de ler um log.
3. Nada fica para trás: o que o app ligou, o app desliga.
4. Pequeno de propósito: cada recurso novo precisa caber na janela ao lado do editor.

## Accessibility & Inclusion

Sem necessidade específica declarada. Mínimo: contraste WCAG 2 AA, status com texto e forma (não só cor) e respeito a `prefers-reduced-motion`.
