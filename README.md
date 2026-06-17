# BookVerse Infrastructure

Demo infrastructure repository for the BookVerse platform, showcasing JFrog
AppTrust capabilities with enterprise library and DevOps tooling patterns.

## 🎯 Demo Purpose & Patterns

This repository demonstrates the Enterprise Library & DevOps Tooling Pattern,
showcasing how shared infrastructure libraries, DevOps utilities, and
enterprise-wide tooling can be managed in AppTrust.

### 🛠️ **Enterprise Library & DevOps Tooling Pattern**
- **What it demonstrates**: Shared libraries, automation scripts, and DevOps 
  utilities managed as versioned artifacts
- **AppTrust benefit**: Enterprise tooling promoted together ensuring consistent
  automation across all environments (DEV → QA → STAGING → PROD)
- **Real-world applicability**: Platform engineering teams, enterprise
  automation, and standardized DevOps practices

This repository is **tooling-focused** - it demonstrates how enterprise
infrastructure and automation can be reliably versioned and promoted.

## 🏗️ Infrastructure Repository Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                BookVerse Infrastructure                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│            ┌─────────────────────────────────┐              │
│            │    Infrastructure Repository    │              │
│            │                                 │              │
│            │  Enterprise Libraries &         │              │
│            │  DevOps Tooling                 │              │
│            │ ┌─────────────────────────────┐ │              │
│            │ │   BookVerse Core Library    │ │              │
│            │ │   (Shared Components)       │ │              │
│            │ └─────────────────────────────┘ │              │
│            │ ┌─────────────────────────────┐ │              │
│            │ │   BookVerse DevOps Tools    │ │              │
│            │ │   (Automation Scripts)      │ │              │
│            │ └─────────────────────────────┘ │              │
│            │ ┌─────────────────────────────┐ │              │
│            │ │   Evidence & Templates      │ │              │
│            │ │   (Policy Templates)        │ │              │
│            │ └─────────────────────────────┘ │              │
│            └─────────────────────────────────┘              │
│                            │                                │
│       ┌────────────────────┼────────────────────┐           │
│       │                    │                    │           │
│       ▼                    ▼                    ▼           │
│ [All Services]       [All Workflows]      [All Teams]      │
│                                                             │
└─────────────────────────────────────────────────────────────┘

AppTrust Promotion Pipeline:
DEV → QA → STAGING → PROD
 │     │       │        │
 └─────┴───────┴────────┘
   Shared Libraries & Tools
   Used Across All Components
```

## 🔧 JFrog AppTrust Integration

This repository creates multiple artifacts per application version:

1. **Python Packages** - BookVerse Core library for all services
2. **DevOps Scripts** - Automation utilities and helper tools
3. **Templates** - Evidence templates and policy configurations
4. **Documentation** - Enterprise architecture and integration guides
5. **SBOMs** - Software Bill of Materials for shared dependencies
6. **Test Reports** - Library and integration testing results
7. **Build Evidence** - Comprehensive infrastructure build attestations

Each artifact moves together through the promotion pipeline:
DEV → QA → STAGING → PROD.

For the non-JFrog evidence plan and gates, see: `docs/EVIDENCE_PLAN.md`.

## 🔄 Workflows

- [`ci.yml`](.github/workflows/ci.yml) — CI: library tests, package builds,
  template validation, publish artifacts/build-info, AppTrust version and
  evidence
- [`promote.yml`](.github/workflows/promote.yml) — Promote the infra app version 
  through stages with evidence
- [`promotion-rollback.yml`](.github/workflows/promotion-rollback.yml) — Roll
  back a promoted infra application version (demo utility)
