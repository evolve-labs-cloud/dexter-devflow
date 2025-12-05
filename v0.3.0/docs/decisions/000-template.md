---
# ADR Metadata (YAML Frontmatter)
id: "ADR-000"
title: "Template de Architecture Decision Record"
status: "template"  # proposed | accepted | deprecated | superseded | template
date: "YYYY-MM-DD"
deciders:
  - "@architect"
  - "team-member"
tags:
  - "template"
  - "example"
category: "process"  # architecture | infrastructure | code | process | security
technical_story: ""  # link para issue/story se aplicável

# Relacionamentos
relates_to: []  # ["ADR-001", "ADR-002"]
supersedes: []  # ["ADR-XXX"] se substituir outra decisão
superseded_by: null  # "ADR-XXX" se foi substituída

# Impacto
impact:
  scope: "project"  # component | module | project | organization
  magnitude: "medium"  # low | medium | high | critical

# Revisão
review_date: null  # YYYY-MM-DD
next_review: null  # YYYY-MM-DD
---

# ADR-000: Template de Architecture Decision Record

## Context

[Descreva o contexto e o problema que está sendo resolvido]

Considerações:
- Constraint 1
- Constraint 2
- Requirement 1

## Decision

[Descreva a decisão tomada]

## Rationale

[Explique POR QUÊ esta decisão foi tomada]

### Benefícios
- Benefício 1
- Benefício 2

### Justificativa Técnica
[Detalhes técnicos que justificam a decisão]

## Alternatives Considered

### Alternativa 1: [Nome]
**Descrição**: [O que é]

**Pros:**
- Pro 1
- Pro 2

**Cons:**
- Con 1
- Con 2

**Por que foi rejeitada**: [Razão]

### Alternativa 2: [Nome]
[Similar ao acima]

## Consequences

### Positive
- Consequência positiva 1
- Consequência positiva 2

### Negative
- Trade-off 1
- Dívida técnica introduzida

### Neutral
- Mudança que é neutra

### Risks
**Risk 1**: [Descrição]
- Likelihood: [Low/Medium/High]
- Impact: [Low/Medium/High]
- Mitigation: [Como mitigar]

## Implementation

[Como implementar esta decisão]

### Steps
1. Passo 1
2. Passo 2
3. Passo 3

### Code Examples
```typescript
// Exemplo de código se aplicável
```

### Configuration
```yaml
# Configurações necessárias
```

## Follow-up Actions

- [ ] Action item 1
- [ ] Action item 2
- [ ] Action item 3

## References

- [Link 1](url)
- [Link 2](url)
- [Related ADR-XXX](./XXX-topic.md)

---

**Notes**:
- Este ADR substitui: [ADR-XXX] (se aplicável)
- Este ADR é superseded por: [ADR-XXX] (se aplicável)
