# Instrução: implementar prospecção e qualificação de leads

## Antes de codificar

1. Definir público-alvo, finalidade comercial, região, critérios de inclusão/exclusão e resultado esperado.
2. Mapear fontes permitidas e registrar limitações, termos de uso e frequência aceitável.
3. Definir os campos mínimos necessários e sua proveniência.
4. Definir a qualificação com critérios configuráveis, pesos explicáveis quando houver pontuação e limiares revisáveis.
5. Definir limites de custo, volume, taxa de requisição e retenção.

## Implementação

- Usar conectores isolados por fonte com timeout, limites e tratamento de falhas.
- Normalizar os dados sem perder a proveniência.
- Deduplicar por evidências adequadas e preservar conflitos para revisão.
- Separar fatos coletados de inferências geradas por IA.
- Produzir justificativa de qualificação que aponte os dados usados e a versão dos critérios.
- Tratar dados ausentes como desconhecidos, não como negativos automáticos.
- Disponibilizar revisão humana, correção e supressão quando aplicável.
- Registrar erros e métricas operacionais sem expor dados pessoais desnecessários.

## Proibições

- Não inventar leads, contatos, empresas, fontes ou evidências.
- Não contornar controles de acesso nem violar termos de fonte.
- Não disparar campanhas ou contatar pessoas sem autorização e controles adequados.
- Não inferir atributos sensíveis.
- Não tomar a resposta de um modelo como verificação factual independente.

## Validação mínima

Testar dados válidos, incompletos, duplicados e conflitantes; indisponibilidade de fontes; rate limit; saída inválida da IA; tenant sem permissão; repetição idempotente; e pedido de supressão/exclusão. Medir precisão da qualificação com amostra revisada por humanos antes de uso comercial amplo.
