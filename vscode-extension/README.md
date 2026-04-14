# Integracao Jira

Extensao local de VS Code para operar o Jira Cloud do projeto usando o CLI em `scripts/jira-cli.mjs`.
Ela leva um CLI proprio empacotado e nao depende do monorepo original.

## O que faz

- valida conexao com o Jira
- mostra informacoes do projeto atual
- cria epics, issues e subtasks
- atualiza issue existente
- adiciona comentarios
- atribui responsavel
- cria links entre issues
- move status
- executa busca JQL
- aplica plano JSON em lote

## Como usar localmente

1. Abra esta pasta no VS Code:

   `vscode-extension`

2. Pressione `F5` para abrir uma janela de Extension Development Host.
3. Na nova janela, abra qualquer workspace em que voce queira usar a integracao.
4. Use o Command Palette:
   - `Integracao Jira: Menu`
   - `Integracao Jira: Check Connection`
   - `Integracao Jira: Create Epic`
   - `Integracao Jira: Create Issue`
   - `Integracao Jira: Update Issue`
   - `Integracao Jira: Assign Issue`
   - `Integracao Jira: Link Issues`

## Configuracoes

- `integracaoJira.nodePath`
- `integracaoJira.cliPath`
- `integracaoJira.projectKey`
- `integracaoJira.planFilePath`

Se `integracaoJira.projectKey` estiver vazio, a extensao usa o projeto definido no `.env.local`.

## Empacotar

```bash
cd vscode-extension
npm install
npm run package
```

Isso gera um `.vsix` instalavel no VS Code.
