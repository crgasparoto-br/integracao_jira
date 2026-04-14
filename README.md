# Integracao Jira

Projeto independente para operar Jira Cloud via:

- CLI em `scripts/jira-cli.mjs`
- extensao de VS Code em `vscode-extension`

## Estrutura

- `scripts/`: CLI e exemplos de plano
- `docs/`: documentacao de uso
- `vscode-extension/`: extensao VS Code empacotavel em `.vsix`

## Setup rapido

1. Copie `.env.example` para `.env.local`
2. Preencha:
   - `JIRA_BASE_URL`
   - `JIRA_EMAIL`
   - `JIRA_API_TOKEN`
   - `JIRA_PROJECT_KEY`
3. Valide:

```bash
npm run jira:check
```

## Comandos

```bash
npm run jira -- help
npm run jira -- project:info
npm run jira -- issue:create --summary "Nova issue"
npm run jira -- issue:update KAN-123 --summary "Novo resumo"
npm run jira -- issue:assign KAN-123 --account-id "<account-id>"
npm run jira -- issue:link-types
npm run jira -- issue:link KAN-123 KAN-456 --type Blocks
npm run jira -- plan:apply --file scripts/jira-plan.example.json --dry-run
```

## Extensao VS Code

A extensao fica em `vscode-extension` e pode ser empacotada com:

```bash
npm run extension:package
```

O `.vsix` sera gerado dentro de `vscode-extension/`.

## Documentacao

Veja [docs/jira-workflow.md](./docs/jira-workflow.md).
