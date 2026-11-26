# Meu Kit de IA

Desafio de Projeto da [DIO](https://dio.me): monte o seu kit de IA para o dia a dia e delegue uma tarefa real, com você no comando.

O kit foi criado pelo Expert Bruno Lima com os prompts, templates, checklists e skills usados nas Aulas. Ele não é uma apostila: abra a pasta que resolve o seu problema, copie o modelo, adapte e use.

**Copie → adapte → teste → confira → melhore**

## Como Fazer o Desafio

Você não precisa instalar nada nem saber programar. Tudo acontece no navegador.

1. Clique em **Use this template**, depois em **Create a new repository**. Dê um nome simples, como `meu-kit-de-ia`, deixe **Public** e confirme.
2. Siga os passos abaixo com uma tarefa real da sua semana.
3. Preencha a seção [Minha Entrega](#minha-entrega) da sua cópia e entregue o link dela na DIO.

## Os Passos

1. **Escolha uma tarefa real.** Comece pelo trabalho que se repete na sua semana, como preparar uma reunião ou montar um relatório, e não pela ferramenta.
2. **Pegue um modelo.** Abra a pasta do kit que combina com a sua tarefa. Cada modelo tem um botão de copiar no canto.
3. **Adapte.** Troque o que está entre colchetes pelo seu contexto, objetivo, dados, limites e formato.
4. **Teste.** A primeira resposta é um ponto de partida. Ajuste até funcionar para a sua realidade.
5. **Delegue.** Com o [template de delegação](02-templates/03-delegacao.md), entregue a tarefa à IA. Peça o plano antes de ela começar, acompanhe e valide o resultado.
6. **Confira.** Provável não é o mesmo que verdadeiro. Revise com o [Pare, Confira, Use](03-checklists/01-pare-confira-use.md) antes de usar.

## O Que Tem no Kit

| Pasta | Para que serve |
|---|---|
| [01-prompts](01-prompts) | Pedidos prontos para adaptar: escrita, comunicação, pesquisa, comparação e preparação de reuniões |
| [02-templates](02-templates) | Estruturas para preencher: bom pedido, pesquisa e decisão, e delegação |
| [03-checklists](03-checklists) | Revisão de respostas, de textos e de tarefas delegadas |
| [04-skills](04-skills) | Como criar uma skill, e a Skill Preparador de Reuniões usada nas Aulas |
| [05-delegacao-e-automacao](05-delegacao-e-automacao) | Gatilhos de automação, supervisão e checkpoints |

## Os Frameworks das Aulas

- **Bom pedido:** contexto + instrução + objetivo + formato. Quanto menos a IA precisa adivinhar, melhor você consegue avaliar a resposta.
- **Pesquisa e decisão:** pergunta → pesquisa → critérios → comparação → você. Peça fontes quando precisar de informação externa. A decisão final é sua.
- **Segurança:** pare → confira → use. Valide fatos, números, datas, fontes e contexto.
- **Atalhos reutilizáveis:** criar → testar → ajustar → salvar. Separe as instruções fixas das informações que mudam a cada uso.
- **Delegação:** objetivo + contexto + recursos + limites + sucesso. Autonomia funciona melhor quando o resultado esperado está claro.
- **Supervisão:** definir → delegar → acompanhar → validar. Em tarefas maiores, confira o plano, acompanhe os checkpoints e valide o resultado.

> A IA pode ajudar você a escrever, pesquisar, organizar e executar. A responsabilidade pelo resultado continua sendo sua.

---

## Minha Entrega

Na sua cópia, abra este README, clique no lápis (**Edit this file**) e role até aqui. Troque cada frase em itálico pelo que você fez e cole o texto dentro dos blocos já prontos. Para pôr um print, é só colar a imagem com Ctrl+V. No fim, clique em **Commit changes**.

Nada de e-mail, nome de cliente, dado da empresa, senha ou informação pessoal nos textos e nos prints.

### Minha Tarefa Real

_Qual tarefa da sua semana você escolheu e por que ela vale a pena?_

### Meus Atalhos

_Conte quais modelos do kit você adaptou, o que ficou fixo e o que muda a cada uso._

```text
Cole aqui o seu primeiro atalho, já adaptado.
```

```text
Cole aqui o seu segundo atalho, já adaptado.
```

### Minha Delegação

```text
Cole aqui o pedido que você entregou à IA, com objetivo, contexto, recursos, limites e sucesso.
```

### O Plano da IA

_Cole o print do plano e conte o que você ajustou antes de a IA começar._

### O Resultado

_Cole o print do resultado e conte como você conferiu antes de usar._

### Como Foi para Você

_Conte em poucas linhas o que mudou no seu dia a dia._

---

## Extensão — Troubleshooting de Infraestrutura

Esta extensão adapta o kit para investigação supervisionada de incidentes. O material original acima e os créditos à DIO e ao Expert Bruno Lima foram preservados integralmente.

**Estado: implementação documental em revisão, com caso SIMULADO.** Não é uma declaração de tarefa real concluída ou de versão 1.0 liberada.

### Como usar a extensão
1. Leia o [caso simulado](06-casos-praticos/01-incidente-infraestrutura.md).
2. Adapte o [prompt de análise de logs](01-prompts/06-analise-de-logs.md) e o [prompt de diagnóstico](01-prompts/07-diagnostico-de-incidentes.md).
3. Registre a investigação no [template de troubleshooting](02-templates/04-troubleshooting.md).
4. Use a [skill de analista](04-skills/03-skill-analista-infraestrutura.md) e o [roteiro de delegação supervisionada](05-delegacao-e-automacao/03-delegacao-troubleshooting.md).
5. Confira o [checklist técnico](03-checklists/04-validacao-troubleshooting.md) e submeta o plano ao analista antes de qualquer coleta.

### Entrega da extensão até aqui
- Escopo: investigação não destrutiva de falha de acesso HTTP, com foco inicial em resolução DNS e conectividade.
- Atalhos criados: os dois prompts acima. Ficam fixos os limites, a rastreabilidade e o formato; mudam ambiente, evidências, impacto e autorização.
- Delegação: pedido e plano documentados, com análise da entrada sintética E1–E3; supervisão e execução reais permanecem pendentes.
- Resultado: materiais reutilizáveis publicados em branch separada. Nenhum comando de infraestrutura executado, causa raiz confirmada ou benefício operacional medido.
- Minha Tarefa Real e o relato pessoal da seção original permanecem para preenchimento após confirmação de caso real. A simulação não substitui essas evidências.

### Backlog e revisão
| Issue | Entrega | Estado documental |
|---|---|---|
| [#1](https://github.com/davipdm/meu-kit-de-ia/issues/1) | Caso prático | Simulação disponível; caso real a confirmar |
| [#2](https://github.com/davipdm/meu-kit-de-ia/issues/2) | Dois prompts | Implementados; revisão humana pendente |
| [#3](https://github.com/davipdm/meu-kit-de-ia/issues/3) | Template | Implementado; revisão humana pendente |
| [#4](https://github.com/davipdm/meu-kit-de-ia/issues/4) | Checklist | Implementado; revisão humana pendente |
| [#5](https://github.com/davipdm/meu-kit-de-ia/issues/5) | Skill | Modelo educacional disponível; sem instalação automática |
| [#6](https://github.com/davipdm/meu-kit-de-ia/issues/6) | Delegação | Roteiro e análise simulada; execução supervisionada pendente |
| [#7](https://github.com/davipdm/meu-kit-de-ia/issues/7) | README | Navegação e estado adicionados |
| [#8](https://github.com/davipdm/meu-kit-de-ia/issues/8) | Revisão v1.0 | Pendente; sem tag ou release publicada |

As alterações estão no [PR #9](https://github.com/davipdm/meu-kit-de-ia/pull/9), em rascunho. Para preparar a v1.0: revisar o material, confirmar o caso real autorizado, registrar a supervisão e os resultados observados, preencher a entrega e validar o encerramento. Não publicar dados reais, credenciais ou informações identificáveis.

### Exercício DNS com passos de execução
O [caso prático](06-casos-praticos/01-incidente-infraestrutura.md) agora inclui comparação do DNS configurado com 1.1.1.1, mudança opcional no Windows pessoal/laboratório, validação, rollback e dicas de DNS seguro. O exercício de nomes públicos é separado de E1–E3 e permanece simulado, sem resultados executados.
