# Delegação supervisionada — troubleshooting

> SIMULAÇÃO DIDÁTICA. Este documento contém um pedido reutilizável e uma análise documental do caso sintético. Não registra coleta, correção, aprovação humana ou resolução de incidente real.

## Pedido para copiar
```text
Objetivo: organizar o diagnóstico não destrutivo do caso fornecido.
Contexto: SIMULAÇÃO do caso 06-casos-praticos/01-incidente-infraestrutura.md.
Recursos: somente E1, E2 e E3 do caso, os dois prompts de infraestrutura, o template e o checklist do kit.
Limites: não executar comandos ou mudanças, não inventar evidências, não acessar infraestrutura ou solicitar dados sensíveis.
Sucesso: entregar hipóteses ligadas aos IDs e plano de verificações com riscos, lacunas e critérios de validação.
Checkpoint: apresentar o plano e aguardar revisão do analista antes de qualquer coleta. Propor correção apenas em etapa separada.
```

## Plano proposto pela IA — SIMULAÇÃO
1. Confirmar sistema/versão, janela, autorização e abrangência do sintoma E1.
2. Organizar E2 (consulta DNS expirada sintética) e E3 (conexão TCP sintética).
3. Priorizar investigação de resolução, mantendo aplicação/TLS como alternativas.
4. Propor consulta limitada de configuração e resolução, seguida de comparação com teste TCP ao alvo autorizado.
5. Registrar resultados reais somente quando fornecidos pelo analista e reaplicar o checklist.

## Análise documental produzida pela IA — SIMULAÇÃO
| Evidência | Interpretação limitada | O que falta |
|---|---|---|
| E1 | Relato fictício de falha de acesso | Erro exato, abrangência e início |
| E2 | Uma consulta expirou na entrada sintética | Resolvedor, configuração, repetição e horário/fuso |
| E3 | Há conexão TCP na entrada sintética | Identidade do serviço, HTTP, TLS e relação com o nome consultado |

Hipótese prioritária: problema de resolução no cliente/caminho/resolvedor; não confirmada. E2 não localiza o ponto de falha. E3 não prova que a aplicação está saudável.
Resultado desta etapa: análise e plano documentais. Causa raiz, correção e benefício operacional não comprovados.

## Checkpoints e registro de supervisão
| Checkpoint | Estado | Registro necessário |
|---|---|---|
| Revisão do plano de coleta | Pendente | Responsável, data, ajustes e alvos autorizados |
| Coleta limitada pelo analista | Não executada | Comando efetivo, versão, horário/fuso e saída sanitizada |
| Revisão de resultados | Pendente | Evidências e decisão do analista |
| Eventual correção | Não proposta para execução | Risco, autorização, janela e rollback |
| Validação e encerramento | Pendente | Critérios antes/depois e confirmação humana |

A autorização para desenvolver o repositório não equivale a aprovação de coleta ou correção em infraestrutura.

## Aplicação documental do checklist
Conferido nesta elaboração: rótulo de simulação, IDs E1–E3, separação entre hipótese e observação, ausência de dados reais e distinção entre proposta e execução.
Pendentes: aprovação do plano, coleta, confirmação do caso real, validação operacional e revisão humana final.
Não aplicáveis nesta etapa: fontes de comandos específicos (nenhum recomendado), rollback (nenhuma mudança).
Não há prints nem saídas reais para anexar.

## Próxima utilização
Após confirmação do caso pelo usuário, substituir o contexto por informações mínimas sanitizadas, reapresentar o plano e registrar apenas checkpoints que efetivamente ocorrerem. Use o [template](../02-templates/04-troubleshooting.md), a [skill](../04-skills/03-skill-analista-infraestrutura.md) e o [checklist](../03-checklists/04-validacao-troubleshooting.md).

## Complemento — exercício de DNS público
Para praticar execução e resultado proposto, seguir o exercício adicional no [caso prático](../06-casos-praticos/01-incidente-infraestrutura.md). Ele é independente de E1–E3: comparar consultas de example.com no DNS atual e no 1.1.1.1 antes de alterar configuração. A mudança opcional é exclusiva de laboratório/pessoal autorizado, em etapa separada, com registro anterior, validação e rollback. Não aplicar DNS público a nomes internos ou usar o domínio fictício portal.example.test nessa comparação. Nenhuma execução, melhora ou aprovação de coleta foi registrada.
