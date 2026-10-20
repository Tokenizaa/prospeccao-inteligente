# Checklist de integração

## Descoberta e preservação

- [ ] Arquitetura, instruções e padrões existentes foram inspecionados.
- [ ] Fluxo e comportamento atuais foram documentados.
- [ ] Não há alterações pendentes sendo sobrescritas.
- [ ] A capacidade equivalente foi procurada antes de criar uma nova.

## Produto e API

- [ ] Contratos de entrada e saída definidos e versionados.
- [ ] Validação de entrada no servidor.
- [ ] Autenticação e autorização reutilizam o modelo do produto.
- [ ] Isolamento de tenant verificado no servidor.
- [ ] Idempotência, paginação, limites e erros definidos.
- [ ] Logs e métricas úteis sem exposição indevida.

## Dados e IA

- [ ] Fontes e finalidade documentadas.
- [ ] Proveniência e data de coleta preservadas.
- [ ] Ausência de dados não é confundida com resultado negativo.
- [ ] Inferências estão separadas de fatos observados.
- [ ] Saídas da IA validadas por esquema e evidência.
- [ ] Revisão humana disponível nos casos previstos.

## Segurança e privacidade

- [ ] Nenhum segredo incluído no código ou logs.
- [ ] Retenção, correção, exclusão e supressão definidas.
- [ ] Conteúdo externo tratado como dado não confiável.
- [ ] Limites contra abuso e consumo excessivo aplicados.
- [ ] Requisitos legais e termos das fontes revisados pelo responsável.

## Validação e entrega

- [ ] Testes focados executados.
- [ ] Testes de regressão relevantes executados.
- [ ] Fluxo integrado validado no ambiente identificado.
- [ ] Persistência e permissões verificadas.
- [ ] Documentação e changelog atualizados.
- [ ] Pendências e bloqueios declarados com clareza.
- [ ] Commit ou referência verificável informado.
