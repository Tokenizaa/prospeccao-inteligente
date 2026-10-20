# Stack tecnológica e arquitetura padrão

## Decisão

O produto deve funcionar como uma aplicação independente na Cloudflare, sem depender de OpenCode, Claude Code ou outro harness em produção. Harnesses podem ajudar a desenvolver e manter o código, mas não são runtime do produto.

O repositório atual contém documentação e instruções; ainda não contém a aplicação executável nem dependências de runtime instaladas.

## Stack de implementação

| Camada | Tecnologia padrão | Responsabilidade |
|---|---|---|
| Linguagem | TypeScript | Código tipado da API, pipeline e integrações. |
| Runtime/API | Cloudflare Workers | Receber solicitações, aplicar regras, coordenar etapas e expor endpoints. |
| Interface web | HTML/CSS/TypeScript servido pela Cloudflare; adotar framework só se a interface justificar | Configurar campanhas, inspecionar evidências, aprovar leads e acompanhar execução. |
| Persistência relacional | Cloudflare D1 (SQLite) | Campanhas, leads, fontes, pontuações, aprovações e estados do pipeline. |
| Arquivos e artefatos | Cloudflare R2, quando necessário | Evidências arquivadas e arquivos gerados. Evitar armazenar cópias desnecessárias de conteúdo de terceiros. |
| Execução assíncrona | Cloudflare Queues; Cloudflare Workflows se houver processos longos que precisem de etapas duráveis e retomada | Processar lotes sem manter uma requisição HTTP aberta; retries e retomada controlada. |
| Navegação automatizada | Cloudflare Browser Run com Playwright/Puppeteer, quando disponível e apropriado | Abrir páginas, observar conteúdo renderizado e extrair informações permitidas. Não depende de Playwright MCP em produção. |
| IA | Adaptador de provedor: Workers AI ou API externa compatível, selecionado por custo, qualidade e disponibilidade | Pesquisa assistida, extração estruturada, análise de evidências e geração de conteúdo. Não acoplar a lógica de negócio a um único modelo. |
| Configuração e segredos | Variáveis de ambiente e Cloudflare Secrets | Configurações e credenciais sem incluí-las no repositório. |
| Deploy | Wrangler e Cloudflare | Desenvolvimento, publicação e configuração de Workers e recursos vinculados. |
| Versionamento | Git e GitHub | Código-fonte, instruções, templates e documentação. |

Documentação oficial: [Workers](https://developers.cloudflare.com/workers/), [D1](https://developers.cloudflare.com/d1/), [Queues](https://developers.cloudflare.com/queues/), [Workflows](https://developers.cloudflare.com/workflows/), [Browser Run](https://developers.cloudflare.com/browser-run/), [Workers AI](https://developers.cloudflare.com/workers-ai/), [R2](https://developers.cloudflare.com/r2/).

## Implementação mínima recomendada

Começar com **TypeScript + Cloudflare Workers + D1 + uma interface simples**. Adicionar Queues para lotes/execução em segundo plano quando necessário. Incluir Browser Run e o provedor de IA atrás de interfaces pequenas, para permitir troca de estratégia sem reescrever as regras do pipeline. Adicionar R2 e Workflows apenas quando os requisitos de armazenamento ou durabilidade exigirem.

Não criar um microserviço por etapa. Um Worker e módulos TypeScript organizados são suficientes para a primeira versão.

## Pipeline do produto

1. Configurar oferta, região, segmento, quantidade e critérios de qualificação.
2. Descobrir fontes públicas ou autorizadas e coletar evidências rastreáveis.
3. Normalizar e deduplicar negócios, preservando URL e data de consulta.
4. Qualificar com critérios explícitos, evidências favoráveis, sinais contrários e confiança.
5. Exibir resultados para aprovação humana.
6. Somente após aprovação, gerar uma demonstração usando templates versionados e conteúdo autorizado.
7. Entregar a demonstração e uma mensagem sugerida para revisão e envio manual.
8. Registrar estados, falhas, consumo e auditoria sem coletar dados além do necessário.

## Regras de simplicidade e custo

- Nenhuma dependência de harness de desenvolvimento em produção.
- Não exigir CRM externo, SaaS de scraping, API paga de mapas ou plataforma de enriquecimento para a primeira versão.
- Não assumir que Workers AI ou Browser Run serão gratuitos ou ilimitados; medir custos e limites reais antes de escalar.
- Manter o provedor de IA substituível e definir limites de consumo por execução.
- Não adicionar ORM, framework frontend pesado, vetor database ou arquitetura de microserviços sem requisito demonstrado.
- Playwright MCP pode continuar sendo ferramenta de desenvolvimento manual, mas a execução do produto deve usar APIs/Bindings da Cloudflare ou integrações explícitas.

## Acesso, privacidade e direitos

Respeitar termos das fontes, limites de acesso, privacidade e legislação aplicável. Não contornar autenticação, CAPTCHA, paywalls ou mecanismos de proteção. Não presumir que imagens, vídeos, avaliações ou marcas de terceiros podem ser copiados e republicados. Usar ativos autorizados, links ou placeholders e identificar demonstrações não oficiais.

## Estado atual

Esta é a stack-alvo documentada, não uma declaração de que os serviços já foram configurados ou de que o pipeline já funciona. Antes de afirmar implementação, criar o código, configurar recursos Cloudflare, executar testes e validar o fluxo real.
