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

## Featured Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)
[![Dependency Review](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/dependency-review.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/dependency-review.yml)

A local-first enterprise document platform built around **ASP.NET Core, FastAPI, PostgreSQL, pgvector, Redis, Docker Compose, semantic retrieval, and grounded AI answers**.

Selected engineering capabilities:

- durable document ingestion with transactional job creation, bounded retries, recovery, and PostgreSQL `FOR UPDATE SKIP LOCKED` claiming;
- JWT authentication with durable tenant membership and immediate authorization revocation;
- forced PostgreSQL Row-Level Security with direct cross-tenant negative tests;
- separated public API, platform-management, and privileged Worker database identities;
- safe TXT/PDF/DOCX ingestion with bounded parsing, OOXML validation, spoofed-file rejection, and explicit OCR-required outcomes;
- persistent pgvector semantic retrieval with reproducible Precision@K, Recall@K, and MRR evaluation;
- provider-neutral grounded-answer generation with mandatory citations and insufficient-evidence handling;
- append-only tenant audit storage, OpenTelemetry traces/metrics, correlation propagation, and operational observability;
- independent CI coverage for application tests, PostgreSQL integration, document formats, retrieval, grounding, Dependency Review, and CodeQL.

**Repository:** [enterprise-ai-document-assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

## Open-Source Contributions

Focused contributions merged into established .NET projects:

- [dotnet/aspnetcore #67481](https://github.com/dotnet/aspnetcore/pull/67481) — clarified `ActionLink` URL-generation documentation behavior.
- [dotnet/docs #54567](https://github.com/dotnet/docs/pull/54567) — documented `sizeof` behavior for enum types in the C# language reference.
- [dotnet/docs #54559](https://github.com/dotnet/docs/pull/54559) — corrected ASP.NET workload documentation in the .NET microservices guidance.

## Selected Projects

### [Enterprise AI Toolkit](https://github.com/mahdiaghtaee/enterprise-ai-toolkit)
A .NET foundation for provider-independent AI contracts with a deterministic provider, runnable console sample, tests, and CI.

### [Fast Fair Wait-Free Locks](https://github.com/mahdiaghtaee/fast-fair-wait-free-locks)
An exploratory concurrency project focused on randomized locking, contention, fairness, reproducible testing, and careful treatment of algorithmic guarantees.

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

## Current Technical Direction

I am currently deepening work around:

- production-grade multi-tenant identity and authorization;
- enterprise observability, audit integrity, retention, SLOs, and operational runbooks;
- multilingual and adversarial retrieval/answer evaluation;
- secure document-processing boundaries including OCR and complex layouts;
- scalable .NET backend architecture and enterprise data workflows.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
