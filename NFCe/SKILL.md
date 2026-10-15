---
name: nfce-modelo-65
description: Preparar, validar, transmitir e confirmar NFC-e modelo 65 conforme as regras estaduais vigentes.
---

# Skill: emissão e validação de NFC-e (modelo 65)

## Fontes técnicas obrigatórias

- Portal Nacional: https://www.nfe.fazenda.gov.br/portal/
- Documentação técnica: https://www.nfe.fazenda.gov.br/portal/listaConteudo.aspx?tipoConteudo=ndIjl+iEFdE=
- Consulte também a SEFAZ da UF do emitente para credenciamento, endpoints, QR Code, CSC, contingência, leiautes e regras locais vigentes.

## Procedimento de ponta a ponta

1. **Confirmar aplicabilidade**: validar que a operação pode usar NFC-e modelo 65 na UF, e não NF-e modelo 55 ou outro documento.
2. **Validar emitente**: confirmar cadastro, inscrição estadual, regime tributário, credenciamento NFC-e, série/numeração e certificado digital exigido.
3. **Validar venda**: coletar itens, quantidades, preços, descontos, pagamentos, dados do consumidor quando exigidos, entrega e demais informações aplicáveis. Não inventar NCM, CFOP, CST/CSOSN nem alíquotas.
4. **Configurar QR Code**: obter CSC e identificador de token por canal seguro e seguir exatamente a versão da especificação estadual/nacional aplicável. Nunca gravar segredos no código-fonte ou logs.
5. **Construir XML**: usar leiaute e schemas XSD vigentes; calcular chave de acesso, totais e campos exigidos para modelo 65.
6. **Validar localmente**: executar validação XSD, regras de negócio, códigos oficiais, consistência de totais, datas, série/numeração e assinatura XMLDSig.
7. **Assinar**: usar certificado habilitado e proteger chave privada/senha. Confirmar relógio do sistema e cadeia do certificado.
8. **Transmitir**: enviar para o serviço de autorização da SEFAZ competente, no ambiente configurado, usando endpoint oficial vigente para NFC-e. Não assumir que o endpoint de NF-e seja intercambiável.
9. **Tratar retorno**: confirmar código de status, chave e protocolo. Só marcar como autorizada após confirmação oficial. Se rejeitada, guardar código/motivo, corrigir com fonte confiável e validar novamente. Em timeout/resultado desconhecido, consultar conforme o fluxo oficial antes de retransmitir.
10. **Emitir representação e entregar**: gerar DANFE NFC-e/QR Code a partir do documento autorizado, seguindo especificação vigente, e disponibilizar ao consumidor.
11. **Contingência e eventos**: implementar somente o modo de contingência autorizado pela UF e seguir suas condições, prazos e procedimentos de transmissão posterior. Cancelamento e outros eventos devem seguir regras oficiais específicas.

## Para onde enviar

À **SEFAZ autorizadora da UF do estabelecimento**, pelo endpoint oficial NFC-e e ambiente configurado (homologação/produção). Descubra o endereço na documentação estadual vigente; não use URLs presumidas ou endpoints de terceiros sem aprovação.

## Critérios de conclusão

- [ ] Credenciamento, série, numeração e ambiente corretos.
- [ ] Dados da venda e tributação revisados.
- [ ] XML válido no XSD vigente.
- [ ] Assinatura/certificado válidos.
- [ ] QR Code/CSC conforme especificação e segredos protegidos.
- [ ] Resposta oficial confirma autorização e protocolo.
- [ ] XML, protocolo e evidências persistidos.
- [ ] Representação auxiliar entregue ao consumidor quando aplicável.

Estados de retorno recomendados: `authorized`, `rejected`, `processing`, `failed_validation`, `unknown`. Nunca tratar falha de rede como autorização.
