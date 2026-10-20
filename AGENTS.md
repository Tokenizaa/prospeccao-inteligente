# Instruções para agentes

Este arquivo é a entrada canônica para qualquer agente ou harness que trabalhe com esta biblioteca ou a aplique a um produto.

## Objetivo

Implementar módulos reutilizáveis de prospecção, geração e qualificação de leads com IA, configuráveis por segmento e integráveis a diferentes produtos por contratos claros.

## Regra obrigatória: entender, preservar, melhorar, validar

1. **ENTENDER** — inspecionar o repositório, instruções existentes, arquitetura, fluxos, dados, integrações, autenticação, testes e estado de deploy. Separar fatos verificados de hipóteses.
2. **PRESERVAR** — manter comportamentos, contratos, dados, padrões e decisões válidas. Não apagar, recriar ou migrar sem necessidade demonstrada e plano de reversão.
3. **MELHORAR** — implementar a menor mudança completa que resolva o problema real. Evitar duplicar páginas, menus, serviços, abstrações ou configurações.
4. **VALIDAR** — executar verificações proporcionais à mudança e testar o caminho real de uso. Informar exatamente o que passou, falhou, não foi executado e por quê.

## Regras operacionais

- Ler o README e os documentos relevantes antes de implementar.
- Não assumir framework, banco, hospedagem, gateway, provedor de IA ou ferramenta de agente.
- Não tratar um plano, uma análise ou um commit como prova de funcionamento.
- Não inventar fontes, leads, campos, resultados de teste, permissões ou estado de produção.
- Não expor chaves, tokens, dados pessoais ou segredos em logs, commits ou exemplos.
- Preferir APIs explícitas, contratos versionados e configuração por segmento.
- Não introduzir dependências ou infraestrutura sem justificar necessidade e custo.
- Não fazer alterações destrutivas nem operações externas irreversíveis sem autorização.
- Se houver bloqueio, concluir tudo que for possível com segurança e registrar o bloqueio específico, sem declarar a tarefa concluída.
- Documentar decisões que afetem arquitetura, segurança, compatibilidade ou dados.

## Independência de ferramenta

Estas instruções não exigem OpenCode, Claude Code, Google AI Studio ou qualquer harness específico. Use os recursos disponíveis no ambiente e respeite suas permissões reais.

## Relato final obrigatório

Informe: objetivo concluído; arquivos e contratos alterados; validações executadas e resultados; riscos ou pendências; commit ou referência verificável. Nunca declarar testes não executados como aprovados.
