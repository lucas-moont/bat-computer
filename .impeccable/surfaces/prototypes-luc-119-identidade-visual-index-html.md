---
version: 1
slug: "prototypes-luc-119-identidade-visual-index-html"
primary_target: "prototypes/luc-119-identidade-visual/index.html"
related_targets: []
---

# Surface brief: janela principal do Bat-Computer (protótipo LUC-119)

Escopo: as três telas da janela (lista, detalhes com log, formulário), janela pequena 480×640 e média 880×580. Modo: Operate.

Tarefa: ver num relance o que roda e o que quebrou; ligar/desligar; ler o log de um projeto; cadastrar/editar. Até ~10 projetos. Cena: dev à noite, quarto escuro, janela ao lado do editor (por isso escuro).

Vetado pelo usuário: fantasia demais, genérico demais, log difícil de ler, status ambíguo. Variação A (noir/carimbos) descartada; B/C (ciano tático) é a linha aprovada.

## Direction contract

THESIS: Cada projeto é uma faixa de controle de tráfego aéreo encaixada na baia do seu estado (ATIVOS, FALHA, EM ESPERA). A posição é o status. Recusa o card grid de dashboard e a lista neutra com badges.

OWN-WORLD: sala de radar escura (#070B0E), baias como trilhos com régua 1px, faixas planas (#111C22) divididas em células por linhas finas, suporte colorido com forma na ponta esquerda (losango ciano RODANDO, triângulo vermelho ERRO, anel ardósia PARADO, âmbar na transição). Cor chapada, sem halo. Barlow/Barlow Semi Condensed para interface; JetBrains Mono só para comando, caminho, tempo e log.

STORY: o usuário bate o olho, vê quantas faixas estão em cada baia, liga uma faixa e a vê deslizar para ATIVOS; abre a transcrição para ler o log.

FIRST VIEWPORT: barra de 44px (nome, contagem, relógio, Novo projeto); à esquerda as três baias empilhadas com faixas de 48px (quadro de 430px fixo; a transcrição fica com o resto da largura); à direita (janela média) a transcrição do projeto selecionado com ações no cabeçalho. Na pequena, só as baias; a transcrição vira tela.

FORM: quadro de faixas de ATC, item 4 da minha lista ordenada; seed 4214fcc5. Movimento-assinatura: ligar/desligar desliza a faixa entre baias (FLIP, ~300ms, expo-out, com um breve brilho no suporte ao pousar; sem pulso contínuo), respeitando reduced motion. Raises: régua visível (Crouwel), cor plana (mapa), uma família (anuário), ↑↓ salta entre faixas (feed).

FINISH: unreviewed and undocumented is unfinished; this build ends with the finish review, the verdict, DESIGN.md, and every shipping raster carrying its provenance

## Decisões de implementação

- Fontes self-hosted no app Tauri (WebView2 pode estar offline): Barlow, Barlow Semi Condensed e JetBrains Mono via `@fontsource`. Nada de `<link>` do Google Fonts no app; o protótipo descartável usa o link só por conveniência.

## Modo compacto (contrato)

Aprovado pelo usuário em 2026-10-24, depois de descartar a barra deitada (horizontal) em favor de uma lista vertical com altura fixa e rolagem.

THESIS: a janela pequena encolhida. A mesma janela vira uma coluna de 236×170px (redimensionável de 200×110 até 420×640) que mora num canto da tela; as baias e as faixas de sempre, menores, com rolagem vertical. Recusa a barra deitada, o widget de ícones soltos e o menu da bandeja.

OWN-WORLD: o mesmo do Quadro de Faixas: suporte colorido com forma, face #111C22, réguas de 1px com tiques nos cabeçalhos de baia, Barlow + JetBrains Mono. Sem halo, sem pulso.

STORY: com o editor aberto, o usuário bate o olho na coluna, liga ou desliga um projeto com um clique e percebe na hora quando algo cai (contador vermelho ▲N no cabeçalho, faixa deslocada 8px na baia FALHA e a lista rola sozinha até ela).

FIRST VIEWPORT: cabeçalho de 32px (marca + BAT-COMPUTER como alça de arrastar, ▲N quando houver falha, + novo projeto, alfinete para fixar no topo, expandir); baias com cabeçalho de 18px (nome, contagem, régua), só as que têm faixas; faixas de 26px com ícone de estado (suporte de 20px), nome e botão ligar/desligar de 26px. Sem tempo rodando: o estado é o ícone (forma + cor) e o grupo de baia; a palavra fica no title e para leitores de tela. Transbordo: rolagem vertical com esmaecimento de 28px em cima/embaixo. Clicar no nome expande direto no log daquele projeto, no tamanho anterior.

FORM: Coluna de faixas finas (item 1 da lista de estruturas, rodada 019a0d38), pedida pelo usuário no lugar da Barra de faixas sorteada. Movimento: a mesma FLIP do quadro, só quando o tamanho não muda.

FINISH: unreviewed and undocumented is unfinished; this build ends with the finish review, the verdict, DESIGN.md, and every shipping raster carrying its provenance
