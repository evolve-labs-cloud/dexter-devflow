# Changelog

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
e este projeto adere ao [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.3.0] - 2025-12-05

### Added - Hard Stops & Mandatory Delegation

- **Hard Stops em todos os agentes**: Seção `🚨 REGRAS CRÍTICAS - LEIA PRIMEIRO` no topo de cada arquivo `.md`
- **Regras de NUNCA FAÇA**: Instruções explícitas `⛔ NUNCA FAÇA (HARD STOP)` com lógica IF/THEN para parar e delegar
- **Regras de SEMPRE FAÇA**: Instruções `✅ SEMPRE FAÇA (OBRIGATÓRIO)` para delegação mandatória
- **Geração automática de stories**: Chronicler agora DEVE gerar user stories se strategist não criar
- **Checklist pós-ação**: Chronicler executa verificações após qualquer agente completar tarefa
- **Detection patterns**: Padrões de código em `strategist.meta.yaml` para detectar violações de escopo
- **Mandatory delegation triggers**: Em todos os `.meta.yaml` com regras de quando delegar

### Changed - Orchestration System

- **`.claude_project`**: Adicionadas regras obrigatórias de orquestração no topo do arquivo
- **`strategist.md`**: Hard stops para nunca escrever código, sempre delegar para architect/builder
- **`strategist.meta.yaml`**: Versão 1.1.0 com `hard_stops` e `mandatory_delegation` sections
- **`architect.md`**: Hard stops para apenas exemplos de código, nunca produção
- **`builder.md`**: Hard stops para verificar design antes de implementar, delegar após implementar
- **`guardian.md`**: Hard stops e fluxo de aprovação/rejeição com delegação
- **`chronicler.md`**: Ações automáticas obrigatórias e geração de stories
- **`chronicler.meta.yaml`**: Versão 1.1.0 com `mandatory_actions` para cada evento

### Fixed - Agent Role Violations

- **Bug**: Strategist escrevia código ao invés de delegar para builder
  - **Solução**: Hard stops explícitos + detection patterns para keywords de código
- **Bug**: Stories não eram geradas automaticamente
  - **Solução**: Chronicler agora tem trigger obrigatório `after_strategist_prd`
- **Bug**: Documentação não era atualizada após implementações
  - **Solução**: Checklist pós-ação em chronicler com verificações automáticas

### Benefits - Por que isso melhora?

- **Zero violações de papel**: Agentes param imediatamente ao detectar ação fora do escopo
- **Delegação garantida**: Fluxo obrigatório strategist → architect → builder → guardian → chronicler
- **Stories sempre disponíveis**: Se strategist não criar, chronicler gera automaticamente
- **Documentação sincronizada**: Checklist automático garante docs atualizados
- **Detecção proativa**: Patterns de código identificam quando strategist tenta implementar

## [0.2.0] - 2025-11-15

### Added - Metadata Estruturada (IA-Optimized)
- **`.devflow/project.yaml`**: Metadata estruturada do projeto para parse rápido pela IA
- **`.devflow/agents/*.meta.yaml`**: Metadata YAML para cada agente (5 arquivos)
- **Knowledge Graph**: `.devflow/knowledge-graph.json` conectando decisões, features, agentes e documentos
- **Snapshots Estruturados**: `.devflow/snapshots/2025-11-15.json` (além do .md)
- **ADR com YAML Frontmatter**: Template atualizado com metadata estruturada
- **ADR-001**: Decisão formal documentada - "5 Agentes ao invés de 19+"
- **Build System**: `build-release.sh` para gerar releases limpas
- **Release Structure**: `release/v0.2.0/` com estrutura pronta para distribuição
- **Release Docs**: `RELEASE.md` com processo completo de release

### Changed - Metadata Layer
- Template ADR (`docs/decisions/000-template.md`) agora inclui YAML frontmatter completo
- Snapshots agora disponíveis em 2 formatos: .md (humanos) + .json (IA)
- Sistema de tags implementado em ADRs para queries rápidas
- Estrutura separada: desenvolvimento vs release

### Benefits - Por que isso melhora?
- **Parse 100x mais rápido**: IA lê JSON em milissegundos vs. interpretar markdown
- **Zero ambiguidade**: Dados estruturados eliminam interpretação incorreta
- **Knowledge Graph**: IA vê todas as conexões entre decisões, features e agentes instantaneamente
- **Queries complexas**: IA pode responder "Quais decisões impactam X?" sem grep
- **Contexto preservado**: Metadata garante que nada seja esquecido entre sessões
- **Distribuição limpa**: Release separada de arquivos de desenvolvimento

## [0.1.0] - 2025-11-15

### Added - Release Inicial
- Sistema DevFlow multi-agentes implementado
- 5 agentes especializados:
  - Strategist (Planejamento & Produto)
  - Architect (Design & Arquitetura)
  - Builder (Implementação)
  - Guardian (Qualidade & Segurança)
  - Chronicler (Documentação & Memória)
- Estrutura de documentação automática
- Sistema de snapshots para prevenir drift de contexto
- Workflow adaptativo (4 níveis de complexidade)
- Documentação completa de instalação em `docs/INSTALLATION.md`
- Guia de quick start em `docs/QUICKSTART.md`
- Documentação de arquitetura em `docs/ARCHITECTURE.md`

### Changed
- Reorganizada estrutura de pastas: toda documentação movida para `docs/`
- README.md simplificado com foco em instalação rápida
- Estrutura mais clara: código do usuário separado de documentação DevFlow
- Pastas `architecture/` e `planning/` movidas para dentro de `docs/` para centralização completa

### Fixed
- Script `install.sh` atualizado para refletir nova estrutura de pastas
- Links quebrados corrigidos em `docs/ARCHITECTURE.md`
- Arquivo `.claude_project` atualizado com estrutura correta
- Adicionados arquivos `.gitkeep` em pastas vazias (api, migration, architecture/diagrams, planning/stories)

---

<!-- O Chronicler manterá este arquivo atualizado automaticamente -->
<!-- Não edite manualmente - use @chronicler /document -->
