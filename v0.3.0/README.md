# DevFlow - Sistema Multi-Agentes para Desenvolvimento

Sistema simplificado de multi-agentes especializados para desenvolvimento de software, otimizado para uso com Claude Code.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 🚀 Instalação em 3 Passos

### 1. Clone este repositório
```bash
git clone https://github.com/seu-usuario/devflow.git
cd devflow
```

### 2. Instale no seu projeto
```bash
# Opção A: Script automático (recomendado)
./install.sh /caminho/para/seu-projeto

# Opção B: Manual
cp -r .devflow /caminho/para/seu-projeto/
```

### 3. Comece a usar
```bash
cd /caminho/para/seu-projeto
# No Claude Code:
@strategist Olá! Quero criar [sua feature]
```

**Pronto! Zero configuração necessária.**

---

## 🤖 Os 5 Agentes

Após instalar, você tem acesso a:

| Agente | Função | Uso |
|--------|--------|-----|
| **@strategist** | Planejamento & Produto | Requisitos, PRDs, user stories |
| **@architect** | Design & Arquitetura | Decisões técnicas, ADRs, APIs |
| **@builder** | Implementação | Código, reviews, refactoring |
| **@guardian** | Qualidade & Segurança | Testes, security, performance |
| **@chronicler** | Documentação & Memória | CHANGELOG, snapshots, docs |

---

## 📁 Estrutura Instalada

```
seu-projeto/
├── .devflow/
│   ├── agents/          # 5 agentes especializados
│   └── snapshots/       # Histórico do projeto
│
├── docs/                # Documentação (opcional, mas recomendado)
│   ├── decisions/       # ADRs
│   ├── api/             # Docs de APIs
│   ├── architecture/    # Diagramas e docs técnicos
│   └── planning/        # PRDs e user stories
│
└── seu código...        # Seu código existente
```

---

## 💡 Diferencial: Zero Drift de Contexto

O **@chronicler** mantém automaticamente:
- ✅ CHANGELOG.md atualizado
- ✅ ADRs para decisões importantes
- ✅ Snapshots do projeto (markdown + JSON)
- ✅ Detecção de docs desatualizados
- ✅ **Knowledge Graph** - Conexões entre decisões, features e agentes
- ✅ **Metadata Estruturada** - Parse 100x mais rápido pela IA

**Resultado**: A IA sempre sabe o estado completo do projeto + compreende instantaneamente.

---

## 📚 Documentação

### Guias Principais
- **[Instalação Completa](docs/INSTALLATION.md)** - Guia detalhado
- **[Quick Start](docs/QUICKSTART.md)** - Comece em 5 minutos
- **[Arquitetura](docs/ARCHITECTURE.md)** - Como funciona
- **[Metadata Guide](docs/METADATA_GUIDE.md)** - Sistema de metadata estruturada (v0.2.0+)
- **[Changelog](docs/CHANGELOG.md)** - Histórico de mudanças

### Referência dos Agentes
- [Strategist](.devflow/agents/strategist.md) - [Metadata](.devflow/agents/strategist.meta.yaml)
- [Architect](.devflow/agents/architect.md) - [Metadata](.devflow/agents/architect.meta.yaml)
- [Builder](.devflow/agents/builder.md) - [Metadata](.devflow/agents/builder.meta.yaml)
- [Guardian](.devflow/agents/guardian.md) - [Metadata](.devflow/agents/guardian.meta.yaml)
- [Chronicler](.devflow/agents/chronicler.md) - [Metadata](.devflow/agents/chronicler.meta.yaml)

---

## 🎯 Filosofia

**"Simplicidade sem sacrificar poder"**

- ✅ 5 agentes especializados
- ✅ Zero configuração inicial
- ✅ Workflows adaptativos (4 níveis)
- ✅ Documentação automática nativa
- ✅ Prevenção de drift de contexto

---

## 📜 Licença

MIT License - veja [LICENSE](LICENSE) para detalhes.
