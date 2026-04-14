# Integracao Jira

Automacao independente para Jira Cloud com dois pontos de uso:

- CLI local para criar, editar e organizar issues
- extensao de VS Code para operar o Jira sem sair do editor

## O que a solucao faz

- valida conexao com Jira Cloud
- descobre automaticamente os tipos corretos do projeto
- cria epics, issues e subtasks
- atualiza resumo, descricao e labels
- comenta, atribui responsavel e move status
- cria links entre issues
- aplica planejamento em lote via JSON
- empacota a extensao VS Code em `.vsix`

## Estrutura

- `scripts/`: CLI e exemplos de plano
- `docs/`: documentacao detalhada
- `vscode-extension/`: extensao VS Code empacotavel

## Setup rapido

1. Copie `.env.example` para `.env.local`
2. Preencha:
   - `JIRA_BASE_URL`
   - `JIRA_EMAIL`
   - `JIRA_API_TOKEN`
   - `JIRA_PROJECT_KEY`
3. Valide a conexao:

```bash
npm run jira:check
```

Para trocar de projeto no mesmo Jira Cloud, normalmente basta alterar `JIRA_PROJECT_KEY`.

## CLI

Exemplos:

```bash
npm run jira -- help
npm run jira -- project:info
npm run jira -- issue:create --summary "Nova issue"
npm run jira -- issue:update KAN-123 --summary "Novo resumo"
npm run jira -- comment:add KAN-123 --body "Atualizacao"
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

## Releases

O repositório possui workflow em `.github/workflows/release.yml`.

- em `push` para `main`, ele gera o `.vsix` como artifact
- em tags `v*`, ele publica uma GitHub Release com o `.vsix` anexado

## Documentacao

Veja [docs/jira-workflow.md](./docs/jira-workflow.md).
