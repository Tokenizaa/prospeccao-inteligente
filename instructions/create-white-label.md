# Instrução: implementar prospecção em uma solução white label

## Objetivo

Criar uma capacidade de prospecção configurável por cliente/segmento sem duplicar a lógica central nem misturar os dados de tenants.

## Procedimento

1. Inspecionar produto, arquitetura, autenticação, modelo de tenant, design system, infraestrutura e testes.
2. Definir qual problema comercial será resolvido e quem poderá usar a capacidade.
3. Separar mecanismo comum de configuração específica do segmento.
4. Definir fontes autorizadas, finalidade, campos necessários, limites, retenção e supressão.
5. Integrar por contratos documentados, reutilizando autenticação, logs e componentes existentes.
6. Isolar configuração e dados por tenant no servidor.
7. Disponibilizar critérios de qualificação explicáveis e versionados.
8. Criar testes para isolamento, autorização, deduplicação, falhas de fonte e saída inválida da IA.
9. Validar o fluxo completo no ambiente disponível e documentar configuração e operação.

## Critérios de conclusão

- Configuração específica não exige fork da lógica comum.
- Dados e credenciais não atravessam tenants.
- Fontes e regras são rastreáveis.
- Falhas são explícitas e recuperáveis.
- Contratos e configuração estão documentados.
- Testes executados e resultados reais estão registrados.

Não afirmar que um módulo é white label apenas por permitir mudar o logotipo. A configuração, os dados, as permissões e as regras comerciais também devem respeitar o tenant.
