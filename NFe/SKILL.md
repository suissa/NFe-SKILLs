---
name: nfe-modelo-55
description: Preparar, validar, transmitir e confirmar NF-e modelo 55 com documentação oficial vigente.
---

# Skill: emissão e validação de NF-e (modelo 55)

## Objetivo e limites

Siga o processo inteiro, desde a identificação da operação até a confirmação do resultado no autorizador. Não invente informações tributárias. Se faltar dado obrigatório, houver dúvida de CFOP/CST/CSOSN/NCM/tributação, ou divergência cadastral, interrompa a emissão e solicite validação do responsável fiscal.

## Fontes técnicas obrigatórias

- Portal oficial: https://www.nfe.fazenda.gov.br/portal/
- Documentação e schemas: https://www.nfe.fazenda.gov.br/portal/listaConteudo.aspx?tipoConteudo=ndIjl+iEFdE=
- Consulte MOC, Notas Técnicas, tabelas oficiais, schemas XSD e regras da SEFAZ da UF vigentes para a data da operação. Não fixe versões antigas no código sem uma política de atualização.

## Procedimento

1. **Classificar a operação**
   - Confirme que o documento adequado é NF-e modelo 55, não NFC-e, NFS-e ou CT-e.
   - Identifique finalidade (normal, complemento, ajuste ou devolução), natureza da operação, UF de origem/destino, presença de consumidor final, entrega e modalidade da operação.
2. **Coletar dados do emitente**
   - CNPJ/CPF quando permitido, inscrição estadual, regime tributário, endereço, UF, município/IBGE e certificado digital válido.
   - Verifique credenciamento e ambiente habilitado na SEFAZ.
3. **Coletar destinatário e operação**
   - Identificação e endereço do destinatário, itens, quantidades, unidades, preços, descontos, frete, seguro, outras despesas, pagamentos e informações de transporte quando aplicáveis.
   - Obtenha NCM, CEST quando aplicável, CFOP, origem, CST/CSOSN e parâmetros tributários de fonte fiscal aprovada. Não deduza alíquotas apenas pelo texto do pedido.
4. **Resolver numeração e configuração**
   - Determine série, próximo número autorizado internamente, modelo 55, ambiente homologação/produção e endpoint oficial correspondente à UF/serviço.
   - Evite concorrência na numeração; não reutilize chave/número indevidamente.
5. **Montar o XML**
   - Gerar grupos e campos segundo o schema XSD e a versão vigente do MOC/Notas Técnicas.
   - Calcular chave de acesso e dígitos verificadores conforme especificação oficial.
   - Aplicar regras de arredondamento e totais definidas no leiaute; comparar totais de itens, impostos, frete, descontos e total da nota.
6. **Validar antes de transmitir**
   - Validar XML contra XSD vigente.
   - Executar validações de campos obrigatórios, domínio de códigos, datas, CFOP versus UF/operação, totais e regras de negócio publicadas.
   - Verificar certificado, cadeia, validade, uso de chave privada, assinatura XMLDSig e configuração TLS.
   - Em homologação, usar dados e ambiente de teste conforme regras oficiais; nunca usar produção para testes.
7. **Assinar e transmitir**
   - Assinar o XML com certificado autorizado, sem expor chave privada ou senha em logs.
   - Enviar ao serviço oficial de autorização da SEFAZ competente usando endpoint do ambiente configurado e protocolo de comunicação vigente.
   - Respeitar timeout, idempotência, indisponibilidade e consulta de recibo; não reenviar cegamente se o resultado for desconhecido.
8. **Interpretar e validar a resposta**
   - Interpretar código e motivo de retorno conforme documentação oficial.
   - Considerar emitida somente quando houver confirmação oficial de autorização e protocolo válido associado à chave.
   - Em rejeição, registrar código/motivo, corrigir a causa com dados autorizados e retransmitir apenas após nova validação.
   - Em processamento/timeout, consultar recibo ou situação da chave conforme o fluxo oficial; não declarar sucesso por mera resposta HTTP positiva.
9. **Persistir e entregar**
   - Armazenar XML assinado/autorizado, protocolo, chave de acesso, timestamps, ambiente, versão de schema e correlação da requisição com controle de acesso e retenção.
   - Gerar DANFE apenas a partir dos dados autorizados, conforme especificação aplicável.
   - Entregar documento ao destinatário pelo canal aprovado e registrar evidência de entrega.
10. **Pós-emissão**
   - Para cancelamento, CC-e, inutilização ou outros eventos, seguir evento, prazo, justificativa e endpoint oficiais próprios; nunca alterar o XML autorizado silenciosamente.

## Destino da transmissão

O autorizador é a **SEFAZ competente**, usando o serviço e endpoint oficial correspondentes à UF, ao modelo, ao serviço e ao ambiente (homologação ou produção). Não codifique uma URL genérica presumida. Resolva-a a partir da documentação oficial vigente e da configuração fiscal do emitente.

## Critérios de conclusão

- [ ] Dados obrigatórios completos e revisados.
- [ ] XML validado contra XSD vigente.
- [ ] Regras fiscais e totais validados.
- [ ] Assinatura e certificado verificados.
- [ ] Transmissão ao autorizador correto.
- [ ] Autorização oficial e protocolo confirmados.
- [ ] XML e protocolo persistidos com segurança.
- [ ] DANFE/entrega executados quando aplicáveis.

## Saída estruturada recomendada ao sistema chamador

Retorne status inequívoco (`authorized`, `rejected`, `processing`, `failed_validation` ou `unknown`), chave quando existente, protocolo quando autorizado, código/motivo oficial, ambiente, timestamps e referências aos artefatos armazenados. Nunca converta `unknown` em sucesso.
