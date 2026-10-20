# Arquitetura de referência

## Propósito

Orientar uma aplicação independente na Cloudflare: TypeScript e Workers para API e coordenação, D1 para estado relacional, processamento assíncrono com Queues/Workflows quando necessário, Browser Run para navegação automatizada permitida e um adaptador de IA substituível. Harnesses de desenvolvimento não fazem parte do runtime de produção.

## Capacidades lógicas

1. **Descoberta de fontes** — identifica fontes públicas ou autorizadas adequadas ao segmento.
2. **Coleta** — obtém dados respeitando permissões, termos de uso, limites e políticas de acesso.
3. **Normalização** — converte dados para um modelo interno consistente, preservando origem e momento da coleta.
4. **Deduplicação** — detecta registros equivalentes sem fundir pessoas ou organizações com evidência insuficiente.
5. **Enriquecimento** — complementa dados somente quando a fonte e a finalidade são permitidas.
6. **Qualificação** — aplica critérios configuráveis e explica os motivos da classificação.
7. **Revisão humana** — permite corrigir, aceitar, rejeitar e contestar resultados.
8. **Entrega** — expõe resultados ao produto por API ou integração documentada.
9. **Auditoria e controle** — registra operações relevantes, erros, consentimentos e solicitações de exclusão conforme a política do produto.

Essas capacidades são limites lógicos, não uma exigência de criar um serviço separado para cada item. Começar pela implementação mais simples que preserve separação de responsabilidades.

## Fluxo de referência

`configuração → fontes autorizadas → coleta → normalização → deduplicação → enriquecimento → qualificação → revisão/entrega`

Falhas de fonte devem ser explícitas. Não preencher dados ausentes com valores inventados nem converter ausência em pontuação zero sem regra documentada.

## Dados e proveniência

Todo dado externo relevante deve carregar, quando aplicável:
- fonte e URL ou identificador de origem;
- instante de coleta e, se disponível, data de atualização na fonte;
- finalidade e base de uso autorizada;
- estado de verificação e grau de confiança;
- transformação aplicada e versão da regra;
- restrições, expiração ou política de retenção.

## IA e determinismo

- Usar regras determinísticas para validações objetivas, deduplicação segura e critérios que exigem reprodutibilidade.
- Usar IA como apoio para extração, classificação ou síntese quando apropriado.
- Exigir saída estruturada, validação de esquema e tratamento de respostas inválidas.
- Registrar modelo/provedor e versão de prompt quando isso for relevante para auditoria.
- Não permitir que a IA invente evidências ou tome decisões de alto impacto sem controle adequado.
- Manter separadas evidência observada, inferência e hipótese.

## Resiliência e observabilidade

Definir limites de requisição, timeout, retentativas com backoff, idempotência e tratamento de indisponibilidade de acordo com o provedor. Não fazer retentativas ilimitadas. Métricas úteis incluem volume processado, erros por fonte, duplicatas, latência, custo, taxa de revisão e qualidade da qualificação.

## Evolução

Versionar contratos públicos. Mudanças incompatíveis exigem plano de migração, compatibilidade explícita e testes de regressão. Consulte também [contrato de integração](integration-contract.md) e [segurança](security.md).
