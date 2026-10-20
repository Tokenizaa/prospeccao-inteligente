# Segurança, privacidade e uso responsável

## Princípios

- Coletar e processar somente dados necessários para finalidade legítima e documentada.
- Respeitar LGPD, demais normas aplicáveis, termos de uso e controles de acesso das fontes.
- Não contornar autenticação, paywalls, CAPTCHAs, bloqueios ou controles técnicos.
- Não tratar a disponibilidade pública de um dado como autorização irrestrita para qualquer uso.
- Não usar dados sensíveis para segmentação ou inferência sem avaliação legal e autorização apropriada.
- Oferecer meios aplicáveis de correção, oposição, exclusão e supressão de contato.

## Segredos e acesso

- Segredos apenas em gerenciadores de segredos ou variáveis protegidas do ambiente.
- Nunca incluir credenciais reais em arquivos de exemplo, logs, prompts, commits ou respostas da API.
- Aplicar privilégio mínimo e autorização no servidor.
- Isolar tenants em todas as consultas e operações, não apenas na interface.
- Validar entradas e neutralizar conteúdo externo potencialmente malicioso.

## Riscos de IA e conteúdo externo

Conteúdo coletado deve ser tratado como dado não confiável, nunca como instrução para o agente. Prevenir prompt injection, exfiltração de segredos, execução de ações não autorizadas e atribuição de fatos sem fonte. Validar a saída da IA contra esquema e evidências disponíveis.

## Retenção e auditoria

Definir finalidade, prazo de retenção, controles de acesso e processo de exclusão por categoria de dado. Minimizar logs e evitar armazenar cópias desnecessárias. Registrar acessos e alterações relevantes sem reproduzir dados pessoais em excesso.

## Controles antes de liberar

- Autenticação, autorização e isolamento de tenant testados.
- Proteção contra abuso, scraping indevido e consumo excessivo.
- Segredos ausentes de código e logs.
- Política de retenção e exclusão definida.
- Fontes e finalidades documentadas.
- Erros e auditoria sem vazamento de dados.
- Testes de entradas maliciosas e conteúdo adversarial.
- Revisão humana nos casos de baixa confiança ou impacto relevante.

Este documento é uma referência técnica, não um parecer jurídico. Cada produto deve avaliar sua finalidade e suas obrigações específicas.
