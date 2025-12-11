---
# ADR Metadata (YAML Frontmatter)
id: "ADR-EXAMPLE-001"
title: "Escolha de Banco de Dados - PostgreSQL"
status: "example"  # Este é um EXEMPLO - não uma decisão real
date: "2025-01-15"
deciders:
  - "@architect"
  - "Rafael"
tags:
  - "example"
  - "database"
  - "infrastructure"
category: "infrastructure"
technical_story: "PROJ-001"

# Relacionamentos
relates_to: []
supersedes: []
superseded_by: null

# Impacto
impact:
  scope: "project"
  magnitude: "high"

# Revisão
review_date: "2025-01-15"
next_review: "2025-07-15"
---

# ADR-EXAMPLE-001: Escolha de Banco de Dados - PostgreSQL

> **NOTA**: Este é um ADR de EXEMPLO para demonstrar o formato esperado.
> Quando @architect tomar decisões reais, ele criará ADRs similares.

## Context

Precisamos escolher um banco de dados para uma aplicação de e-commerce com:
- Catálogo de produtos (20k+ SKUs)
- Pedidos e transações financeiras
- Usuários e autenticação
- Inventário em tempo real

**Considerações**:
- Dados relacionais com integridade referencial
- Transações ACID obrigatórias para pagamentos
- Escala esperada: 10k usuários/mês no primeiro ano
- Equipe familiarizada com SQL

## Decision

**Escolhemos PostgreSQL** como banco de dados principal.

## Rationale

### Por que PostgreSQL?

1. **Transações ACID**: Crítico para e-commerce
   - Pedidos atômicos (payment + inventory + order)
   - Rollback automático em falhas
   - Consistência garantida

2. **Relacionamentos Complexos**:
   - Products ↔ Categories (many-to-many)
   - Orders → OrderItems → Products
   - Users → Addresses → Orders

3. **Data Integrity**:
   - Foreign keys
   - Constraints (unique, check, not null)
   - Triggers para validações

4. **JSON Support**:
   - JSONB para dados flexíveis
   - Melhor dos dois mundos

### Justificativa Técnica

PostgreSQL oferece o melhor equilíbrio entre:
- Modelo relacional maduro
- Features modernas (JSONB, full-text search)
- Performance comprovada
- Ecossistema rico (ORMs, ferramentas)

## Alternatives Considered

### Alternativa 1: MongoDB
**Descrição**: Banco NoSQL document-oriented

**Pros:**
- Schema flexibility
- Horizontal scaling nativo
- JSON nativo

**Cons:**
- Transações limitadas (antes v4.0)
- Joins problemáticos
- Consistência eventual

**Por que foi rejeitada**: Transações ACID são requisito crítico para pagamentos. Risco muito alto de inconsistências.

### Alternativa 2: MySQL
**Descrição**: Banco relacional popular

**Pros:**
- Familiar para equipe
- Bom ecossistema
- Performance reads

**Cons:**
- JSON support inferior
- Menos features avançadas
- MVCC implementation inferior

**Por que foi rejeitada**: PostgreSQL oferece superset de features sem desvantagens significativas.

## Consequences

### Positive
- Data integrity garantida
- Complex queries simples (SQL)
- Ecosystem maduro
- JSONB para flexibilidade
- Excellent performance com índices

### Negative
- Horizontal scaling mais complexo
  - Mitigação: Vertical scaling + read replicas
- Schema migrations necessárias
  - Mitigação: Usar Prisma/TypeORM migrations
- Requer DBA knowledge
  - Mitigação: AWS RDS managed

### Risks
**Risk 1**: Performance degradation com escala
- Likelihood: Medium
- Impact: High
- Mitigation: Indexes, partitioning, read replicas

## Implementation

### Setup Recomendado
```bash
# Development
docker run -d \
  --name postgres \
  -e POSTGRES_PASSWORD=dev \
  -e POSTGRES_DB=ecommerce \
  -p 5432:5432 \
  postgres:15-alpine

# Production
AWS RDS PostgreSQL 15
Instance: db.t3.medium
Multi-AZ: Yes
```

### Connection Example
```typescript
import { Pool } from 'pg';

export const pool = new Pool({
  host: process.env.DB_HOST,
  database: process.env.DB_NAME,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  max: 20,
});
```

## Follow-up Actions

- [ ] Setup PostgreSQL em ambiente dev
- [ ] Configurar backup strategy
- [ ] Documentar schema conventions
- [ ] Setup monitoring (slow queries)

## References

- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [ACID vs BASE](https://www.ibm.com/cloud/blog/acid-vs-base)
- [Template ADR](./000-template.md)

---

**Este é um EXEMPLO** - @architect criará ADRs reais quando decisões arquiteturais forem tomadas no seu projeto.
