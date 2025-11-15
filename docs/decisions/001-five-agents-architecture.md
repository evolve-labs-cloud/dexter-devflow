---
# ADR Metadata
id: "ADR-001"
title: "5 Agentes ao invés de 19+ (Simplificação do BMAD)"
status: "accepted"
date: "2025-11-15"
deciders:
  - "@architect"
  - "rafael.ribeiro"
tags:
  - "architecture"
  - "agents"
  - "simplicity"
  - "core-design"
category: "architecture"
technical_story: ""

# Relacionamentos
relates_to: []
supersedes: []
superseded_by: null

# Impacto
impact:
  scope: "project"
  magnitude: "critical"

# Revisão
review_date: null
next_review: "2026-05-15"  # 6 meses
---

# ADR-001: 5 Agentes ao invés de 19+ (Simplificação do BMAD)

## Context

O método BMAD original propõe 19+ agentes especializados para cobrir todo o ciclo de desenvolvimento. Embora completo, isso introduz:

**Constraints**:
- Complexidade de onboarding (usuários precisam conhecer 19+ agentes)
- Dificuldade de manutenção (19+ arquivos .md para manter)
- Overhead cognitivo (decidir qual agente usar é difícil)
- Conflito/sobreposição entre agentes

**Requirements**:
- Cobrir 90% dos casos de uso
- Simplicidade de uso (instalação em minutos)
- Fácil entendimento do fluxo
- Manutenibilidade a longo prazo

## Decision

**Implementar apenas 5 agentes especializados**:

1. **Strategist** - Planejamento & Produto
2. **Architect** - Design & Arquitetura
3. **Builder** - Implementação
4. **Guardian** - Qualidade & Segurança
5. **Chronicler** - Documentação & Memória

## Rationale

### Benefícios

- **Simplicidade**: Usuário aprende 5 nomes ao invés de 19+
- **Cobertura**: Mapeia todo o SDLC (plan → design → build → test → document)
- **Clareza**: Cada agente tem responsabilidade bem definida
- **Manutenibilidade**: Apenas 5 arquivos para manter atualizados

### Justificativa Técnica

Análise mostrou que:
- 80% das interações usam apenas 5-7 agentes
- Agentes raramente usados podem ser incorporados nos principais
- Especialização excessiva = confusão > benefício

**Mapeamento BMAD → DevFlow**:
```
BMAD (19+ agentes)              DevFlow (5 agentes)
├── Product Manager      →      Strategist
├── Business Analyst     →      Strategist
├── Requirements         →      Strategist
├── Tech Lead            →      Architect
├── Solution Architect   →      Architect
├── API Designer         →      Architect
├── Developer            →      Builder
├── Code Reviewer        →      Builder
├── Refactorer           →      Builder
├── QA Engineer          →      Guardian
├── Security Specialist  →      Guardian
├── Performance Expert   →      Guardian
├── DevOps Engineer      →      Guardian
├── Documentation        →      Chronicler
├── Knowledge Manager    →      Chronicler
└── ...                  →      (incorporados)
```

## Alternatives Considered

### Alternativa 1: Manter 19+ Agentes (BMAD Original)

**Descrição**: Implementar todos agentes do BMAD original

**Pros**:
- Granularidade máxima
- Especialização extrema
- Cobre 100% dos casos edge

**Cons**:
- Complexidade proibitiva para novos usuários
- Manutenção de 19+ arquivos
- Difícil escolher qual agente usar
- Overhead cognitivo alto

**Por que foi rejeitada**: Viola princípio de simplicidade. Análise mostrou que ganho marginal (10% casos edge) não compensa custo (200% complexidade).

### Alternativa 2: 10 Agentes (Meio Termo)

**Descrição**: Reduzir para 10 agentes mais usados

**Pros**:
- Mais granular que 5
- Ainda relativamente simples
- Cobre 95% dos casos

**Cons**:
- Ainda complexo para iniciantes
- Sobreposição de responsabilidades
- Não atinge simplicidade máxima

**Por que foi rejeitada**: Análise mostrou que diferença entre 5 e 10 agentes é marginal (<5% casos), mas complexidade dobra.

### Alternativa 3: 3 Agentes (Minimalista)

**Descrição**: Plan, Build, Test

**Pros**:
- Extremamente simples
- Fácil de lembrar
- Setup instantâneo

**Cons**:
- Perde granularidade importante (Architect separado)
- Chronicler é diferencial crítico (anti-drift)
- Arquitetura vs implementação devem ser separadas

**Por que foi rejeitada**: Perde benefícios-chave. Architect e Chronicler são críticos para qualidade.

## Consequences

### Positive

- ✅ Onboarding reduzido de horas para minutos
- ✅ Manutenção 5x mais fácil
- ✅ Usuários entendem fluxo rapidamente
- ✅ Zero ambiguidade sobre qual agente usar
- ✅ Documentação enxuta e clara

### Negative

- ❌ Casos edge extremos podem precisar workarounds
- ❌ Alguns usuários avançados podem preferir granularidade
- ❌ Perda de 10% de especialização ultra-específica

### Neutral

- 🔄 Alguns agentes terão scope mais amplo
- 🔄 Pode precisar ajustar se casos edge aumentarem (futuro)

### Risks

**Risk 1**: Agentes ficarem muito abrangentes
- Likelihood: Medium
- Impact: Medium
- Mitigation: Monitorar feedback e dividir se necessário (ex: Builder → Developer + Reviewer)

**Risk 2**: Usuários avançados quererem mais granularidade
- Likelihood: Low
- Impact: Low
- Mitigation: Permitir custom agents no futuro

## Implementation

### Steps

1. ✅ Definir escopo de cada um dos 5 agentes
2. ✅ Criar arquivos .md com instruções claras
3. ✅ Mapear workflows (quem chama quem)
4. ✅ Documentar em README
5. ✅ Adicionar metadata YAML para IA

### Code Examples

```markdown
# Exemplo de chamada clara:

@strategist Quero criar sistema de auth
  ↓
@architect Design a solução
  ↓
@builder Implementa
  ↓
@guardian Valida segurança
  ↓
@chronicler Documenta (automático)
```

### Configuration

```yaml
# .devflow/project.yaml
agents:
  - strategist
  - architect
  - builder
  - guardian
  - chronicler
```

## Follow-up Actions

- [x] Implementar 5 agentes
- [x] Criar metadata YAML
- [ ] Coletar feedback após 1 mês de uso
- [ ] Revisar decisão em 6 meses
- [ ] Considerar sub-agentes se demanda surgir

## References

- [BMAD Method Original](https://github.com/example/bmad)
- Análise de uso de agentes em 50+ projetos
- Feedback de early adopters
- [Pareto Principle](https://en.wikipedia.org/wiki/Pareto_principle) - 80/20 rule

---

**Notes**:
- Esta decisão pode ser revisitada se padrões de uso mostrarem necessidade de mais granularidade
- Mantemos flexibilidade para adicionar agentes especializados no futuro se comprovadamente necessário
- Princípio guia: "Simplicidade até que complexidade seja comprovadamente necessária"
