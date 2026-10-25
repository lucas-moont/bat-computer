# Bat-Computer: design

Data: 2026-10-24

## Problema

Para rodar cada projeto pessoal, hoje é preciso abrir o cmd, entrar na pasta e digitar o comando (`npm run dev`, `npm run electron`...). O Bat-Computer é um app desktop instalado no Windows que centraliza isso: uma lista de projetos, cada um com um botão de Start/Stop.

## Escopo da v1

- Cadastrar projeto: nome, caminho da pasta, comando de start, URL (opcional).
- Editar e apagar projetos.
- Start/Stop por projeto, com status: PARADO, RODANDO ou ERRO.
- Logs visíveis só na tela de detalhes do projeto.
- Botão "Abrir no navegador" quando o projeto tem `url` e está rodando.
- Fechar o Bat-Computer para todos os projetos que ele iniciou.
- Modo compacto: a mesma janela encolhe para uma coluna pequena e redimensionável, com Start/Stop, status e aviso de falha; um alfinete opcional a mantém por cima das outras janelas.

Fora do escopo: bandeja do sistema, iniciar com o Windows, abrir pasta/VS Code, detecção automática de URL nos logs, health check HTTP.

## Arquitetura

Tauri 2 com React + TypeScript (Vite). A escolha por Tauri em vez de Electron foi por consumo de RAM (~30-60MB contra ~150MB) e porque o Job Object do Windows é simples de usar em Rust. O projeto deve evoluir pouco, então manter a parte de processos em Rust é aceitável.

- **Frontend (React):** só interface. Chama o backend via `invoke(...)` e escuta eventos.
- **Backend (Rust):**
  - `store.rs`: CRUD do `projects.json` no diretório de dados do app (`%APPDATA%\com.batcomputer.app\`), com `serde_json`.
  - `scripts.rs`: lê `package.json` de uma pasta e devolve a lista de scripts.
  - `process.rs`: gerencia os processos.
    - Start: `cmd /C <command>` com `current_dir = path` e `CREATE_NO_WINDOW`.
    - Cada processo é associado a um Job Object com `JOB_OBJECT_LIMIT_KILL_ON_JOB_CLOSE`, para que todos os filhos morram quando o Bat-Computer fechar ou crashar.
    - stdout e stderr são lidos por threads e guardados num ring buffer de 1000 linhas por projeto.
    - Stop: `taskkill /PID <pid> /T /F`.
    - Mudanças de status e novas linhas de log viram eventos para o frontend.

### Commands (frontend → backend)

`list_projects`, `add_project`, `update_project`, `delete_project`, `read_scripts(path)`, `start_project(id)`, `stop_project(id)`, `get_logs(id)`, `open_url(url)`.

### Eventos (backend → frontend)

`project-status { id, status, exitCode? }`, `project-log { id, line, stream }`.

### Modelo de dados

```json
{
  "id": "uuid",
  "name": "Meu App",
  "path": "C:\\Projetos\\meu-app",
  "command": "npm run dev",
  "url": "http://localhost:5173"
}
```

O status não é persistido. Ao abrir o app, todos os projetos começam como PARADO.

## Telas

1. **Lista principal:** uma linha por projeto com status, nome, comando, Start/Stop, 🌐 (se houver `url` e o projeto estiver rodando) e menu `⋯` (Editar, Apagar). Clicar na linha abre os detalhes. Há um estado vazio com chamada para "+ ADICIONAR".
2. **Detalhes:** cabeçalho com dados e ações, e o painel de logs com auto-scroll. Sair dos detalhes não para o processo.
3. **Formulário (adicionar/editar):** nome, caminho (colar ou "Procurar..."), comando (lista de scripts do `package.json` + "Outro comando..." livre; só campo livre se não houver `package.json`), URL opcional. A edição fica bloqueada enquanto o projeto está rodando.

4. **Modo compacto:** a janela encolhe para uma coluna (236×170, redimensionável) com uma faixa por projeto: ícone de estado, nome e Start/Stop. Expandir volta ao tamanho anterior, já no log do projeto clicado.

Apagar pede confirmação e para o processo antes, se ele estiver rodando.

Visual: ver "Direção visual escolhida" abaixo.

## Direção visual escolhida

Decidida na LUC-119, com protótipo descartável no galho `prototype/luc-119-identidade-visual`. A referência completa (tokens, componentes, regras) está em `DESIGN.md`, e a pesquisa de referências em `docs/research/2026-10-24-referencias-visuais-batcomputador.md`.

**Quadro de Faixas.** Cada projeto é uma faixa de controle de tráfego aéreo encaixada na baia do seu estado: ATIVOS, FALHA, EM ESPERA. A posição é o status. É uma sala escura e tática na linha ciano do Batcomputador, com cor chapada: sem brilho, sem pulso, sem marcas da DC.

### Paleta

| Papel | Hex |
|---|---|
| Fundo (sala de radar) | `#070B0E` |
| Painéis laterais / barra superior | `#0A1216` |
| Face da faixa | `#111C22` (hover/selecionada `#16252E`) |
| Régua fina / linha de controle | `#1C2B33` / `#263943` |
| Texto / texto calado / texto apagado | `#DCEBF2` / `#8CA3B0` / `#7A93A3` |
| Sinal (RODANDO, ação primária, foco) | `#3FD8FF` (hover `#86E8FF`) |
| Falha (ERRO) | `#FF5C4D` (texto de log `#FF9A90`) |
| Trânsito (Ligando…/Desligando…) | `#F2B33D` |
| Suporte PARADO / tinta | `#2A3A43` / `#A9BCC7` |
| Tinta sobre ciano / vermelho / âmbar | `#03141B` / `#1A0402` / `#1A1203` |

### Fontes

- **Barlow** (interface) e **Barlow Semi Condensed** (títulos, rótulos em caixa alta).
- **JetBrains Mono** só para dado de máquina: comando, caminho, tempo, contagens e log.
- No app, as três ficam empacotadas via `@fontsource`, nunca carregadas por `<link>` do Google Fonts.

### Tratamento de cada status

Cada status é dito três vezes: pela baia, pela forma no suporte e pela palavra.

| Status | Baia | Suporte (cor + forma) | Texto |
|---|---|---|---|
| RODANDO | ATIVOS | ciano, losango cheio | "Rodando" + tempo no ar |
| ERRO | FALHA | vermelho, triângulo cheio | "Erro" + código de saída |
| PARADO | EM ESPERA | ardósia, anel | "Parado" |
| Ligando… / Desligando… | fica na baia de origem | âmbar, losango vazado | botão desabilitado |

- **Falha não vista:** a faixa fica "torta", deslocada 12px no quadro e 8px na coluna compacta, até o usuário abri-la.
- **Ligar/desligar:** a faixa desliza para a nova baia em ~300ms. Isso some com "efeitos contidos" ou com `prefers-reduced-motion`.

### Densidade

| Elemento | Medida |
|---|---|
| Barra superior | 44px |
| Faixa (quadro) | 48px |
| Controles | 30px |
| Campos | 32px |
| Quadro na janela média | 430px de largura fixa, log com o resto |
| Coluna compacta | 236×170 (200×110 a 420×640) |
| Faixa compacta | 26px |
| Cabeçalho da coluna | 32px |

- **Janela média (880×580):** o quadro à esquerda e o log ou formulário à direita.
- **Janela pequena (480×640):** só o quadro; o log e o formulário viram telas próprias.

## Tratamento de erros

| Situação | Comportamento |
|---|---|
| Caminho inexistente no cadastro | Erro de validação, não salva |
| Pasta sumiu antes do Start | Status ERRO, mensagem no log |
| Processo sai com código ≠ 0 | Status ERRO, logs preservados |
| Processo sai com código 0 | Status PARADO |
| Start duplo | Botão desabilitado durante a transição; backend ignora Start de projeto já rodando |
| `projects.json` corrompido | Renomeia para `projects.json.bak`, abre com lista vazia e mostra aviso |
| App fecha ou crasha | Job Object encerra todos os filhos |

RODANDO significa "processo vivo", não "servidor respondendo".

## Testes

- **Rust (`cargo test`):** store (CRUD, arquivo corrompido), scripts (com/sem scripts, sem arquivo, JSON inválido), process (start real de um comando longo, logs chegando, stop matando a árvore, comando que falha → ERRO), ring buffer (limite de 1000 linhas).
- **React (`vitest`):** validação do formulário, lista de scripts, renderização dos status na lista.
- **Manual:** cadastrar 2 ou 3 projetos reais, start/stop, fechar o app e conferir no Gerenciador de Tarefas que não sobrou `node.exe` órfão.

## Distribuição

`tauri build` gera um instalador NSIS/MSI. Pré-requisitos já presentes na máquina: Rust stable MSVC, VS 2022 C++ tools, WebView2.
