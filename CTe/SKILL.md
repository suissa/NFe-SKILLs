---
name: cte-modelo-57
description: Preparar, validar, transmitir e confirmar CT-e modelo 57 com base na documentação oficial vigente.
---

# Skill: emissão e validação de CT-e (modelo 57)

## Fontes técnicas obrigatórias

- Portal oficial: https://www.cte.fazenda.gov.br/portal/
- Consulte MOC, notas técnicas, schemas XSD, tabelas e regras da SEFAZ autorizadora vigentes.

## Procedimento de ponta a ponta

1. **Confirmar documento e operação**: validar que a prestação exige CT-e modelo 57 e identificar modal, tipo de serviço, UF de início/fim, tomador, remetente, expedidor, recebedor e destinatário conforme aplicável.
2. **Validar emitente**: cadastro fiscal, inscrição estadual, credenciamento, regime, certificado digital, série, numeração e ambiente autorizado.
3. **Coletar dados da prestação**: documentos de referência, carga, valores, componentes do frete, tomador, participantes, percurso, modal e informações exigidas pelo leiaute. Validar documentos relacionados e regras de vínculo.
4. **Validar classificação e tributação**: obter CFOP, CST e parâmetros tributários por fonte oficial/contador; não inferir tributos nem preencher campos fiscais com valores fictícios.
5. **Montar XML**: usar versão vigente do MOC e schemas; gerar chave de acesso e campos de identificação segundo especificação. Garantir consistência entre valores, participantes, documentos vinculados e dados do transporte.
6. **Validar localmente**: validar XSD, campos obrigatórios, tabelas oficiais, datas, UFs, códigos de município, regras de negócio, totais e vínculos documentais.
7. **Assinar e proteger credenciais**: assinar XML com certificado habilitado. Não expor chave privada, senha, tokens ou dados sensíveis em logs.
8. **Transmitir**: usar o serviço de autorização da SEFAZ competente e endpoint oficial do CT-e para UF/serviço/ambiente. Não reutilizar endpoints de NF-e sem confirmação explícita na documentação.
9. **Interpretar retorno**: validar código, protocolo, chave e status. Só declarar autorizado quando o retorno oficial confirmar autorização. Em rejeição, registrar código/motivo e corrigir após verificar a regra. Em timeout, consultar recibo/situação conforme manual antes de tentar de novo.
10. **Persistir e disponibilizar**: guardar XML assinado/autorizado, protocolo, chave, DACTE gerado a partir do documento autorizado, versão do schema, ambiente e trilha de auditoria.
11. **Eventos e encerramento**: cancelamento, carta de correção, prestação em desacordo e outros eventos devem obedecer aos fluxos, prazos e pré-condições oficiais. Não alterar XML autorizado diretamente.

## Para onde enviar

Ao **autorizador da SEFAZ competente**, usando o serviço de autorização CT-e e o endpoint oficial correspondente à UF e ao ambiente configurado. Consulte a lista e os serviços vigentes no portal oficial; não invente URLs nem confunda autorização com consulta de situação.

## Critérios de conclusão

- [ ] Modelo, modal e participantes corretos.
- [ ] Dados da prestação e documentos vinculados conferidos.
- [ ] XML válido no XSD vigente.
- [ ] Regras fiscais e totais conferidos.
- [ ] Assinatura e certificado válidos.
- [ ] Resposta oficial confirma autorização e protocolo.
- [ ] XML, protocolo e evidências persistidos.
- [ ] DACTE disponibilizado quando aplicável.

Estados recomendados: `authorized`, `rejected`, `processing`, `failed_validation`, `unknown`. Não confundir aceite de transporte HTTP com autorização fiscal.
