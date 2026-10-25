---
name: Bat-Computer
description: Quadro de faixas para ligar, desligar e ler o log dos projetos locais, numa janela ao lado do editor.
colors:
  radar-ground: "#070B0E"
  rack: "#0A1216"
  strip-face: "#111C22"
  strip-face-raised: "#16252E"
  rule: "#1C2B33"
  line: "#263943"
  control-hover: "#1C2F3A"
  control-hover-line: "#3A5664"
  ink: "#DCEBF2"
  mute: "#8CA3B0"
  dim: "#7A93A3"
  signal-cyan: "#3FD8FF"
  signal-cyan-bright: "#86E8FF"
  fault-red: "#FF5C4D"
  fault-red-text: "#FF9A90"
  transit-amber: "#F2B33D"
  slate-holder: "#2A3A43"
  slate-ink: "#A9BCC7"
  on-cyan: "#03141B"
  on-red: "#1A0402"
  on-amber: "#1A1203"
typography:
  title:
    fontFamily: "Barlow Semi Condensed, sans-serif"
    fontSize: "20px"
    fontWeight: 600
    lineHeight: 1.2
  brand:
    fontFamily: "Barlow Semi Condensed, sans-serif"
    fontSize: "15px"
    fontWeight: 600
    letterSpacing: "0.08em"
  strip-name:
    fontFamily: "Barlow, sans-serif"
    fontSize: "15px"
    fontWeight: 600
  body:
    fontFamily: "Barlow, sans-serif"
    fontSize: "14px"
    fontWeight: 400
    lineHeight: 1.4
    fontFeature: "tnum"
  control:
    fontFamily: "Barlow, sans-serif"
    fontSize: "13px"
    fontWeight: 500
  bay-label:
    fontFamily: "Barlow Semi Condensed, sans-serif"
    fontSize: "12px"
    fontWeight: 600
    letterSpacing: "0.14em"
  cell-label:
    fontFamily: "Barlow Semi Condensed, sans-serif"
    fontSize: "11px"
    fontWeight: 600
    letterSpacing: "0.12em"
  fact-label:
    fontFamily: "Barlow Semi Condensed, sans-serif"
    fontSize: "10.5px"
    fontWeight: 600
    letterSpacing: "0.12em"
  mono-data:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "12px"
    fontWeight: 400
  mono-command:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "11.5px"
    fontWeight: 400
  mono-input:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "12.5px"
    fontWeight: 400
  log:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "12px"
    fontWeight: 400
    lineHeight: 1.6
  log-tag:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "10px"
    fontWeight: 700
  mini-brand:
    fontFamily: "Barlow Semi Condensed, sans-serif"
    fontSize: "11px"
    fontWeight: 600
    letterSpacing: "0.08em"
  mini-bay-label:
    fontFamily: "Barlow Semi Condensed, sans-serif"
    fontSize: "10px"
    fontWeight: 600
    letterSpacing: "0.14em"
  mini-count:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "10.5px"
    fontWeight: 500
  mini-name:
    fontFamily: "Barlow, sans-serif"
    fontSize: "12.5px"
    fontWeight: 600
  alert-count:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "10.5px"
    fontWeight: 700
rounded:
  holder: "2px"
  control: "3px"
spacing:
  slot-gap: "4px"
  bay-head-gap: "6px"
  cell-inset: "10px"
  board-inset: "12px"
  panel-inset: "14px"
  bay-gap: "16px"
components:
  top-bar:
    backgroundColor: "{colors.rack}"
    textColor: "{colors.ink}"
    height: "44px"
    padding: "0 12px 0 14px"
  board:
    backgroundColor: "{colors.radar-ground}"
    width: "430px"
    padding: "12px 12px 18px"
  strip:
    backgroundColor: "{colors.strip-face}"
    textColor: "{colors.ink}"
    typography: "{typography.strip-name}"
    rounded: "{rounded.control}"
    height: "48px"
  strip-hover:
    backgroundColor: "{colors.strip-face-raised}"
  strip-selected:
    backgroundColor: "{colors.strip-face-raised}"
  holder-stop:
    backgroundColor: "{colors.slate-holder}"
    textColor: "{colors.slate-ink}"
    rounded: "{rounded.holder}"
    width: "30px"
  holder-run:
    backgroundColor: "{colors.signal-cyan}"
    textColor: "{colors.on-cyan}"
    rounded: "{rounded.holder}"
    width: "30px"
  holder-err:
    backgroundColor: "{colors.fault-red}"
    textColor: "{colors.on-red}"
    rounded: "{rounded.holder}"
    width: "30px"
  holder-busy:
    backgroundColor: "{colors.transit-amber}"
    textColor: "{colors.on-amber}"
    rounded: "{rounded.holder}"
    width: "30px"
  bay-empty:
    textColor: "{colors.dim}"
    rounded: "{rounded.control}"
    height: "32px"
    padding: "0 12px"
  button:
    backgroundColor: "{colors.strip-face-raised}"
    textColor: "{colors.ink}"
    typography: "{typography.control}"
    rounded: "{rounded.control}"
    height: "30px"
    padding: "0 12px"
  button-hover:
    backgroundColor: "{colors.control-hover}"
  button-go:
    backgroundColor: "{colors.strip-face-raised}"
    textColor: "{colors.signal-cyan}"
    typography: "{typography.control}"
    rounded: "{rounded.control}"
    height: "30px"
    padding: "0 12px"
  button-primary:
    backgroundColor: "{colors.signal-cyan}"
    textColor: "{colors.on-cyan}"
    typography: "{typography.control}"
    rounded: "{rounded.control}"
    height: "30px"
    padding: "0 12px"
  button-primary-hover:
    backgroundColor: "{colors.signal-cyan-bright}"
  button-danger-fill:
    backgroundColor: "{colors.fault-red}"
    textColor: "{colors.on-red}"
    rounded: "{rounded.control}"
    height: "30px"
    padding: "0 12px"
  icon-button:
    textColor: "{colors.mute}"
    rounded: "{rounded.control}"
    size: "30px"
  input:
    backgroundColor: "{colors.radar-ground}"
    textColor: "{colors.ink}"
    typography: "{typography.mono-input}"
    rounded: "{rounded.control}"
    height: "32px"
    padding: "0 9px"
  transcript:
    backgroundColor: "{colors.rack}"
    textColor: "{colors.ink}"
    padding: "12px 14px 10px"
  log:
    backgroundColor: "{colors.radar-ground}"
    textColor: "{colors.ink}"
    typography: "{typography.log}"
    padding: "6px 0 10px"
  menu:
    backgroundColor: "{colors.strip-face-raised}"
    textColor: "{colors.ink}"
    rounded: "{rounded.control}"
    padding: "4px"
  mini-column:
    backgroundColor: "{colors.rack}"
    textColor: "{colors.ink}"
    width: "236px"
    height: "170px"
  mini-head:
    backgroundColor: "{colors.rack}"
    textColor: "{colors.ink}"
    typography: "{typography.mini-brand}"
    height: "32px"
    padding: "0 3px 0 7px"
  mini-list:
    backgroundColor: "{colors.rack}"
    padding: "3px 5px 6px"
  mini-bay-head:
    textColor: "{colors.mute}"
    typography: "{typography.mini-bay-label}"
    height: "18px"
  mini-strip:
    backgroundColor: "{colors.strip-face}"
    textColor: "{colors.ink}"
    typography: "{typography.mini-name}"
    rounded: "{rounded.control}"
    height: "26px"
  mini-holder:
    rounded: "{rounded.holder}"
    width: "20px"
  mini-toggle:
    textColor: "{colors.mute}"
    width: "26px"
  mini-alert:
    backgroundColor: "{colors.fault-red}"
    textColor: "{colors.on-red}"
    typography: "{typography.alert-count}"
    rounded: "{rounded.control}"
    height: "18px"
    padding: "0 5px"
  mini-icon-button:
    textColor: "{colors.mute}"
    rounded: "{rounded.control}"
    size: "24px"
  icon-button-pinned:
    textColor: "{colors.signal-cyan}"
    rounded: "{rounded.control}"
    size: "24px"
---

# Design System: Bat-Computer

## Overview

**Creative North Star: "A Sala de Radar"**

Cada projeto é uma faixa de controle de tráfego aéreo encaixada na baia do seu estado: ATIVOS, FALHA, EM ESPERA. A posição é o status. O quadro é lido como um controlador lê a mesa de faixas: quantas faixas há em cada trilho, qual suporte está aceso, qual faixa está torta. Recusamos o grid de cards de dashboard e a lista neutra com badges; o estado não é um enfeite ao lado do nome, é o lugar onde a faixa mora.

O mundo é uma sala escura, porque o app vive ao lado do editor à noite. O fundo é quase preto azulado, as baias são trilhos com régua de 1px, as faixas são placas planas divididas em células por linhas finas, e a única cor forte de cada faixa está no suporte da ponta esquerda, que carrega também uma forma (losango, triângulo, anel). Cor chapada, sem halo, sem brilho contínuo. A identidade "Batcomputador" vive nos detalhes (a precisão do quadro, o ciano de sinal, a régua), nunca à custa de ler um log.

A densidade é de ferramenta: faixas de 48px, barra de 44px, controles de 30px, até ~10 projetos cabendo sem rolar. No modo compacto, a mesma janela encolhe para uma coluna de 236×170px que mora num canto da tela: as mesmas baias e faixas, menores, empilhadas com rolagem vertical. Barlow e Barlow Semi Condensed falam a interface; JetBrains Mono aparece só onde há dado de máquina (comando, caminho, tempo, contagem, log).

**Key Characteristics:**
- A posição é o status: três baias fixas, na ordem ATIVOS, FALHA, EM ESPERA.
- Status sempre em três canais: baia, cor+forma do suporte e texto.
- Superfícies planas em tons de azul-ardósia; profundidade por tom e linha de 1px, não por sombra.
- Um único movimento-assinatura: a faixa desliza de baia ao mudar de estado.
- Mono só para dados de máquina.
- Duas escalas de quadro: o quadro inteiro (janelas média e pequena) e a coluna compacta, com o mesmo vocabulário de baia, faixa, suporte e régua.

## Colors

Uma sala escura em azul-ardósia com três sinais chapados (ciano, vermelho, âmbar) que só aparecem onde há estado.

### Primary
- **Ciano de Sinal** (signal-cyan): o sinal de "vivo" e de ação positiva. Preenche o suporte das faixas RODANDO, colore o rótulo da baia ATIVOS e o texto de estado "Rodando", o botão primário ("Novo projeto", "Salvar", "Adicionar ao quadro"), o ícone e a borda do botão Ligar, o anel de foco (1px), o cursor de texto e a borda do campo em foco. Na coluna compacta, também a marca no cabeçalho e o alfinete ligado (ícone ciano, borda a 45%, fundo a 8%). A faixa selecionada usa o ciano a 60% na borda (`rgba(63,216,255,.6)`); o botão Ligar usa o ciano a 45% na borda e a 10% no fundo do hover.
- **Ciano Aceso** (signal-cyan-bright): só o hover do botão primário.

### Secondary
- **Vermelho de Falha** (fault-red): ERRO. Preenche o suporte das faixas em falha, colore a baia FALHA, o texto "Erro", a tag ERR do log, o botão de apagar (ícone), o botão de confirmação de apagar (preenchido) e o contador de falha ▲N da coluna compacta (preenchido). Fundos de alerta usam o vermelho a 7% com borda a 55%.
- **Vermelho de Leitura** (fault-red-text): o texto das linhas de erro no log e das notas de erro do formulário, mais claro que o sinal para ser lido em corrido sobre o fundo avermelhado.

### Tertiary
- **Âmbar de Trânsito** (transit-amber): transição ("Ligando…", "Desligando…") e mensagens do sistema. Preenche o suporte da faixa em trânsito, colore o texto de estado, a tag SYS e o texto das linhas SYS no log, e a nota de "edição bloqueada" do formulário (borda a 50%, fundo a 6%).

### Neutral
- **Chão do Radar** (radar-ground): fundo da janela e do quadro, fundo do log e dos campos de texto. O ponto mais escuro: o que está "afundado".
- **Rack** (rack): barra superior e painel da transcrição/formulário. Um passo acima do chão.
- **Face da Faixa** (strip-face): a placa da faixa e o grid de fatos da transcrição.
- **Face Erguida** (strip-face-raised): hover e seleção da faixa, fundo dos botões padrão, do menu e do toast.
- **Régua** (rule): linhas de 1px entre células da faixa, contorno da faixa em repouso, divisores de painel.
- **Linha** (line): contorno dos controles, régua das baias, contorno tracejado de vazios, polegar da barra de rolagem.
- **Hover de Controle** (control-hover / control-hover-line): fundo e borda do botão padrão no hover.
- **Tinta** (ink): texto principal, nomes de projeto, valores de dado.
- **Tinta Calada** (mute): comando sob o nome, caminho, rótulos de baia neutros, ícones das ações da faixa, cabeçalho do log, rótulos de campo.
- **Tinta Apagada** (dim): relógio, horário das linhas de log, rótulos do grid de fatos, placeholders, dicas e vazios. Passa AA sobre radar-ground e strip-face.
- **Suporte Ardósia** (slate-holder) e **Tinta Ardósia** (slate-ink): suporte e texto de estado de PARADO. Neutro de propósito: parado não é alarme.
- **Tinta sobre Sinal** (on-cyan, on-red, on-amber): texto e forma sobre os preenchimentos ciano, vermelho e âmbar. Quase pretos tingidos do próprio sinal, nunca preto puro nem branco. on-red é também o triângulo e o número do contador ▲N da coluna compacta.

### Named Rules
**A Regra do Sinal Raro.** Ciano, vermelho e âmbar só aparecem onde há estado ou ação. Nenhuma superfície, borda de painel ou ornamento usa um sinal "porque fica bonito". Se o quadro inteiro está parado, a única coisa ciano na tela é o botão "Novo projeto".

**A Regra da Cor Chapada.** Sinais são preenchimentos planos. Sem gradiente, sem `text-shadow`, sem halo luminoso, sem brilho interno.

## Typography

**Display Font:** Barlow Semi Condensed (com sans-serif)
**Body Font:** Barlow (com sans-serif)
**Label/Mono Font:** JetBrains Mono (com monospace), só para dados

**Character:** uma família de anuário técnico: Barlow para ler, a versão Semi Condensed para rotular e titular em caixa alta espaçada, como as letras de uma mesa de controle. JetBrains Mono entra só onde o texto é de máquina.

As três famílias são self-hosted no app via `@fontsource` (`@fontsource/barlow`, `@fontsource/barlow-semi-condensed`, `@fontsource/jetbrains-mono`), porque o WebView2 pode estar offline. O app não carrega Google Fonts por `<link>`; o protótipo descartável só fazia isso por conveniência. Pesos usados: Barlow 400/500/600, Barlow Semi Condensed 600, JetBrains Mono 400/500/700. Todo o app usa algarismos tabulares (`font-variant-numeric: tabular-nums`) para que tempos e contagens não dancem.

### Hierarchy
- **Title** (600, 20px, 1.2): nome do projeto no cabeçalho da transcrição, "Novo projeto"/"Editar projeto", título do estado vazio.
- **Brand** (600, 15px, 0.08em, caixa alta): só o nome "Bat-Computer" na barra superior.
- **Strip name** (Barlow 600, 15px): nome do projeto na faixa, com reticências.
- **Body** (400, 14px, 1.4): texto corrido, notas, opções do seletor de comando.
- **Control** (500, 13px): rótulos de botão, resumo da barra ("2 ativos · 1 em falha · 2 em espera"), itens de menu, voltar.
- **Bay label** (Semi Condensed 600, 12px, 0.14em, caixa alta): nome da baia (ATIVOS, FALHA, EM ESPERA) e cabeçalho LOG.
- **Cell label** (Semi Condensed 600, 11px, 0.12em, caixa alta): texto de estado na faixa (RODANDO, ERRO, PARADO, LIGANDO) e rótulos dos campos do formulário.
- **Fact label** (Semi Condensed 600, 10.5px, 0.12em, caixa alta): rótulos do grid de fatos (ESTADO, NO AR HÁ, COMANDO, ENDEREÇO).
- **Mono data** (400, 12px): tempo no ar, "código 1", contagem da baia (500), valores do grid de fatos, "17 / 1000 linhas" (11px).
- **Mono command** (400, 11.5px): comando sob o nome na faixa, caminho na transcrição.
- **Mono input** (400, 12.5px): campos de pasta, comando livre e endereço. O campo Nome usa Barlow 14px, porque nome é texto de gente.
- **Log** (400, 12px, 1.6) e **Log tag** (700, 10px): ver Componentes.
- **Mini brand** (Semi Condensed 600, 11px, 0.08em, caixa alta): "BAT-COMPUTER" no cabeçalho da coluna compacta.
- **Mini bay label** (Semi Condensed 600, 10px, 0.14em, caixa alta) e **Mini count** (mono 500, 10.5px): nome e contagem da baia na coluna compacta.
- **Mini name** (Barlow 600, 12.5px): nome do projeto na faixa compacta, numa linha só, ocupando a célula do meio e cortado com reticências. A faixa compacta não escreve o estado nem o tempo no ar: o estado é dito pela forma, pela cor do suporte e pela baia, e por extenso no title e num texto só para leitores de tela.
- **Alert count** (mono 700, 10.5px): número do contador de falha ▲N.

### Named Rules
**A Regra do Mono de Máquina.** JetBrains Mono só em comando, caminho, endereço, tempo, código de saída, contagem e log. Rótulos, títulos, botões, estados e mensagens são Barlow. Se uma pessoa escreveu a frase, ela não é mono.

**A Regra da Caixa Alta Rotulada.** Caixa alta espaçada é exclusiva da Semi Condensed e só para nomes de baia, estado e rótulo de campo/fato. Nunca em frase, botão ou título.

## Layout

A janela tem duas formas, e o quadro é a constante.

**Janela média (880×580).** Barra superior de 44px atravessando tudo. Abaixo, duas colunas: o quadro com largura fixa de 430px à esquerda e a transcrição (ou o formulário) com o resto da largura à direita, separada por uma régua de 1px. O projeto selecionado é sempre mostrado na transcrição; o formulário substitui a transcrição no mesmo lugar. Com zero projetos, o quadro ocupa a janela inteira com o estado vazio.

**Janela pequena (480×640).** Só o quadro, em largura total. A transcrição e o formulário viram telas inteiras com um botão "Quadro" (seta de voltar) acima do título. A barra superior esconde o resumo e o relógio e deixa só marca, nome e "Novo projeto" alinhado à direita.

**Quadro.** Respiro de 12px nas laterais e topo (18px no pé). As três baias empilham com 16px entre si; cada baia tem um cabeçalho de 20px (rótulo, contagem em mono, régua até a borda) e 6px até as faixas; as faixas empilham com 4px entre si. Ordem fixa das baias: ATIVOS, FALHA, EM ESPERA. Baia vazia mostra uma caixa tracejada de 32px com uma frase curta ("Nenhum projeto rodando.", "Nenhuma falha.", "Nada em espera."), para a baia nunca desaparecer.

**Faixa.** 48px de altura, grid de células divididas por régua de 1px: suporte de 30px, identificação (nome + comando, flexível), célula de estado (104px na janela média, 100px na pequena) e ações (abrir no navegador, ligar/desligar, mais). Quando "abrir no navegador" não se aplica, o lugar fica reservado (30px) para os botões não pularem. A porta não ganha coluna própria; o endereço vive no grid de fatos da transcrição.

**Transcrição.** Cabeçalho com 12px/14px de respiro: título à esquerda, ações à direita (Ligar/Desligar com rótulo, abrir no navegador, editar, apagar), caminho em mono na linha de baixo. Depois um grid 2×2 de fatos (Estado, No ar há / Saiu com / Tempo no ar, Comando, Endereço), o cabeçalho LOG com a contagem de linhas, e o log ocupando o resto da altura até a borda. Paineis laterais usam 14px de respiro horizontal.

**Coluna compacta (236×170 por padrão).** A mesma janela encolhe para uma coluna sem moldura que mora num canto da tela (no Tauri: `decorations` desligado). O usuário a redimensiona de 200×110 até 420×640 (no Tauri, janela redimensionável com esses mínimo e máximo), e o app lembra o último tamanho. Dois andares: um cabeçalho de 32px e a lista com o resto da altura. O cabeçalho (respiro 0 3px 0 7px, régua inferior de 1px) traz à esquerda a marca de 15px em ciano e "BAT-COMPUTER" em Mini brand, que juntos são a região de arrastar a janela (`data-tauri-drag-region` no cabeçalho e na alça); à direita, colados, o contador ▲N (só com falha), "+" (novo projeto), alfinete e expandir.

**Lista da coluna.** Respiro de 3px em cima, 5px nas laterais e 6px no pé; faixas a 2px umas das outras. As baias seguem a ordem ATIVOS, FALHA, EM ESPERA, mas só aparecem as que têm faixas (o espaço é curto demais para caixas vazias). Cada baia abre com um cabeçalho de 18px (rótulo, contagem, régua com tiques até a borda), 4px abaixo da faixa anterior (2px na primeira). A lista rola na vertical; quando há conteúdo fora de vista, a borda correspondente (cima, baixo ou as duas) se apaga num esmaecimento de 28px (máscara sobre o conteúdo, não cor de superfície). Uma faixa torta é rolada até o meio da lista sempre que estiver sob um esmaecimento ou fora de vista.

**Voltar ao tamanho.** Ao entrar no compacto, o app lembra o tamanho anterior (média, por padrão). Clicar no nome de uma faixa abre esse tamanho já na transcrição do projeto (endireitando a faixa, se torta); o ▲N abre a primeira falha, endireitada; expandir volta ao quadro; "+" volta direto no formulário novo. Sem projetos, a lista mostra, centralizados, "Nenhum projeto ainda." em tinta calada (Barlow 12.5px) e o botão primário "Cadastrar projeto", que também volta ao tamanho anterior no formulário.

**Teclado.** ↑↓ salta entre faixas na ordem visual das baias (e endireita uma faixa torta), S liga/desliga a selecionada, N abre o formulário novo, Esc fecha confirmação e formulário.

## Elevation & Depth

O sistema é plano. A profundidade é tonal, em quatro degraus de azul-ardósia: chão do radar (afundado: janela, log, campos), rack (barra e painel), face da faixa (placas) e face erguida (hover, seleção, controles). Cada degrau é delimitado por linha de 1px, não por sombra. A única sombra pertence ao que flutua de fato sobre o quadro: o menu de "mais ações" e o toast. A coluna compacta é a própria janela e não desenha sombra: é rack com contorno line de 1px.

### Shadow Vocabulary
- **Flutuante** (`box-shadow: 0 10px 28px rgba(0,0,0,.55)`): menu contextual e toast. Nada mais.

### Named Rules
**A Regra do Tom Antes da Sombra.** Para destacar uma superfície, suba um degrau de tom e troque a linha (rule para line). Sombra só para o que sai do plano do quadro.

## Shapes

Cantos quase retos: 3px em faixas, botões, campos, caixas de nota, menu e grid de fatos; 2px nos dois cantos esquerdos do suporte, que encosta na borda da faixa. A forma recorrente é a placa retangular dividida em células por linhas de 1px, como uma faixa de papel de controle de voo. Vazios e prévias usam contorno tracejado de 1px (baia vazia, faixa-fantasma do estado vazio, prévia da faixa no formulário). A régua da baia é uma linha de 1px com marcas verticais a cada 12px (5px de altura); na coluna compacta, a mesma linha com marcas de 4px.

**As formas de status** (12×12, no suporte, na cor de tinta sobre o sinal):
- **RODANDO:** losango cheio.
- **ERRO:** triângulo cheio.
- **PARADO:** anel (traço 1.6).
- **Em trânsito:** losango vazado (traço 1.6), anunciando o losango cheio que vem.

A mesma forma aparece no grid de fatos ao lado do texto de estado, na cor do sinal. Na faixa compacta e no contador ▲N, a forma encolhe para 9×9.

## Components

### Faixa (componente-assinatura)
Uma placa plana que diz tudo de um projeto em 48px.
- **Repouso:** fundo strip-face, contorno rule, cantos 3px, células divididas por rule.
- **Hover:** fundo strip-face-raised, contorno line (transição de 0.15s).
- **Selecionada:** fundo strip-face-raised, contorno ciano a 60%. É também o foco do teclado (`role="button"`, Enter/Espaço abrem).
- **Identificação:** nome em Barlow 600 15px (tinta), comando em mono 11.5px (tinta calada), ambos com reticências.
- **Ações:** botões-ícone transparentes de 30px em tinta calada; Ligar em ciano; hover com fundo radar-ground e contorno line.

**Tratamento por status:**

| Status | Baia | Suporte | Forma | Texto de estado | Célula de tempo |
|---|---|---|---|---|---|
| RODANDO | ATIVOS (rótulo ciano) | signal-cyan, forma on-cyan | losango cheio | "Rodando" em ciano | tempo no ar `hh:mm:ss` em mono, tinta, ao vivo |
| ERRO | FALHA (rótulo vermelho) | fault-red, forma on-red | triângulo cheio | "Erro" em vermelho | "código N" em mono, tinta |
| PARADO | EM ESPERA (rótulo calado) | slate-holder, forma slate-ink | anel | "Parado" em slate-ink | "—" em mono, tinta apagada |
| Em trânsito | fica na baia de origem até assentar | transit-amber, forma on-amber | losango vazado | "Ligando" / "Desligando" em âmbar | mantém o valor anterior |

Durante o trânsito, o botão de ligar/desligar fica desabilitado (opacidade 0.45) e seu rótulo vira "Ligando…" / "Desligando…". Quando o processo assenta, a faixa troca de baia.

**Faixa torta (falha não vista).** Quando um projeto cai para ERRO sem o usuário estar olhando, a faixa entra na baia FALHA recuada 12px para a direita (largura máxima reduzida no mesmo valor), como uma faixa de papel posta torta no trilho para chamar o controlador. Ela se endireita assim que o usuário a abre ou chega nela com ↑↓. É o único aviso de falha: sem pulso, sem piscar.

### Coluna compacta
A janela pequena encolhida: baias e faixas de sempre, menores, numa coluna que rola.
- **Coluna:** fundo rack, contorno line de 1px em volta, sem sombra. `role="region"` com o nome "Bat-Computer compacto".
- **Cabeçalho:** 32px, régua inferior em rule. Marca de 15px em ciano e "BAT-COMPUTER" em Mini brand (tinta), com 6px de vão, ocupando o espaço livre como alça de arrastar (cursor de agarrar).
- **Botões do cabeçalho:** botões-ícone de 24px com ícone de 16px. Repouso transparente em tinta calada; hover em strip-face-raised com contorno line e tinta.
- **Alfinete:** ligado, ícone ciano, borda ciano a 45%, fundo ciano a 8%. Liga e desliga "sempre por cima" da janela e reflete o estado em `aria-pressed`; o title alterna entre "Fixar no topo" e "Soltar do topo".
- **Contador de falha ▲N:** 18px de altura, respiro 0 5px, cantos 3px, fundo fault-red, triângulo de 9px e número em Alert count, ambos em on-red. Só existe com N > 0; clicar abre a primeira falha expandida, já endireitada.
- **Cabeçalho de baia:** 18px, rótulo em Mini bay label (ciano em ATIVOS, vermelho em FALHA, tinta calada em EM ESPERA), contagem em Mini count (tinta) e a régua com tiques, 5px de vão entre os três.
- **Faixa compacta:** 26px de altura, grid de três células (suporte de 20px, nome flexível, botão de 26px) divididas por rule; fundo strip-face, contorno rule, cantos 3px. O suporte usa as mesmas cores e formas da faixa grande, com a forma em 9px. O nome é um botão (respiro 0 7px, hover em strip-face-raised) cujo title traz nome e estado; um texto só para leitores de tela repete o estado. Sem tempo no ar e sem palavra de estado visível. O botão ligar/desligar é transparente em tinta calada (Ligar em ciano), ícone de 14px, hover com fundo radar-ground; desabilitado durante o trânsito.
- **Faixa torta compacta:** a falha não vista recua 8px para a direita (em vez de 12px), a lista rola até ela, e ela se endireita quando aberta.
- **Vazio:** "Nenhum projeto ainda." em Barlow 12.5px tinta calada e o botão primário "Cadastrar projeto", centralizados.

### Barra superior
- 44px, fundo rack, régua inferior de 1px.
- Marca (glifo de três faixas empilhadas com o primeiro suporte cheio, 18px, ciano), "BAT-COMPUTER" em Brand, resumo em Control (tinta calada), relógio em mono 12px (tinta apagada) empurrado à direita, botão primário "Novo projeto".
- Na janela pequena: só marca, nome e botão.

### Botões
- **Forma:** cantos 3px, altura 30px, respiro 0 12px, ícone de 16px + rótulo com 6px de vão; ícone sozinho em 30×30.
- **Padrão:** fundo strip-face-raised, contorno line, tinta. Hover: control-hover com contorno control-hover-line.
- **Ligar (go):** tinta ciano, contorno ciano a 45%; hover com fundo ciano a 10% e contorno ciano cheio. Desligar usa o botão padrão com ícone de quadrado.
- **Primário:** fundo e contorno signal-cyan, texto on-cyan em 600. Hover: signal-cyan-bright. Um por tela: "Novo projeto", "Salvar", "Adicionar ao quadro", "Cadastrar o primeiro projeto".
- **Perigo:** ícone/texto em vermelho sobre o botão padrão (apagar); a confirmação usa fundo fault-red com texto on-red em 600.
- **Foco:** anel de 1px em ciano com 2px de afastamento, em todos os controles.
- **Desabilitado:** opacidade 0.45, sem hover.

### Campos
- **Estilo:** 32px, fundo radar-ground (afundado), contorno line, cantos 3px, respiro 9px, mono 12.5px (Nome em Barlow 14px). Placeholder em tinta apagada; cursor ciano.
- **Foco:** contorno passa a signal-cyan, sem halo.
- **Desabilitado:** opacidade 0.5 (edição bloqueada enquanto o projeto roda, com a nota âmbar "Este projeto está rodando. Desligue-o para editar." e um botão Desligar dentro dela).
- **Rótulos:** Cell label em tinta calada; "opcional" em Barlow 12px apagado, sem caixa alta.
- **Seletor de comando:** lista com contorno line, linhas de 32px divididas por rule; marcador redondo de 12px com contorno apagado, que vira contorno ciano com miolo ciano quando escolhido; linha escolhida em strip-face-raised.
- **Prévia:** o formulário mostra no topo a faixa como ela vai aparecer, com contorno tracejado, atualizando nome e comando ao digitar.

### Notas e confirmação
- **Nota de trânsito/bloqueio:** contorno âmbar a 50%, fundo âmbar a 6%, texto âmbar, ícone de cadeado.
- **Nota de erro:** contorno vermelho a 55%, fundo vermelho a 7%, texto fault-red-text.
- **Confirmar apagar:** faixa inline sob o cabeçalho da transcrição (não um modal), mesmas cores da nota de erro, com Cancelar e Apagar (perigo preenchido). Se o projeto está rodando, o texto avisa que o processo será desligado antes.

### Log
A transcrição é o motivo de abrir um projeto; ela tem de ler bem.
- **Superfície:** fundo radar-ground, régua superior de 1px, mono 12px com entrelinha 1.6, rolagem própria que gruda no fim enquanto o usuário está no fim.
- **Anatomia da linha:** grid de duas colunas: 104px para o horário (`hh:mm:ss` em tinta apagada) seguido da tag, e o texto no resto, com quebra em qualquer ponto (`overflow-wrap: anywhere`) e recuo pendente sob o texto, nunca sob o horário. Respiro lateral de 14px.
- **Linha normal:** texto em tinta, sem tag.
- **Linha ERR:** fundo vermelho a 7%, tag "ERR" (mono 700 10px, fault-red) depois do horário, texto em fault-red-text.
- **Linha SYS** (mensagens do próprio Bat-Computer, como "[processo encerrado com código 1]"): tag "SYS" em âmbar, texto em âmbar, sem fundo.
- **Vazio:** frase em Barlow 13px apagada, centralizada ("Nada por aqui ainda. Ligue o projeto para ver a saída do processo.").
- **Cabeçalho:** "LOG" em Bay label e "N / 1000 linhas" em mono 11px apagado.

### Grid de fatos
Uma placa strip-face 2×2 com réguas de 1px entre as células; rótulo em Fact label apagado sobre o valor (mono 12px tinta). A célula de Estado repete a forma de status e o texto na cor do sinal.

### Menu e toast
Fundo strip-face-raised, contorno line, cantos 3px, sombra Flutuante. Itens do menu em Barlow 13px com ícone (Ver log, Editar, Apagar em vermelho), hover em `#1F3340`.

### Ícones
Desenhados para o app, em SVG próprio: grade de 16×16, sem preenchimento, traço de 1.5 com pontas e junções arredondadas, cor herdada do texto. Conjunto atual: ligar (play), parar (quadrado), abrir fora, mais (três pontos), editar, apagar, voltar, mais/novo, pasta, confirmar, cadeado, log, alfinete e expandir (duas setas para cantos opostos). Ícone novo segue a mesma grade e o mesmo traço; nada de biblioteca de ícones nem fonte de ícones.

### Movimento
- **Assinatura:** ao mudar de estado, a faixa desliza da posição antiga para a nova baia (FLIP, 300ms, `cubic-bezier(.16,1,.3,1)`); ao pousar, o suporte dá um único brilho (`brightness(1.7)` → normal, 600ms, começando 200ms depois, ease-out). Na coluna compacta, o mesmo FLIP desliza a faixa até a nova baia.
- **Nunca através de uma troca de tamanho:** ao entrar ou sair do compacto (ou trocar entre média e pequena), as faixas aparecem direto no lugar novo; o deslizar só acontece dentro do mesmo tamanho.
- **Micro:** hover de faixa e botão em 0.15s (fundo e contorno).
- **Desligado** quando os efeitos estão desligados ou com `prefers-reduced-motion: reduce`: a faixa simplesmente aparece na baia nova.
- Nenhuma animação em loop: sem pulso no status, sem cintilar, sem varredura de radar.

## Do's and Don'ts

### Do:
- **Do** pôr o status em três canais ao mesmo tempo: baia, cor+forma do suporte e texto.
- **Do** manter as três baias na ordem ATIVOS, FALHA, EM ESPERA; no quadro inteiro, sempre visíveis, com caixa tracejada quando vazias; na coluna compacta, só as que têm faixas.
- **Do** usar 48px para a faixa, 44px para a barra superior, 30px para controles, 32px para campos e 430px para o quadro na janela média; na coluna compacta, 236×170 por padrão (de 200×110 a 420×640), 32px para o cabeçalho, 18px para o cabeçalho de baia, 26px para a faixa e 24px para os botões do cabeçalho.
- **Do** marcar uma falha não vista entortando a faixa 12px (8px na coluna compacta), e endireitá-la quando o usuário a vê.
- **Do** rolar a coluna compacta até a faixa torta, para que ela nunca fique sob o esmaecimento de 28px.
- **Do** separar células e superfícies com linhas de 1px (rule, line) e subir um degrau de tom para destacar.
- **Do** usar algarismos tabulares em tudo e JetBrains Mono só em comando, caminho, endereço, tempo, código, contagem e log.
- **Do** self-hostear Barlow, Barlow Semi Condensed e JetBrains Mono via `@fontsource`.
- **Do** desenhar ícones novos em 16×16 com traço de 1.5, pontas arredondadas e `currentColor`.
- **Do** desligar o deslizar e o brilho do suporte com efeitos desligados ou `prefers-reduced-motion`, e nunca deslizar através de uma troca de tamanho da janela.

### Don't:
- **Don't** usar marcas da DC: nada de símbolo do morcego, das palavras "Batman", "Batmobile", "Gotham City", de logos de filmes nem dos glifos do Charada.
- **Don't** pôr halo, brilho, `text-shadow` luminoso, glow interno ou gradiente em sinais e superfícies.
- **Don't** usar mono fora de código e dado (nada de botões, rótulos, títulos ou mensagens em mono).
- **Don't** usar bordas laterais coloridas com mais de 1px como decoração; o suporte de 30px é uma célula preenchida com forma, não uma borda.
- **Don't** animar em loop: sem pulso de status, sem cintilação, sem scanline.
- **Don't** trocar o quadro por um grid de cards ou por uma lista com badges de status.
- **Don't** usar ciano, vermelho ou âmbar fora de estado e ação.
- **Don't** usar sombra fora do menu e do toast.
- **Don't** carregar fontes por `<link>` do Google Fonts no app.
- **Don't** escrever o estado nem o tempo no ar na faixa compacta; o estado é forma, cor do suporte e baia, com a palavra só no title e para leitores de tela.
