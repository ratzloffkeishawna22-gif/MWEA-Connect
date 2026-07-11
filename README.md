# MWEA Connect Platform

MWEA Connect is a secure, role-based advocacy platform for families, advocates, volunteers, school districts, partners, and administrators.  
It is built as a **Turbo monorepo** using **Next.js 15 App Router** for web, **Firebase Functions + Express** for API, **Firestore** for data, and shared **Zod contracts** for validation integrity.

This repository is the single source of truth for implementation standards, architecture boundaries, security policy, and delivery workflow.

---

## Table of Contents

- [1. Platform Overview](#1-platform-overview)
- [2. Product Scope](#2-product-scope)
- [3. Monorepo Architecture](#3-monorepo-architecture)
- [4. Routing & Application Surfaces](#4-routing--application-surfaces)
- [5. RBAC Security Model](#5-rbac-security-model)
- [6. Backend API Architecture](#6-backend-api-architecture)
- [7. Firestore Data Model](#7-firestore-data-model)
- [8. Validation & Contract Strategy](#8-validation--contract-strategy)
- [9. Authentication & Session Model](#9-authentication--session-model)
- [10. UI/UX Implementation Standards](#10-uiux-implementation-standards)
- [11. AI Educational Advocate Governance](#11-ai-educational-advocate-governance)
- [12. Payments & Financial Safety](#12-payments--financial-safety)
- [13. Local Development Setup](#13-local-development-setup)
- [14. Environment Variables](#14-environment-variables)
- [15. Scripts & Commands](#15-scripts--commands)
- [16. Testing Strategy](#16-testing-strategy)
- [17. CI/CD Requirements](#17-cicd-requirements)
- [18. Deployment Runbook](#18-deployment-runbook)
- [19. Observability, Audit, and Incident Response](#19-observability-audit-and-incident-response)
- [20. Definition of Done](#20-definition-of-done)
- [21. Contribution Guidelines](#21-contribution-guidelines)
- [22. Known Exclusions](#22-known-exclusions)
- [23. License](#23-license)

---

## 1. Platform Overview

MWEA Connect provides:

- A public website for education, services, events, and outreach
- Multi-role portals for operational workflows
- Secure case and document collaboration
- Learning center and community capabilities
- Donations, payments, and e-commerce
- AI-assisted advocacy tools with governance controls

### Core Technical Principles

- **Deny-by-default access**
- **RBAC at route + API + data boundaries**
- **Shared schema validation using Zod**
- **Strict separation of presentational UI vs feature logic**
- **Immutable audit trail for state-changing events**

---

## 2. Product Scope

### Included Domains

- Public Site
- About / Services / Who We Help
- Resource Center
- Learning Center (LMS)
- Community
- Events
- Donate
- Shop
- Book Appointment
- Contact
- Payments
- Legal
- Client / Advocate / Volunteer / District / Partner / Admin portals
- AI Educational Advocate tools

### Explicitly Excluded

- Grants
- Scholarships

All routes, API modules, schemas, and collections for Grants/Scholarships are intentionally omitted.

---

## 3. Monorepo Architecture

```text
mwea-connect/
├── apps/
│   ├── web/              # Next.js 15 (App Router)
│   └── api/              # Firebase Functions + Express
├── packages/
│   ├── ui/               # Shared UI components and design tokens
│   ├── validation/       # Shared Zod schemas
│   ├── types/            # Shared TypeScript types
│   └── sdk/              # Typed API clients
├── firebase/             # Rules, indexes, emulator config
├── docs/                 # System design and policy docs
├── scripts/              # Seed, migration, and utility scripts
├── turbo.json
├── pnpm-workspace.yaml
└── package.json
