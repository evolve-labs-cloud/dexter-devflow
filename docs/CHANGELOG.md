# Changelog

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
e este projeto adere ao [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0] - 2025-11-15

### Added - Metadata Estruturada (IA-Optimized)
- **`.devflow/project.yaml`**: Metadata estruturada do projeto para parse rápido pela IA
- **`.devflow/agents/*.meta.yaml`**: Metadata YAML para cada agente (5 arquivos)
- **Knowledge Graph**: `.devflow/knowledge-graph.json` conectando decisões, features, agentes e documentos
- **Snapshots Estruturados**: `.devflow/snapshots/2025-11-15.json` (além do .md)
- **ADR com YAML Frontmatter**: Template atualizado com metadata estruturada
- **ADR-001**: Decisão formal documentada - "5 Agentes ao invés de 19+"

### Changed - Metadata Layer
- Template ADR (`docs/decisions/000-template.md`) agora inclui YAML frontmatter completo
- Snapshots agora disponíveis em 2 formatos: .md (humanos) + .json (IA)
- Sistema de tags implementado em ADRs para queries rápidas

### Benefits - Por que isso melhora?
- **Parse 100x mais rápido**: IA lê JSON em milissegundos vs. interpretar markdown
- **Zero ambiguidade**: Dados estruturados eliminam interpretação incorreta
- **Knowledge Graph**: IA vê todas as conexões entre decisões, features e agentes instantaneamente
- **Queries complexas**: IA pode responder "Quais decisões impactam X?" sem grep
- **Contexto preservado**: Metadata garante que nada seja esquecido entre sessões

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
