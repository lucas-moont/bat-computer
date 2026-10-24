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

Apagar pede confirmação e para o processo antes, se ele estiver rodando.

Visual: tema "Batcomputador", com fundo quase preto, acentos ciano/âmbar, fonte monoespaçada, cantos retos e brilho sutil nos status. Sem marcas registradas.

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
