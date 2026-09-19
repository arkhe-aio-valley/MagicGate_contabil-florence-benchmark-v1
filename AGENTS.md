# AGENTS.md — Florence Benchmark v1

Este repositório é um benchmark determinístico multiagente. Estas regras valem para qualquer IA, IDE agent, runner ou automação que opere aqui.

## Modelo de acesso

- O repositório é público. Leitura e clone são permitidos sem credencial especial.
- Escrita no GitHub exige uma identidade autenticada com permissão de push.
- O nome comercial do agente (MagicGate, Codex, ChatGPT, Cursor, Copilot ou Gemini) não é, por si só, uma identidade GitHub.
- Cada executor deve usar uma credencial GitHub autorizada pelo proprietário e gravar exclusivamente na branch designada.
- Nunca compartilhar tokens, PATs, chaves ou segredos em commits, logs, issues, PRs ou documentação.

## Branch obrigatória por executor

| Executor | Branch exclusiva |
|---|---|
| MagicGate | `executor/magicgate` |
| Codex | `executor/codex` |
| ChatGPT | `executor/chatgpt` |
| Cursor | `executor/cursor` |
| GitHub Copilot | `executor/copilot` |
| Gemini | `executor/gemini` |

## Regras de isolamento

1. Antes de iniciar, confirmar que a branch atual é a branch exclusiva do executor.
2. Não escrever diretamente em `main`.
3. Não fazer merge, cherry-pick, rebase ou copiar código de branch concorrente.
4. Durante a rodada, não usar a implementação de outro executor como referência.
5. O plano canônico é `plans/contabil-florence-benchmark-v1.yaml`.
6. Registrar métricas, intervenções, retries, falhas, testes e evidências na própria branch.
7. Não alterar o plano canônico nem enfraquecer critérios de aceite.
8. Commits e pushes do executor devem permanecer na sua branch até o encerramento da rodada.
9. Se a identidade GitHub usada pelo agente não possuir push, o agente deve interromper antes de qualquer tentativa de contornar autenticação e solicitar que o proprietário autorize a integração.
10. Segredos de autenticação pertencem ao ambiente do executor, nunca ao repositório.

## Estado de autorização verificável

O acesso de escrita deve ser verificado pela identidade GitHub efetivamente usada pelo agente. A conta proprietária `arkhe-aio-valley` possui administração do repositório. Integrações externas podem usar OAuth, GitHub App, Git Credential Manager ou outra identidade autorizada; esse vínculo é externo ao conteúdo do repositório e precisa existir no ambiente de cada executor.

## Critério de largada

Uma rodada só começa após:
- branch correta selecionada;
- identidade de push validada;
- baseline confirmada;
- cronômetro/evidência de início preparado.

Configuração de infraestrutura, autenticação e instalação de runner não contam como desenvolvimento do benchmark enquanto a rodada não tiver sido formalmente iniciada.
