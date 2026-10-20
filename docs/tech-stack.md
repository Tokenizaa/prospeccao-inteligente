# Stack tecnológica e arquitetura padrão

## Decisão

O padrão inicial é **agent-first, local-first e baseado em arquivos**. A primeira implementação será um conjunto de instruções e skills executadas por um harness de agente, não uma aplicação SaaS com backend próprio.

O repositório atual contém documentação e instruções. Ainda não contém pipeline executável, dependências instaladas ou integrações configuradas.

## Tecnologias padrão

| Camada | Padrão inicial | Função |
|---|---|---|
| Instruções e skills | Markdown | Fluxos, critérios, prompts e procedimentos reutilizáveis. |
| Harness | OpenCode como ambiente de referência; outros harnesses compatíveis são aceitos | Executar as instruções e coordenar as etapas. |
| Navegação web | Playwright MCP | Navegar em páginas públicas no navegador e observar contexto visual quando permitido. |
| Código complementar | TypeScript/Node.js somente se forem necessários scripts determinísticos | Normalização, validação e automações locais que não devem depender apenas do prompt. |
| IA | Modelo já disponível no harness | Pesquisa, análise de evidências, qualificação e produção de conteúdo; sem provedor obrigatório. |
| Armazenamento inicial | Arquivos locais Markdown, JSON e pastas por execução | Configurações, evidências, decisões humanas, relatórios e artefatos. |
| Templates de demonstração | HTML/CSS/JS ou template do framework pertinente à entrega | Reutilizar modelos por segmento sem criar plataforma de publicação própria. |
| Versionamento | Git e GitHub | Versionar instruções e templates genéricos; não publicar dados pessoais nem segredos. |

## Pipeline padrão

1. Configurar oferta, região, segmento, quantidade de leads, critérios de qualificação e fontes permitidas.
2. Pesquisar o mercado e documentar hipóteses, sem apresentá-las como fatos comprovados.
3. Encontrar negócios por navegação assistida e fontes públicas permitidas; guardar URL e data da consulta.
4. Avaliar atividade, reputação, canais digitais e sinais concretos de oportunidade. A ausência de site, isoladamente, não qualifica um lead.
5. Produzir pontuação explicável com evidências favoráveis, sinais contrários, lacunas e confiança.
6. Solicitar aprovação humana antes de produzir a demonstração.
7. Para leads aprovados, gerar um protótipo claramente identificado como demonstração não solicitada e não oficial.
8. Entregar arquivos e uma sugestão de mensagem para revisão e envio manual. Não enviar mensagens automaticamente por padrão.
9. Registrar decisões, fontes, resultados e falhas localmente, coletando somente os dados necessários.

## Não incluir na primeira versão

- Backend, API pública, SaaS ou painel administrativo próprios.
- Banco de dados obrigatório, ORM ou migrations.
- Zod, Vitest ou Playwright Test como dependências obrigatórias. Playwright MCP é uma ferramenta de navegação e não exige, por si só, o pacote Playwright Test.
- Serviços pagos de scraping, bases comerciais ou enriquecimento.
- Provedor de IA pago adicional imposto pelo projeto.
- Publicação automática de sites ou disparo automático de mensagens.

Adicionar esses componentes apenas quando houver necessidade concreta que justifique o custo e a complexidade.

## Custos, acesso e direitos

Playwright MCP não garante acesso gratuito, ilimitado ou autorizado a qualquer site. O uso do modelo pode estar coberto por uma assinatura existente ou ser cobrado conforme o provedor e o consumo. Não prometer prospecção ilimitada sem custo.

Respeitar termos das fontes, limites de acesso, privacidade e legislação aplicável. Não contornar CAPTCHA, autenticação, paywalls ou mecanismos de proteção. Não presumir que imagens, vídeos, avaliações ou marcas de terceiros podem ser copiados e republicados. Preferir ativos autorizados, links ou placeholders, e identificar claramente demonstrações não oficiais.

## Quando evoluir para uma aplicação

Só introduzir TypeScript/Node.js como runtime, validação estruturada, testes, banco, filas, API ou interface própria quando requisitos concretos — por exemplo, execução concorrente persistente, histórico compartilhado ou integração com produto — justificarem essa evolução. Até lá, manter o fluxo simples, local, inspecionável e executado pelo harness existente.
