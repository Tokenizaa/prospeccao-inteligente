# Contrato de integração API-first

Este documento define princípios e um contrato lógico inicial. Não representa uma API já implantada nem prescreve rotas ou tecnologias específicas.

## Recursos lógicos

- **Campaign**: objetivo, segmento, filtros, fontes autorizadas, estado e limites.
- **Lead**: organização ou contato potencial, dados permitidos e proveniência.
- **Qualification**: resultado, critérios aplicados, justificativas, versão da regra e confiança.
- **Source**: origem, permissões, limites, estado e metadados da coleta.
- **Activity**: evento de auditoria operacional com dados minimizados.
- **Suppression**: registro necessário para impedir contato ou nova coleta conforme a finalidade e a política de retenção.

## Requisitos de interface

- Definir contratos de entrada e saída com esquema explícito.
- Validar campos, tipos, tamanhos, enumerações e limites no servidor.
- Usar autenticação e autorização do produto hospedeiro; não criar uma segunda identidade sem justificativa.
- Isolar dados por organização/tenant quando houver múltiplos clientes.
- Aplicar limites de uso, paginação, timeouts e respostas de erro consistentes.
- Projetar operações que possam ser repetidas com segurança; usar idempotência em operações de criação/processamento quando necessário.
- Versionar APIs e documentar compatibilidade.
- Nunca retornar segredos, dados internos desnecessários ou detalhes sensíveis em mensagens de erro.

## Modelo conceitual mínimo de lead

| Campo | Finalidade |
|---|---|
| id | Identificador interno estável |
| entity_type | Organização, pessoa ou outro tipo permitido |
| name | Nome conforme fonte, quando disponível |
| contact_points | Canais de contato permitidos, com status de verificação |
| attributes | Atributos autorizados e tipados |
| source_records | Proveniência dos dados |
| qualification | Resultado e justificativa da qualificação |
| status | Estado explícito do fluxo |
| created_at / updated_at | Auditoria temporal |

O modelo final deve ser adequado ao segmento e à legislação aplicável. Não coletar campos apenas porque são tecnicamente possíveis.

## Estados e erros

Estados de processamento devem distinguir pelo menos: pendente, em processamento, concluído, concluído com avisos, falhou e cancelado. Não representar falha ou ausência de dados como sucesso.

Erros devem incluir um código estável, uma mensagem segura e indicação se a operação pode ser repetida. Evitar devolver stack traces ou respostas brutas de fornecedores.

## Webhooks e eventos

Quando aplicável, validar assinatura, timestamp e proteção contra replay; processar de forma idempotente; e não confiar no corpo recebido sem validação. Não incluir dados pessoais excessivos em eventos.

## Critérios de aceitação

A integração só é considerada concluída após validar autenticação, autorização, isolamento de tenant, esquema, erros, idempotência, limites e fluxo de ponta a ponta no ambiente disponível.
