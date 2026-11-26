# Caso prático — investigação de indisponibilidade HTTP

> SIMULAÇÃO DIDÁTICA. Cenário e registros abaixo são fictícios, criados para exercitar os prompts. Não são evidências coletadas nem comprovam execução em ambiente real. Aguardamos confirmação do usuário para definir um caso real.

## Escopo
Objetivo: organizar uma investigação não destrutiva de falha de acesso ao serviço web de laboratório `portal.example.test`, separando observações de hipóteses.
Ambiente fictício: cliente Windows, servidor Linux com serviço HTTP e resolução DNS interna. Versões, topologia e configuração não foram fornecidas.
Impacto simulado: um cliente relata falha de acesso; abrangência, duração e criticidade ainda desconhecidas.
O kit poderá ser adaptado futuramente para Windows Server, Active Directory, Linux, Azure, virtualização e redes. Este exemplo cobre apenas DNS e conectividade HTTP.

## Entrada sintética para copiar nos prompts
```text
SIMULAÇÃO — não coletado de infraestrutura real.
E1 | T+00 | cliente-lab | Relato fictício: portal.example.test não abre no navegador.
E2 | T+02 | cliente-lab | Resultado sintético de consulta DNS: consulta expirou.
E3 | T+03 | cliente-lab | Resultado sintético de teste TCP ao destino 192.0.2.10:443: conexão estabelecida.
```
T+ representa tempo relativo; data, fuso e relógios não foram definidos. O endereço é ilustrativo. E3 não prova funcionamento HTTP, TLS ou identidade do serviço; E2 não prova falha geral do DNS.

## Hipóteses, não conclusões
1. Problema de resolução no cliente ou no caminho ao resolvedor: compatível com E2; falta configuração e repetição controlada.
2. Falha específica do registro ou do resolvedor: falta comparar consultas e respostas.
3. Problema de aplicação ou TLS coexistente: E3 não o exclui.

## Plano proposto — nenhum comando executado
Primeiro confirmar autorização, sistema, versões, destino e janela de coleta.
- Consultar configuração DNS local, limitada ao necessário; sanitizar nomes e endereços antes de compartilhar.
- Consultar apenas o nome e o resolvedor autorizados; registrar horário, comando, saída e origem.
- Repetir teste TCP somente ao destino/porta autorizados e comparar com resolução por nome.
- Pedir registros relevantes e sanitizados de aplicação e DNS, em janela pequena.
Mesmo testes de leitura podem gerar tráfego e logs; limitar tentativas e interromper se houver impacto. Não varrer rede.

## Limites e encerramento
Não reiniciar serviços, limpar caches, editar DNS/firewall, alterar permissões ou executar correções. Nenhuma mudança foi proposta para execução; rollback não se aplica a esta etapa documental. Qualquer correção futura exige plano, risco, aprovação e rollback próprios.
Sucesso desta etapa: hipóteses rastreáveis e plano revisável. Causa raiz, solução, validação operacional, aprovação humana e benefícios reais permanecem pendentes.
Próximo checkpoint: o analista confirma o plano antes de qualquer coleta. Não substituir os dados sintéticos por dados reais sem autorização e sanitização.

## Materiais
Usar [análise de logs](../01-prompts/06-analise-de-logs.md) e [diagnóstico](../01-prompts/07-diagnostico-de-incidentes.md).
Base educacional: desafio Meu Kit de IA da DIO, criado pelo Expert Bruno Lima; exemplo adicional de infraestrutura.
