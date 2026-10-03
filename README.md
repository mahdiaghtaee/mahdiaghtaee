# Mahdi Aghtaee

**Senior .NET / Backend / Enterprise / AI Engineer**

I design and build secure, reliable backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, **Docker**, and **OpenTelemetry**, with a focus on enterprise workflows, multi-tenant architecture, data integrity, observability, and AI-enabled applications.

My engineering approach emphasizes explicit trust boundaries, durable processing, database-enforced security, measurable quality, reviewable changes, and production-oriented failure handling.

## Core Engineering Focus

- **Backend:** C#, .NET, ASP.NET Core, REST APIs, background services
- **Enterprise systems:** durable workflows, transactional boundaries, lifecycle/state management, integrations
- **Databases:** SQL Server, PostgreSQL, pgvector, Row-Level Security, query and schema design
- **Architecture:** API/Worker separation, least privilege, multi-tenant systems, service trust boundaries
- **Security:** JWT, durable authorization, tenant isolation, secure document ingestion, negative security testing
- **Observability:** OpenTelemetry, structured logging, correlation, metrics, health checks, SLO-oriented monitoring
- **AI engineering:** RAG, semantic retrieval, grounded answers, provider abstraction, evaluation and citation gates
- **Infrastructure:** Docker Compose, Redis, CI/CD, GitHub Actions, CodeQL, dependency automation

## Portfolio Snapshot

| Project | Role in portfolio | Status |
|---|---|---|
| [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) | Flagship enterprise backend + AI reference system | Maintenance — v0.5.1 |
| [Enterprise AI Toolkit](https://github.com/mahdiaghtaee/enterprise-ai-toolkit) | Reusable provider-independent .NET contracts | Stable foundation — v0.2.0 |
| [Fast Fair Wait-Free Locks](https://github.com/mahdiaghtaee/fast-fair-wait-free-locks) | Concurrency research artifact | Archived — v0.1.0 |
| [Persian License Plate Recognition](https://github.com/mahdiaghtaee/persian-license-plate-recognition) | Computer-vision study with documented provenance | Archived |

The portfolio is intentionally centered on a small number of reviewable projects rather than repository count. Forks used for upstream contributions are secondary to the projects above.

## Featured Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)
[![Dependency Review](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/dependency-review.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/dependency-review.yml)
[![Multilingual quality](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/multilingual-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/multilingual-evaluation.yml)

A completed v0.5.x reference milestone for a local-first enterprise document platform built around **ASP.NET Core, FastAPI, PostgreSQL, pgvector, Redis, Docker Compose, semantic retrieval, and grounded AI answers**. The repository is now in maintenance mode.

Selected engineering capabilities:

- durable document ingestion with transactional job creation, bounded retries, recovery, and PostgreSQL `FOR UPDATE SKIP LOCKED` claiming;
- JWT authentication with durable tenant membership and immediate authorization revocation;
- forced PostgreSQL Row-Level Security with direct cross-tenant negative tests;
- separated public API, platform-management, and privileged Worker database identities;
- safe TXT/PDF/DOCX ingestion with bounded parsing, OOXML validation, spoofed-file rejection, and explicit OCR-required outcomes;
- persistent pgvector semantic retrieval with reproducible Precision@K, Recall@K, and MRR evaluation;
- reviewed English, Persian, and mixed-language retrieval/answer evaluation with per-language/category gates and deterministic bootstrap intervals;
- provider-neutral grounded-answer generation with mandatory citations and insufficient-evidence handling;
- append-only tenant audit storage, OpenTelemetry traces/metrics, correlation propagation, and operational observability;
- independent CI coverage for application tests, PostgreSQL integration, document formats, retrieval, multilingual quality, grounding, Dependency Review, and CodeQL.

**Repository:** [enterprise-ai-document-assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

## Open-Source Contributions

Focused contributions merged into established .NET projects:

- [dotnet/aspnetcore #67481](https://github.com/dotnet/aspnetcore/pull/67481) — clarified `ActionLink` URL-generation documentation behavior.
- [dotnet/docs #54567](https://github.com/dotnet/docs/pull/54567) — documented `sizeof` behavior for enum types in the C# language reference.
- [dotnet/docs #54559](https://github.com/dotnet/docs/pull/54559) — corrected ASP.NET workload documentation in the .NET microservices guidance.

## Selected Projects

### [Enterprise AI Toolkit](https://github.com/mahdiaghtaee/enterprise-ai-toolkit)
A stable v0.2.0 .NET foundation for provider-independent chat and embedding contracts with deterministic local providers, explicit vector dimensions/input mapping, a runnable console sample, tests, and CI. Active feature development is paused.

### [Fast Fair Wait-Free Locks](https://github.com/mahdiaghtaee/fast-fair-wait-free-locks)
An archived research artifact preserving scope, attribution, reproducibility requirements, and explicit limitations without claiming a completed benchmark or production synchronization primitive.

### [Persian License Plate Recognition](https://github.com/mahdiaghtaee/persian-license-plate-recognition)
An archived computer-vision study retained with explicit attribution, reproducibility boundaries, and documented limitations.

## Engineering Principles

- Prefer durable state over process-memory assumptions.
- Enforce critical authorization boundaries at more than one layer.
- Treat external inputs and retrieved AI context as untrusted data.
- Make failure modes explicit and observable.
- Use negative tests to validate security boundaries.
- Measure retrieval and answer quality instead of relying on selected demos.
- Keep documentation aligned with implemented behavior.

## Current Portfolio Status

The current public project cycle is closed cleanly:

- Enterprise AI Document Assistant is maintained as the completed v0.5.1 reference milestone;
- Enterprise AI Toolkit is maintained as the stable v0.2.0 chat/embedding foundation;
- Fast Fair Wait-Free Locks is retained as an archived research artifact;
- broader runtime migrations and speculative framework expansion are deferred rather than left as active promises.

New project work is intentionally kept separate so these repositories remain reviewable at their documented boundaries.

## Contact & Collaboration

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
- For repository-specific technical collaboration, use the relevant project's Issues or Pull Requests so design decisions and evidence remain reviewable.

No additional public contact channel is listed here unless it can be verified and intentionally maintained.
