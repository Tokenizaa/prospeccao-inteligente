# Prospecção Inteligente

Biblioteca pública e versionada de instruções, padrões e contratos para agentes de IA implementarem módulos de **prospecção, geração e qualificação de leads** em diferentes produtos digitais.

O repositório é uma fonte de instruções reutilizáveis — não é, por si só, um plugin, CRM ou aplicação executável.

## Objetivos

- Encontrar e pesquisar potenciais clientes usando fontes permitidas e rastreáveis.
- Enriquecer e qualificar leads com critérios explícitos e configuráveis por segmento.
- Registrar fontes, evidências, confiança, data de coleta e limitações.
- Integrar a capacidade a diferentes produtos por contratos API-first.
- Permitir implementação por diferentes agentes e harnesses, sem dependência de fornecedor.
- Preservar projetos existentes e validar mudanças antes de considerá-las concluídas.

## Princípio de trabalho

**ENTENDER → PRESERVAR → MELHORAR → VALIDAR**

Nenhum agente deve alterar um projeto antes de entender seu estado atual, seus contratos, dados, segurança e fluxo de execução. Não substituir sistemas existentes sem evidência e plano explícito.

## Compatibilidade

As instruções são independentes de ferramenta e podem ser consumidas por OpenCode, Claude Code, Google AI Studio e outros agentes. Consulte primeiro [AGENTS.md](AGENTS.md).

## Conteúdo

- [Stack tecnológica recomendada](docs/tech-stack.md) — linguagem, runtime, bibliotecas e critérios de escolha\n- [Arquitetura](docs/architecture.md)
- [Contrato de integração API-first](docs/integration-contract.md)
- [Segurança e privacidade](docs/security.md)
- [Sistema de design](docs/design-system.md)
- [Criar um módulo de prospecção](instructions/implement-prospecting.md)
- [Criar uma implementação white label](instructions/create-white-label.md)
- [Adaptar um projeto existente](instructions/adapt-existing-project.md)
- [Configuração por segmento](templates/segment-config.md)
- [Checklist de integração](templates/integration-checklist.md)
- [Registro de decisões arquiteturais](docs/decisions/README.md)
- [Exemplo: serviços jurídicos](examples/legal/README.md)
- [Exemplo: beleza e bem-estar](examples/beauty/README.md)

## Escopo e limites

A biblioteca orienta a construção; cada produto continua responsável por suas credenciais, infraestrutura, permissões, conformidade legal, custos e operação. Não inventar dados nem apresentar inferências como fatos. Respeitar termos das fontes, legislação aplicável, privacidade, direitos dos titulares e mecanismos de exclusão.

## Evolução

Toda mudança relevante deve atualizar a documentação correspondente e o [CHANGELOG](CHANGELOG.md). Decisões estruturais devem ser registradas em `docs/decisions/`.
