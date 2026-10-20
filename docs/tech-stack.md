# Stack tecnológica recomendada

## Estado atual

Este repositório é uma biblioteca de instruções e contratos. Ele **não possui uma aplicação de prospecção executável nem dependências de runtime instaladas**. Portanto, a stack abaixo é o padrão recomendado para futuras implementações, não uma descrição de tecnologias já em uso.

## Padrão recomendado

| Camada | Escolha padrão | Regra |
|---|---|---|
| Linguagem | TypeScript em modo strict | Usar JavaScript apenas quando o projeto hospedeiro exigir ou já adotar esse padrão. |
| Runtime de backend | Node.js LTS | Não exigir Bun, Deno ou runtime proprietário; adaptar ao ambiente existente. |
| Núcleo de domínio | TypeScript sem dependência de framework web | Regras de normalização, deduplicação e qualificação devem poder ser testadas isoladamente. |
| Validação de dados | Zod | Validar entradas, configurações e respostas estruturadas de IA na fronteira do sistema. Se o projeto já tiver validador equivalente, avaliar reutilização. |
| API | REST/JSON com OpenAPI quando houver API pública | Em módulo embutido, preferir os contratos e padrões de API já existentes no produto. |
| Persistência | Banco já utilizado pelo produto; PostgreSQL como padrão para produto novo | Não criar um segundo banco se o hospedeiro já tiver persistência adequada. |
| Acesso a dados | Reutilizar ORM/cliente existente; para projeto novo, escolher um só entre Drizzle ORM ou Prisma | Não misturar ORMs nem introduzi-los sem necessidade. |
| IA generativa | Adaptador de provedor com saída estruturada; Vercel AI SDK é uma opção, não requisito | Manter regras críticas determinísticas e evitar acoplamento do domínio a um único modelo. |
| Descoberta/coleta web | APIs oficiais e fontes autorizadas primeiro; Firecrawl pode ser um adaptador opcional | Playwright apenas quando a interação com navegador for necessária e permitida. Não contornar autenticação, paywalls ou controles de acesso. |
| Testes unitários e integração | Vitest | Usar o runner já estabelecido pelo produto se houver um equivalente funcional. |
| Testes de navegador | Playwright, apenas para fluxos que precisem de navegador | Não tornar testes de UI requisito para toda mudança de domínio. |
| Interface | Interface e design system do produto hospedeiro | Não impor Next.js, React ou uma nova navegação a um produto existente. Em aplicação nova, escolher o framework depois de definir os requisitos. |
| Execução assíncrona | Começar com tarefas simples do backend; adicionar fila durável quando volume e confiabilidade justificarem | Redis/BullMQ, Inngest ou serviços equivalentes são opções, não dependências obrigatórias. |
| Observabilidade | Logs estruturados, métricas de custo/latência/erros e trilha de auditoria | Reutilizar a plataforma de observabilidade do produto. |

## Decisão prática para este ecossistema

Para um módulo novo, portátil e reutilizável, o ponto de partida recomendado é **TypeScript + Node.js LTS + Zod + Vitest**, integrado ao banco, à autenticação, à interface e à infraestrutura que o produto hospedeiro já usa.

Se for necessário criar um produto independente do zero, avaliar **PostgreSQL** como banco. Supabase pode ser usado quando oferecer vantagem concreta de autenticação, banco ou serviços gerenciados, mas não é requisito da biblioteca. A hospedagem deve seguir a infraestrutura já adotada pelo produto; não assumir Vercel, Cloudflare ou outro fornecedor sem verificar o contexto.

## Dependências que não devem ser presumidas

Não instalar automaticamente Next.js, React, Supabase, Prisma, Drizzle, Redis, BullMQ, Firecrawl ou SDK de um provedor de IA. Cada dependência precisa corresponder a um requisito real. Não adicionar todas as opções ao mesmo projeto: selecionar uma implementação por responsabilidade.

## Como o agente decide

1. Inspecionar `package.json`, lockfile, runtime, framework, banco, autenticação, testes e deploy do produto.
2. Se houver uma stack funcional, reutilizá-la e propor somente as dependências que faltarem.
3. Se for um projeto novo, aplicar o padrão recomendado acima e justificar qualquer desvio.
4. Registrar as escolhas e versões efetivamente instaladas no próprio projeto, incluindo lockfile.
5. Validar instalação, build, testes relevantes e um fluxo real de integração antes de declarar conclusão.

## Referências

- [TypeScript](https://www.typescriptlang.org/)
- [Node.js](https://nodejs.org/)
- [Zod](https://zod.dev/)
- [Vitest](https://vitest.dev/)
- [Playwright](https://playwright.dev/)
- [PostgreSQL](https://www.postgresql.org/)
- [Vercel AI SDK](https://ai-sdk.dev/)
- [Firecrawl](https://docs.firecrawl.dev/)
