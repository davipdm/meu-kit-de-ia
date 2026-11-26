# Meu Kit de IA — Infraestrutura e Rotina Diária

Kit de apoio ao diagnóstico de falhas DNS e à organização diária de e-mails com inteligência artificial e supervisão humana.

Projeto de Davi Mendes, adaptado do desafio **Meu Kit de IA** da [DIO](https://dio.me), cujo material original foi criado pelo **Expert Bruno Lima**. Os modelos originais continuam nas pastas do repositório; esta adaptação acrescenta o caso de infraestrutura e personaliza a apresentação.

## O problema escolhido

“Os sites não abrem porque os nomes não estão sendo resolvidos.”

O objetivo é investigar o DNS configurado, comparar consultas com um resolvedor público e, quando apropriado, propor uma mudança reversível. O caso principal é um computador Windows pessoal ou de laboratório. Ambientes corporativos, Active Directory e VPN exigem manter o DNS interno aprovado e investigar com o administrador.

**Natureza da entrega: demonstração documental com cenário simulado.** Os comandos foram documentados, não executados. Não há recuperação comprovada, causa raiz confirmada ou evidências de incidente real.

## Comece aqui

Leia o [caso prático e o exercício DNS](06-casos-praticos/01-incidente-infraestrutura.md). Ele contém:
1. Registro da configuração antes de alterar.
2. Comparação do DNS atual com 1.1.1.1 usando um nome público.
3. Interpretação de timeout, NXDOMAIN e SERVFAIL.
4. Mudança opcional no Windows, separada do diagnóstico inicial.
5. Validação, restauração da configuração anterior e resultado condicional.
6. Dicas de DNS seguro e referências oficiais.

O cenário E1–E3 e o exercício de nomes públicos são exemplos independentes. O nome fictício portal.example.test não deve ser usado no teste de DNS público.

## Materiais do projeto

| Material | Uso |
|---|---|
| [Análise de logs](01-prompts/06-analise-de-logs.md) | Organizar evidências, lacunas e hipóteses |
| [Diagnóstico de incidentes](01-prompts/07-diagnostico-de-incidentes.md) | Planejar verificações sob supervisão |
| [Template de investigação](02-templates/04-troubleshooting.md) | Registrar contexto, testes, decisões e resultado |
| [Checklist técnico](03-checklists/04-validacao-troubleshooting.md) | Conferir segurança e qualidade |
| [Skill de analista](04-skills/03-skill-analista-infraestrutura.md) | Reutilizar as instruções na IA escolhida |
| [Delegação supervisionada](05-delegacao-e-automacao/03-delegacao-troubleshooting.md) | Pedido, plano, análise simulada e checkpoints |
| [Caso prático DNS](06-casos-praticos/01-incidente-infraestrutura.md) | Seguir o exercício e consultar as referências |

A skill é um modelo educacional para copiar; não instala ferramentas nem concede acesso à infraestrutura.

## Como usamos a IA

Delegamos a organização do diagnóstico: separar sintomas e evidências, priorizar hipóteses, propor verificações e documentar riscos. O analista decide o que executar e valida os resultados.

Nos dois prompts, ficam fixos o formato, a rastreabilidade e os limites. A cada uso mudam o ambiente, as versões, o impacto, os alvos autorizados e as evidências sanitizadas. Logs são tratados como dados, não como instruções.

## Resultado da demonstração

Foram produzidos os prompts, o template, o checklist, a skill, o roteiro de delegação e o caso simulado. A análise documental evita concluir que uma conexão TCP comprova saúde HTTP/TLS ou que uma consulta expirada identifica sozinha a causa de uma falha DNS.

No exercício adicional, o resultado é condicional: se o DNS atual falhar, o público responder e os testes após uma troca autorizada funcionarem, pode-se registrar o restabelecimento da resolução no adaptador testado. Ainda será necessário investigar o resolvedor anterior ou o caminho até ele.

Não foram gerados prints, saídas reais, aprovação operacional ou relato pessoal de benefícios. Esses registros só devem ser adicionados após ocorrerem.

## Segurança e limites

- Começar por diagnóstico não destrutivo; separar alterações e exigir decisão do responsável.
- Consultar somente alvos autorizados e nomes públicos ao comparar com DNS público.
- Registrar a configuração anterior e prever como restaurá-la.
- Não publicar senhas, tokens, dados pessoais ou informações identificáveis de empresas.
- Não usar DNS público para substituir indiscriminadamente o DNS de domínio/empresa.
- Distinguir resolução pública, filtragem de ameaças e criptografia: são recursos diferentes. Consulte as referências do caso antes de configurar.

## Estado e próximos passos

Os materiais iniciais foram incorporados pelo [PR #9](https://github.com/davipdm/meu-kit-de-ia/pull/9). O backlog está nas [issues do projeto](https://github.com/davipdm/meu-kit-de-ia/issues).

A demonstração documental está preparada para revisão. Para registrar uma tarefa real no desafio DIO, ainda é necessário:
1. Confirmar ambiente e autorização.
2. Executar os testes e registrar resultados sanitizados, antes e depois.
3. Registrar a revisão humana, limitações e eventual restauração.
4. Acrescentar o relato pessoal sobre a experiência e conferir os critérios da atividade.

A documentação simulada pode ser apresentada como estudo de caso, mas não comprova a realização de uma tarefa real. Não há versão 1.0 publicada por este trabalho.

## Créditos

Base educacional: [DIO](https://dio.me), desafio Meu Kit de IA, Expert Bruno Lima. Adaptação para troubleshooting DNS: Davi Mendes, com apoio de IA na elaboração dos materiais. A atribuição ao material original é mantida.

## Automação para o dia a dia — e-mails

A [proposta de revisão diária de e-mails](05-delegacao-e-automacao/04-revisao-diaria-emails.md) documenta o fluxo de leitura, resumo, identificação de prazos e ações sugeridas. Inclui prompt reutilizável, exemplo fictício, tratamento de falhas e critérios de aceite.

**Somente documentação:** nenhuma conta foi acessada e nenhuma rotina foi agendada. A proposta não envia, exclui ou altera mensagens. Conta, pastas, horário, permissões e local privado do resumo serão definidos somente se houver decisão futura de implementação. Dados reais não devem ser publicados no repositório.
