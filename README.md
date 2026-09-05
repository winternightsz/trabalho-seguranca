# Trabalho 1 - Case Prático 1 (OWASP Juice Shop)

Disciplina: Segurança de Sistemas Computacionais - UNIVALI 2026/2
Prof. Ramicés dos Santos Silva

## O que é

Este repositório contém a avaliação de vulnerabilidades realizada sobre a aplicação
intencionalmente vulnerável **OWASP Juice Shop**, conforme roteiro do Trabalho 1 (Case
Prático 1). Foram identificadas e documentadas 6 categorias de vulnerabilidades do
OWASP Top 10:2021: **A01, A02, A03, A05, A07 e A09**.

## Estrutura do repositório

```
scripts/       comandos utilizados (Docker, curl, exploração)
evidencias/    prints de cada vulnerabilidade e das pontuações CVSS
```

## Como subir o ambiente

O ambiente foi executado em um GitHub Codespaces, com o alvo rodando em Docker:

```bash
docker run --rm -d -p 3000:3000 --name juiceshop bkimminich/juice-shop
```

Verificar se está rodando:

```bash
docker ps
```

## Como acessar a aplicação

Após subir o contêiner, acesse pela porta 3000 encaminhada automaticamente pelo
Codespaces: na aba **PORTS** do VS Code, clique no ícone de globo ao lado da porta
3000 para abrir a URL pública (padrão `https://<nome-do-codespace>-3000.app.github.dev`).

## Todos os comandos usados

Ver arquivo `scripts/comandos.md`.

