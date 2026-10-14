# NFe-SKILLs

Skills para agentes que precisam preparar, validar, transmitir e acompanhar documentos fiscais eletrônicos brasileiros.

## Tipos documentados

| Diretório | Documento | Uso principal |
|---|---|---|
| [NFe](./NFe/) | NF-e, modelo 55 | Operações com mercadorias e produtos |
| [NFCe](./NFCe/) | NFC-e, modelo 65 | Varejo ao consumidor final |
| [NFSe](./NFSe/) | NFS-e | Prestação de serviços |
| [CTe](./CTe/) | CT-e, modelo 57 | Prestação de serviços de transporte de cargas |

Cada diretório contém:
- `README.md`: conceito, escopo e referências oficiais.
- `SKILL.md`: procedimento operacional para o agente, da coleta dos dados à validação do resultado da transmissão.

## Regra de segurança fiscal

Estas skills orientam a implementação do fluxo, mas não substituem a legislação, o contador, o manual técnico vigente ou as regras da SEFAZ/município. O agente deve consultar a documentação oficial atual antes de emitir. Nunca invente dados fiscais, certificados, códigos, alíquotas, URLs de produção ou protocolos. Não transmita documentos reais sem autorização explícita do responsável.

## Fluxo de alto nível

1. Identificar o documento correto e a jurisdição aplicável.
2. Coletar e validar dados cadastrais, fiscais e da operação.
3. Resolver regras tributárias com fonte autorizada e versionada; encaminhar ambiguidades ao responsável fiscal.
4. Construir o payload/XML conforme o leiaute e a versão vigentes.
5. Validar estrutura, regras de negócio, assinatura digital e pré-requisitos.
6. Transmitir ao autorizador correto, usando ambiente e credenciais configurados.
7. Interpretar o retorno, confirmar autorização ou registrar rejeição.
8. Persistir XML/payload, protocolo, recibos, eventos e evidências de auditoria.
9. Só informar emissão concluída após confirmar o status oficial de autorização.

## Referências oficiais gerais

- Portal Nacional da NF-e: https://www.nfe.fazenda.gov.br/portal/
- Portal Nacional da NFC-e / documentação no Portal NF-e: https://www.nfe.fazenda.gov.br/portal/
- Portal Nacional da NFS-e: https://www.gov.br/nfse/pt-br
- Portal do CT-e: https://www.cte.fazenda.gov.br/portal/

Consulte também a SEFAZ autorizadora, a prefeitura ou o provedor municipal aplicável, conforme o documento e a localidade.
