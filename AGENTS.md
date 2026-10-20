# Instruções para agentes

Este arquivo é a entrada canônica para qualquer agente ou harness que use esta biblioteca.

## Objetivo

Executar um pipeline reutilizável de prospecção e qualificação de leads com IA, com opção de produzir demonstrações comerciais após aprovação humana.

## Princípio obrigatório: entender, preservar, melhorar, validar

1. **ENTENDER** — ler o README e os documentos relevantes; inspecionar o ambiente e separar fatos de hipóteses.
2. **PRESERVAR** — não substituir ferramentas, dados ou fluxos válidos sem necessidade demonstrada.
3. **MELHORAR** — implementar a menor solução completa; evitar arquitetura e dependências desnecessárias.
4. **VALIDAR** — verificar o fluxo real e relatar exatamente o que foi e não foi testado.

## Stack padrão

- Consultar [docs/tech-stack.md](docs/tech-stack.md) antes de definir tecnologias.
- Padrão inicial: instruções e skills em Markdown, harness já disponível, Playwright MCP para navegação quando autorizado e arquivos locais para evidências, decisões e resultados.
- Não criar backend, SaaS, banco de dados, API, ORM, sistema de scraping pago ou painel próprio na primeira versão sem requisito concreto.
- TypeScript/Node.js só deve entrar quando scripts determinísticos forem realmente necessários.
- Não exigir provedor de IA específico. Usar o modelo já disponível no harness, quando adequado.

## Regras operacionais

- Não qualificar um lead apenas pela ausência de site. Exigir evidências de oportunidade comercial e registrar sinais contrários.
- Registrar fontes e datas de consulta; não inventar dados, fontes ou resultados.
- Solicitar aprovação humana antes de gerar uma demonstração ou preparar uma abordagem específica para um lead.
- Não enviar mensagens nem publicar demonstrações automaticamente por padrão.
- Respeitar termos das fontes, limites de acesso, privacidade e legislação aplicável. Não contornar autenticação, CAPTCHA, paywalls ou proteções.
- Não presumir que imagens, vídeos, avaliações ou marcas de terceiros podem ser copiados e republicados.
- Não expor chaves, tokens, dados pessoais ou segredos em logs, commits ou exemplos.
- Não realizar alterações destrutivas ou operações externas irreversíveis sem autorização.
- Se houver bloqueio, concluir o que for possível com segurança e declarar o bloqueio específico.
- Não tratar plano, análise ou commit como prova de funcionamento.

## Independência de ferramenta

OpenCode é um ambiente de referência, não uma dependência obrigatória. As instruções devem poder ser adaptadas a outros harnesses que suportem arquivos de instrução, ferramentas e navegação.

## Relato final obrigatório

Informar objetivo concluído, arquivos alterados, validações executadas, resultados, riscos, pendências e referência verificável. Nunca declarar testes não executados como aprovados.
