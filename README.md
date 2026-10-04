# Kit da Fábrica de SaaS

Pasta de trabalho para conduzir a criação de software com uma IA capaz de ler e editar arquivos. O Codex é o caminho de referência; outras ferramentas de desenvolvimento podem precisar de adaptação. O Kit não inclui acesso à IA nem um software pronto.

## Experiência do cliente
Leia `CLIENTE-LEIA-PRIMEIRO.txt` para o início em linguagem simples. A mensagem inicial oficial é: `Leia o START-HERE.md e comece. Quero criar meu software.`

Use uma cópia do Kit para cada projeto. A IA deve começar pela descoberta, registrar o plano para sua validação e só então construir. Publicação não é automática.

## Mapa das pastas
- `01-comeco-guiado/`: orquestração e modo de uso.
- `02-descoberta/`: entrevista sobre o negócio e seus usuários.
- `03-especificacao/`: regras e primeira versão do produto.
- `04-planejamento/`: arquitetura, segurança inicial e backlog.
- `05-construcao/`: implementação, revisão e correção.
- `06-testes-seguranca/`: QA, verificação de segurança e preparação para publicação.
- `modelos/`: documentos-modelo; `exemplos/`: caso ilustrativo; `assets/`: orientação para arquivos do projeto.
- `docs/`: estado e decisões da sua cópia de trabalho; `scripts/`: verificações locais.

As skills em `.agents/skills/` tornam os fluxos reutilizáveis em agentes compatíveis. As mesmas etapas podem ser seguidas por `START-HERE.md` quando a ferramenta não reconhecer skills.

## Camadas internas
- Beginner Orchestrator
- Discovery Engine
- Product SPEC
- SDD
- Backlog
- TDD
- Code Review
- QA / Red Team
- Self-healing
- Preview Loop
- Production Readiness

## Regra de produto
Vibe Coding por fora. Engenharia estruturada por dentro.

## Security + Architecture OS
Esta edição inclui uma camada formal de AppSec e arquitetura de backend: monólito modular por padrão, critérios para microserviços, threat modeling, route inventory, RLS/database policy standard, tenant-isolation tests, secret scanning, webhook/upload standards e release security gates.

O objetivo não é prometer segurança absoluta. O sistema transforma segurança em requisitos, controles e testes verificáveis, e bloqueia release quando controles críticos aplicáveis falham.
