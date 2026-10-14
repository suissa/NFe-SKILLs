# NF-e — Nota Fiscal Eletrônica (modelo 55)

A NF-e documenta eletronicamente operações com mercadorias e produtos, como vendas, devoluções, transferências e outras operações previstas na legislação. Seu arquivo fiscal é estruturado em XML, assinado digitalmente e submetido à autorização da administração tributária competente.

A NF-e não é simplesmente um PDF/DANFE: o documento fiscal válido é o XML autorizado e seu protocolo. O DANFE é uma representação auxiliar para acompanhar a operação quando aplicável.

## Fluxo conceitual

Emitente autorizado → montagem do XML conforme o leiaute vigente → validação e assinatura → transmissão à SEFAZ autorizadora → resposta de autorização/rejeição → armazenamento do XML e protocolo → geração/entrega do DANFE quando aplicável.

## Documentação oficial

- [Portal Nacional da NF-e](https://www.nfe.fazenda.gov.br/portal/)
- [Documentos, manuais, notas técnicas e esquemas XML](https://www.nfe.fazenda.gov.br/portal/listaConteudo.aspx?tipoConteudo=ndIjl+iEFdE=)
- [Manual de Orientação do Contribuinte e especificações vigentes](https://www.nfe.fazenda.gov.br/portal/)
- [Skill operacional](./SKILL.md)

Confirme sempre a versão vigente do MOC, das Notas Técnicas, dos schemas XSD e das regras da UF antes de implementar.
