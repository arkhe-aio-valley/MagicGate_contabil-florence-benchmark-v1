# Florence Benchmark v1

Este repositório é o contêiner canônico de um benchmark determinístico de desenvolvimento de software contábil.

## Regra central

Todos os executores partem do mesmo commit da `main`, recebem o mesmo plano, o mesmo dataset e os mesmos critérios de verificação. Nenhum executor pode consultar ou reutilizar a implementação de outro durante sua rodada.

## Branches de execução

- `executor/magicgate`
- `executor/codex`
- `executor/chatgpt`
- `executor/cursor`
- `executor/copilot`
- `executor/gemini`

A `main` é neutra e contém somente o protocolo canônico, documentação e plano. Código produzido por um executor deve existir exclusivamente na branch daquele executor até o encerramento do benchmark.

## Protocolo de rodada

1. Confirmar que a branch do executor deriva da mesma baseline canônica.
2. Registrar instante de início antes da primeira ação de desenvolvimento.
3. Executar `plans/contabil-florence-benchmark-v1.yaml` sem alterar requisitos ou critérios.
4. Registrar toda intervenção humana, pausa, retry, falha de comando e execução de teste.
5. Preservar código, testes e evidências na própria branch.
6. Executar o gate Florence final sem correções silenciosas após o início da validação final.
7. Registrar instante de término e manifesto da entrega.
8. Não fazer merge da implementação do executor em `main` durante as rodadas.

## Métricas mínimas

Tempo total e ativo, intervenções humanas, pausas, retries, comandos falhos, execuções de teste, testes aprovados/reprovados, tarefas concluídas/bloqueadas, arquivos criados/modificados, commits, build final, testes finais e taxa de aceite.

## Comparabilidade

O escopo funcional e os critérios de aceite são idênticos. A arquitetura mínima é React + TypeScript no frontend, FastAPI/Python no backend e SQLite. A identidade visual e decisões internas de implementação podem variar quando não alterarem o contrato funcional.

## Resultado

Após todas as rodadas, os artefatos das branches serão analisados para produzir um relatório comparativo separado. O relatório deverá distinguir métricas objetivas de observações qualitativas e preservar as evidências brutas de cada executor.
