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

## Exercício orientado — nomes públicos não resolvem no Windows

> SIMULAÇÃO ADICIONAL, independente de E1–E3. Não consulte portal.example.test no DNS público: esse nome fictício não é um domínio público. Abaixo usamos example.com apenas como alvo público de exemplo. Não foram executados os comandos nem produzidas saídas reais.

### Cenário e limites
Windows 10/11 de laboratório ou computador pessoal, fora de domínio Active Directory e sem VPN/DNS corporativo obrigatório. Sintoma proposto: sites públicos não abrem por nome. Antes de usar em caso real, confirmar versão, adaptador, autorização e se há política corporativa. Não mudar roteador, servidor, VPN ou vários dispositivos.

Em rede corporativa, domínio AD ou VPN com nomes internos, manter o DNS interno aprovado: um DNS público não conhece as zonas privadas e pode prejudicar descoberta de serviços e login. Investigar o DNS interno e seus encaminhadores com o administrador. Não enviar nomes internos a resolvedores públicos.

### 1. Registrar o estado antes de alterar
No PowerShell do Windows, os comandos abaixo são de diagnóstico; não exigem troca de configuração:
```powershell
Get-DnsClientServerAddress
ipconfig /all
nslookup example.com
nslookup example.com 1.1.1.1
```
Registrar adaptador ativo, DNS configurado, DHCP ou manual, horário/fuso, erro completo e resultado de cada consulta. A saída de ipconfig pode revelar nomes e endereços internos: manter o registro original privado e sanitizar antes de publicar. Não interpretar IPv4 isoladamente se houver IPv6, VPN ou múltiplos adaptadores.

A consulta explícita ao 1.1.1.1 testa outro resolvedor sem mudar o DNS do computador. Gera tráfego externo e só deve usar domínio público e rede autorizada.

### 2. Interpretar antes de decidir
| Resultado a observar | Interpretação e próximo passo |
|---|---|
| DNS configurado expira; 1.1.1.1 responde | Indício de problema no resolvedor atual ou caminho até ele; não identifica sozinho a causa raiz. Testar mais de um nome público antes de mudança. |
| Ambos expiram | Verificar conectividade, VPN, firewall ou bloqueio de DNS externo; não concluir que trocar DNS resolverá. |
| Ambos respondem, navegador falha | Investigar cache, DNS seguro do navegador, proxy, TLS ou aplicação. |
| NXDOMAIN | O resolvedor informa nome inexistente; conferir grafia e registro. Não é o mesmo que timeout. |
| SERVFAIL | Falha ao concluir a resolução; investigar servidor, domínio e possível validação DNSSEC, sem afirmar causa apenas pelo código. |

Test-NetConnection com porta 53 verifica TCP, não comprova funcionamento DNS UDP. Ping bloqueado também não prova falta de Internet. Não desativar firewall como tentativa genérica.

### 3. Mudança opcional e reversível — somente após decisão humana
Se o laboratório/pessoal permite DNS público e o teste comparativo justifica, registrar a configuração original e testar primeiro em um único adaptador.

No Windows 11: Configurações → Rede e Internet → adaptador ativo → Atribuição de servidor DNS → Editar → Manual → IPv4. Definir DNS preferencial 1.1.1.1 e alternativo 1.0.0.1; salvar. Os rótulos podem variar por versão. No Windows 10, usar as propriedades IPv4 do adaptador conforme o guia oficial abaixo. Não alterar endereço IP, gateway ou desabilitar IPv6 para realizar este teste.

Isso é uma alteração de configuração, separada do diagnóstico não destrutivo inicial. Pode afetar nomes internos, filtros e acesso; não aplicar em máquina corporativa sem aprovação. Se IPv6 fornecer outro DNS, documentar e configurar de forma coerente somente quando autorizado, com orientação do provedor; não considerar o teste IPv4 como validação de todo o tráfego.

### 4. Validar e desfazer se necessário
Repetir nslookup example.com sem servidor explícito e conferir qual resolvedor respondeu. Testar outros nomes públicos e o acesso pelo navegador. DNS seguro do navegador pode usar outro provedor; verificar sua configuração antes de atribuir a melhora à mudança do sistema.

Se houver cache negativo suspeito, somente após registrar a evidência e aprovar essa ação separada, considerar ipconfig /flushdns. Ele altera o cache local; não faz parte da coleta inicial nem corrige uma falha persistente do servidor.

Rollback: restaurar exatamente os DNS anteriores ou Automático (DHCP), conforme o estado registrado, incluindo IPv6 se alterado. Repetir os testes e verificar serviços necessários. Não escolher DHCP por suposição se a configuração original era manual.

### 5. Resultado proposto — condicional, não observado
Se o DNS anterior falhar, o público responder e, após a mudança autorizada, consultas e navegação funcionarem, registrar:
“Resolução de nomes públicos restabelecida no adaptador testado após troca do resolvedor. Evidência compatível com problema no DNS anterior ou no caminho até ele; causa raiz ainda não confirmada. Investigar configuração recebida por DHCP/roteador, disponibilidade e encaminhamento do resolvedor original.”

Anexar somente saídas realmente coletadas, com antes/depois e horário. Se não houver melhora, restaurar configuração e continuar investigação. Esta simulação não declara recuperação, execução ou aprovação operacional.

### 6. Dicas de DNS seguro
- 1.1.1.1 e 1.0.0.1: resolução pública sem filtro de conteúdo.
- 1.1.1.2 e 1.0.0.2: alternativa Cloudflare com filtragem de domínios conhecidos de malware/phishing; não garante bloqueio de todas as ameaças.
- DNS sobre HTTPS (DoH) ou TLS (DoT) cifra o trecho entre cliente e resolvedor quando configurado e suportado. Apenas inserir 1.1.1.1 no adaptador não garante criptografia.
- DNSSEC valida autenticidade/integridade das respostas em zonas assinadas; é diferente de criptografia e de filtro contra malware.
- Usar os dois endereços da mesma modalidade de filtragem. Um alternativo sem filtro pode permitir consultas sem a proteção pretendida.
- Preferir provedor com política de privacidade clara e configuração compatível com a rede. Em empresa, seguir o DNS e a política de criptografia aprovados; DNS público não deve contornar controles internos.

### Referências oficiais
- [Microsoft — diagnóstico de clientes DNS](https://learn.microsoft.com/en-us/windows-server/networking/dns/troubleshoot/troubleshoot-dns-client)
- [Microsoft — configurações DNS em ambientes AD](https://learn.microsoft.com/en-us/troubleshoot/windows-server/networking/best-practices-for-dns-client-settings)
- [Cloudflare — configuração no Windows](https://developers.cloudflare.com/1.1.1.1/setup/windows/)
- [Cloudflare — endereços e filtros](https://developers.cloudflare.com/1.1.1.1/ip-addresses/)
- [Cloudflare — criptografia DNS](https://developers.cloudflare.com/1.1.1.1/encryption/)

Orientações consultadas em 26/11/2026. Diagnóstico e configuração reais dependem do ambiente confirmado.
