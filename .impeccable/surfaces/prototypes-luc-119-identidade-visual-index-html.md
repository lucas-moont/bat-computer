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
