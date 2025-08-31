---
created: 2025-08-31T14:10:07Z
last_updated: 2025-08-31T14:10:07Z
version: 1.0
author: Claude Code PM System
---

# Project Structure

## Current Directory Organization

```
GaussHub/
├── .claude/                    # Claude Code PM system configuration
│   ├── context/               # Project context documentation
│   ├── scripts/               # PM automation scripts
│   └── rules/                 # Development rules and guidelines
├── .DS_Store                  # macOS system file
├── CLAUDE.md                  # Development guidelines and rules
├── MRD-PRD-v1-aligned-with-AI-Agent.md  # Integrated requirements
├── improved-prd-doc.md        # Enhanced product requirements
├── improved_mrd.md            # Enhanced market requirements
├── mrd.md                     # Market Requirements Document
├── prd.md                     # Product Requirements Document
├── 对齐后的mrd_prd｜_3_d霍尔传感器市场赋能与情报平台（v_1_对齐草案）.md  # Chinese alignment doc
├── 知识库测试list.md           # Knowledge base test list
└── 各类账号与知识库信息.md      # Account and knowledge base info
```

## Documentation Organization

### Requirements Documents
- **Primary Requirements**: `MRD-PRD-v1-aligned-with-AI-Agent.md` (20KB) - Main integrated spec
- **Enhanced Specs**: `improved-prd-doc.md` (23KB) and `improved_mrd.md` (9KB)
- **Original Drafts**: `mrd.md` (7KB) and `prd.md` (8KB)
- **Alignment Document**: Chinese version with final specifications (15KB)

### Configuration Files
- **CLAUDE.md**: Development standards, coding rules, and AI agent guidelines
- **.claude/**: Claude Code PM system with scripts and context management

### Reference Materials
- **Knowledge Base Tests**: Testing scenarios and data lists
- **Account Information**: System access and integration details

## Planned Future Structure (Development Phase)

```
GaussHub/
├── .claude/                   # PM system (existing)
├── docs/                      # Technical documentation
│   ├── api/                   # API documentation
│   ├── architecture/          # System design docs
│   └── user-guides/           # User manuals
├── src/                       # Source code
│   ├── frontend/              # React TypeScript frontend
│   │   ├── components/        # Reusable UI components
│   │   ├── pages/            # Route-based page components
│   │   ├── services/         # API and data services
│   │   ├── hooks/            # Custom React hooks
│   │   ├── utils/            # Utility functions
│   │   └── types/            # TypeScript type definitions
│   ├── backend/              # Node.js backend
│   │   ├── routes/           # API route handlers
│   │   ├── middleware/       # Express middleware
│   │   ├── models/           # Database models
│   │   ├── services/         # Business logic services
│   │   └── utils/            # Backend utilities
│   └── shared/               # Shared code between frontend/backend
├── tests/                    # Test suites
│   ├── unit/                 # Unit tests
│   ├── integration/          # Integration tests
│   └── e2e/                  # End-to-end tests
├── scripts/                  # Build and deployment scripts
├── database/                 # Database migrations and seeds
├── docker/                   # Docker configuration
└── deployment/               # Kubernetes and deployment configs
```

## File Naming Conventions

### Current Pattern
- Kebab-case for main documents: `improved-prd-doc.md`
- Mixed languages: Chinese and English files coexist
- Descriptive names indicating version and purpose

### Planned Conventions (Development)
- **Source Code**: camelCase for variables, PascalCase for components
- **Files**: kebab-case for components, camelCase for utilities
- **Directories**: lowercase with hyphens for multi-word names
- **Tests**: `*.test.ts` or `*.spec.ts` suffixes

## Key Organizational Principles

### Documentation First
- Comprehensive requirements documentation before development
- Version-controlled specification alignment
- Bilingual support (Chinese/English) for international team

### PM System Integration
- Claude Code PM system for task management
- Automated script integration in `.claude/scripts/`
- Context-aware development assistance

### Modular Architecture Preparation
- Clear separation of concerns planned
- Frontend/backend/shared code organization
- Test-driven development structure ready

## Notes
- Project currently in documentation/planning phase
- No source code or dependencies yet
- Strong foundation for structured development approach
- Ready for git initialization and development environment setup