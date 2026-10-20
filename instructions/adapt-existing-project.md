# Instrução: adaptar um projeto existente

Aplicar o princípio **ENTENDER → PRESERVAR → MELHORAR → VALIDAR**.

## 1. Entender

- Ler documentação e instruções locais.
- Inspecionar estrutura, branch, alterações pendentes, commits recentes e estado real do produto.
- Identificar fluxos de usuário, contratos, esquema de dados, autenticação, integrações, deploy e testes atuais.
- Localizar a capacidade equivalente antes de propor novos arquivos, telas ou serviços.
- Separar evidências, hipóteses e dúvidas.

## 2. Preservar

- Não sobrescrever trabalho local ou mudanças de terceiros.
- Manter contratos e comportamentos válidos.
- Evitar migrações destrutivas; quando indispensáveis, preparar backup, compatibilidade e reversão.
- Não reutilizar testes obsoletos como prova de comportamento atual sem verificar sua pertinência.

## 3. Melhorar

- Descrever a mudança mínima que resolve a necessidade.
- Reutilizar padrões e infraestrutura já adotados.
- Atualizar documentação e testes afetados.
- Evitar refatorações não relacionadas e dependências desnecessárias.

## 4. Validar

- Executar verificações focadas e depois as verificações de regressão relevantes.
- Testar o fluxo integrado, não apenas funções isoladas, quando possível.
- Conferir logs, persistência e resultado visível.
- Distinguir teste local, staging e produção; não declarar validação de produção se ela não ocorreu.
- Informar bloqueios concretos e evidências reproduzíveis.

## Entrega

Registrar resumo, arquivos modificados, decisões, comandos executados, resultados, limitações e commit. Uma implementação não está concluída apenas porque o código compila ou foi commitado.
