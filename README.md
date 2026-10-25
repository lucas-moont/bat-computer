# Bat-Computer

Um "quadro de luz" para os seus projetos pessoais no Windows. Em vez de abrir o cmd, entrar na pasta e digitar `npm run dev`, cada projeto vira uma linha numa lista com um botão Start/Stop. Tema Batcomputador.

> **Status:** em planejamento. Ainda não há código; o design está pronto e a implementação vai começar.

## O que ele faz (v1)

- Cadastrar projetos com nome, caminho da pasta, comando de start e URL opcional
- Detectar os scripts do `package.json` (`npm run dev`, `npm run electron`...) ou aceitar qualquer comando
- Start/Stop com status PARADO / RODANDO / ERRO, sem janelas de cmd espalhadas
- Logs ao vivo na tela de detalhes de cada projeto
- Editar, apagar e abrir o projeto no navegador
- Fechar o Bat-Computer encerra tudo o que ele ligou, inclusive em crash

## Stack

[Tauri 2](https://tauri.app) (backend em Rust) + React + TypeScript + Vite.

## Documentação

- Design: [`docs/plans/2026-10-24-bat-computer-design.md`](docs/plans/2026-10-24-bat-computer-design.md)
- Identidade visual: [`DESIGN.md`](DESIGN.md) (produto em [`PRODUCT.md`](PRODUCT.md))

## Licença

[MIT](LICENSE)
