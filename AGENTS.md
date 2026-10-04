# KIT DA FÁBRICA DE SAAS — AI DEVELOPMENT CONSTITUTION

## Missão
Este repositório deve permitir que uma pessoa sem conhecimento de programação crie, altere, teste e publique um SaaS conversando em linguagem natural.

O usuário NÃO é presumido programador. Nunca transfira complexidade técnica para ele quando o agente puder resolvê-la sozinho.

## Experiência desejada
Para o usuário, o fluxo deve parecer:

EXPLICAR → APROVAR → VER FUNCIONANDO → PEDIR MUDANÇAS → PUBLICAR

SPEC, SDD, TDD, backlog, migrations, testes e arquitetura existem nos bastidores.

## Ordem de autoridade
1. Instrução explícita atual do usuário
2. Product SPEC aprovada
3. Change Requests aprovados
4. SDD e ADRs
5. Backlog
6. Código existente

## Bootstrap obrigatório
No início de TODA sessão:
1. Leia `START-HERE.md`.
2. Leia `01-comeco-guiado/BEGINNER-ORCHESTRATOR.md`.
3. Leia `01-comeco-guiado/USER-MODE.yaml`.
4. Leia `docs/project-state.md`.
5. Determine o modo atual: CREATE, CHANGE, FIX, PUBLISH ou EXPLAIN.

Se o projeto for novo, entre automaticamente em CREATE e inicie Discovery.

## Princípios
- SPEC define O QUE construir.
- SDD define COMO construir.
- BACKLOG define EM QUAL ORDEM construir.
- TESTES definem COMPORTAMENTO ESPERADO.
- CÓDIGO implementa o comportamento.
- O repositório é a memória persistente do projeto.

## Regras para usuário leigo
- Não perguntar qual framework, banco, ORM, API style, hospedagem ou biblioteca usar, salvo se isso for requisito explícito do negócio.
- Para decisões técnicas reversíveis, escolher automaticamente a opção mais simples, madura, segura e testável.
- Explicar termos técnicos somente quando forem relevantes para uma ação do usuário.
- Nunca pedir que o usuário edite código manualmente.
- Nunca responder apenas com stack trace ou erro técnico. Diagnosticar, tentar corrigir, testar e traduzir o resultado.
- Quando uma ação externa for inevitável, fornecer UMA instrução por vez, em linguagem simples, dizendo exatamente o que abrir, criar, copiar ou colar.
- Nunca solicitar senha. Secrets devem ser inseridos por mecanismo apropriado de ambiente quando disponível.

## Stack padrão opinativa
Use a stack em `01-comeco-guiado/DEFAULT-STACK.md`, a menos que um requisito real justifique desvio. Registre desvios em ADR.

## TDD
Use RED → GREEN → REFACTOR.
Nunca remover teste apenas para deixar o build verde.

## Self-healing
Quando build, teste, migration, lint, typecheck ou execução falhar:
1. Capture o erro.
2. Classifique a causa provável.
3. Inspecione arquivos e dependências relacionadas.
4. Faça a menor correção segura.
5. Rode novamente.
6. Repita enquanto houver progresso objetivo.
7. Só envolva o usuário se faltar decisão de negócio, credencial/acesso externo, autorização destrutiva ou houver ambiguidade irreversível.

## Segurança
- Nunca contornar autenticação ou autorização.
- Nunca confiar apenas em validação client-side.
- Validar ownership e tenant no servidor.
- Nunca expor secrets.
- Não registrar dados sensíveis sem necessidade.
- Toda operação destrutiva deve ter proteção adequada.

## Mudanças
- Feature fora da SPEC exige Change Request.
- Mudança arquitetural relevante exige ADR.
- Fazer análise de impacto antes de alterar comportamento existente.

## Estado persistente
Após trabalho relevante, atualizar `docs/project-state.md`.
Após Story concluída, atualizar backlog, traceability e project-state.

## Security + Architecture OS — obrigatório
Antes de DESIGN, leia:
- `06-testes-seguranca/padroes/SECURITY-CONSTITUTION.md`
- `06-testes-seguranca/padroes/BACKEND-ARCHITECTURE.md`
- demais padrões em `06-testes-seguranca/padroes/` aplicáveis ao projeto.

Durante DESIGN siga também `04-planejamento/09-security-architect.md`.
Antes de RELEASE siga `06-testes-seguranca/10-security-verifier.md`.

Regras adicionais:
- Monólito modular é o padrão inicial. Microserviços exigem critérios objetivos e ADR.
- Todo endpoint/route/server action/RPC exposto deve constar da matriz de rotas.
- Todo recurso privado deve ter regra explícita de autorização e tenant/ownership.
- Em sistemas multi-tenant, testes negativos cross-tenant são obrigatórios.
- Se o banco suportar RLS/database policies e houver dados USER_PRIVATE/TENANT_PRIVATE, use-as como defesa em profundidade salvo ADR justificando alternativa.
- Secrets privilegiados nunca podem chegar ao cliente/browser bundle.
- Security gates CRITICAL/HIGH bloqueiam publicação.
- `docs/runtime/security-state.yaml` é a fonte de estado dos gates de segurança.
