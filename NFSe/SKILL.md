---
name: nfse
description: Preparar, validar, transmitir e confirmar NFS-e conforme o padrão nacional ou sistema municipal competente.
---

# Skill: emissão e validação de NFS-e

## Fontes técnicas obrigatórias

- Portal Nacional da NFS-e: https://www.gov.br/nfse/pt-br
- Biblioteca técnica: https://www.gov.br/nfse/pt-br/biblioteca/documentacao-tecnica
- Quando aplicável, consulte portal oficial da prefeitura e documentação do provedor autorizado pelo município.

## Procedimento de ponta a ponta

1. **Identificar jurisdição e integração**: obter município de incidência, local da prestação, cadastro municipal, regime do prestador e confirmar se o município usa padrão nacional ou solução própria/provedor. Se não for possível confirmar, interrompa.
2. **Validar prestador e tomador**: CNPJ/CPF quando aplicável, inscrição municipal, endereço, regime tributário, dados do tomador e requisitos de retenção. Proteger dados pessoais.
3. **Descrever o serviço**: coletar código de serviço conforme tabela municipal/nacional aplicável, descrição, competência, valores, deduções, descontos e informações de retenção. Não inferir código de serviço, alíquota de ISS ou retenções sem fonte fiscal aprovada.
4. **Resolver regras tributárias**: validar município competente, incidência, exigibilidade, retenções, regime especial e regras vigentes para a data da prestação. Escalar divergências ao responsável fiscal.
5. **Montar requisição/documento**: seguir o leiaute, schema, contrato de API, assinatura e versão publicados para a integração identificada. Não presumir que todos os municípios usem o mesmo XML, JSON ou fluxo síncrono.
6. **Validar localmente**: validar campos obrigatórios, formato, códigos oficiais, valores, datas, certificado/token, assinatura quando exigida e regras do manual da integração. Usar ambiente de homologação quando disponível.
7. **Transmitir ao destino correto**: usar endpoint oficial do padrão nacional ou do município/provedor autorizado, no ambiente correto. Segredos devem vir de cofre/configuração segura, nunca de prompt ou repositório.
8. **Interpretar retorno**: distinguir documento recebido/processando de NFS-e efetivamente gerada. Se houver protocolo assíncrono, consultar o processamento até estado terminal com limite e backoff. Em rejeição, registrar código/mensagem e corrigir apenas com dados confirmados.
9. **Confirmar emissão**: exigir número/chave/identificador oficial da NFS-e e status de emissão confirmado pela autoridade/plataforma competente. Uma resposta HTTP 200, isoladamente, não prova emissão.
10. **Armazenar e entregar**: persistir payload enviado, resposta, XML/PDF oficial quando disponibilizado, identificador, timestamps, município, versão do contrato e trilha de auditoria. Entregar ao tomador conforme política autorizada.
11. **Cancelar/substituir**: executar somente pelos fluxos oficiais aplicáveis, com motivo, autorização, prazos e vínculo com o documento original. Não editar documento já emitido.

## Para onde enviar

- **Padrão nacional**: endpoint e ambiente indicados pela documentação técnica vigente do Portal Nacional da NFS-e.
- **Sistema municipal/provedor**: endpoint oficial indicado pela prefeitura ou provedor formalmente autorizado.

Nunca escolha o destino apenas pelo nome do município ou por busca não verificada; confirme a documentação e a configuração contratual vigentes.

## Critérios de conclusão

- [ ] Município, padrão e endpoint confirmados.
- [ ] Cadastro e serviço validados.
- [ ] Regras tributárias aprovadas por fonte confiável.
- [ ] Payload conforme contrato/schema vigente.
- [ ] Autenticação/assinatura válidas.
- [ ] Retorno final confirma emissão, não apenas recebimento.
- [ ] Identificador e artefatos oficiais persistidos.
- [ ] Documento entregue ao tomador quando aplicável.

Retorne estado inequívoco: `issued`, `rejected`, `processing`, `failed_validation` ou `unknown`. Nunca prometa emissão quando o resultado for desconhecido.
