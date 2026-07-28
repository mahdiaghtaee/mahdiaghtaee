# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, and **Docker**. My current work focuses on reliable document processing, durable background workflows, authenticated semantic retrieval, and AI-provider integration without losing the security boundaries, observability, and testability expected from enterprise software.

I use this profile to document implemented project work, architecture decisions, technical trade-offs, and focused open-source contributions. I prefer small, reviewable changes and accurate engineering documentation over inflated claims or demo-only features.

## Flagship Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)
[![GitHub stars](https://img.shields.io/github/stars/mahdiaghtaee/enterprise-ai-document-assistant?style=social)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/stargazers)

A local-first reference implementation for authenticated document ingestion, durable background processing, persistent semantic retrieval, and source-aware answers in an ASP.NET Core backend.

```text
JWT user -> Store -> Atomically enqueue with owner -> Background extract/chunk/embed -> Persist vectors -> Authorized search -> Answer with sources
```

The implementation includes:

- fail-closed JWT bearer authentication with issuer, audience, signature, lifetime, subject, and role validation;
- `User` and `Admin` role-based authorization;
- document ownership derived from the authenticated subject rather than client input;
- owner-filtered listing, processing status, semantic search, answers, and source text;
- negative tests for anonymous requests and cross-user retrieval;
- ASP.NET Core APIs and a hosted document-ingestion worker;
- atomic document metadata and initial job creation in PostgreSQL;
- durable `Pending`, `Processing`, `Completed`, and `Failed` lifecycle states;
- transactional job claiming with PostgreSQL `FOR UPDATE SKIP LOCKED`;
- bounded retries, graceful-shutdown requeue, and abandoned-job recovery;
- plain-text extraction, fixed-size chunking, and deterministic local embeddings;
- persistent PostgreSQL/pgvector semantic indexing with cosine retrieval;
- configuration-driven `InMemory` and `Postgres` semantic-index providers;
- deterministic source-aware search and answer endpoints without paid AI credentials;
- Python FastAPI as an explicit boundary for future Python-specific integrations;
- Docker Compose, Swagger, an authenticated Web UI, sample documents, and an end-to-end demo;
- .NET and PostgreSQL integration tests, coverage floors, runtime container verification, CodeQL, Dependency Review, Dependabot, and CODEOWNERS.

The deterministic embedding model is intended for reproducible development rather than production retrieval quality. Tenant/workspace isolation, audit logging, encrypted storage, production identity-provider integration, and provider-backed answer generation remain explicit next milestones.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Authentication](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/AUTHENTICATION_AND_AUTHORIZATION.md) · [Engineering case study](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/CASE_STUDY.md) · [Architecture](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ARCHITECTURE.md) · [Background ingestion](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/BACKGROUND_INGESTION.md) · [Roadmap](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ROADMAP.md)

## Open-source Contributions

I contribute focused changes to established projects and work through maintainer feedback rather than treating pull requests as one-time submissions.

### Merged

- [dotnet/aspnetcore #67481](https://github.com/dotnet/aspnetcore/pull/67481) — clarified `ActionLink` URL-generation documentation for null protocol and host behavior.
- [dotnet/docs #54567](https://github.com/dotnet/docs/pull/54567) — documented `sizeof` behavior for enum types in the C# language reference.
- [dotnet/docs #54559](https://github.com/dotnet/docs/pull/54559) — corrected an ASP.NET workload typo in the .NET microservices documentation.

## Supporting Projects

### [Enterprise AI Toolkit](https://github.com/mahdiaghtaee/enterprise-ai-toolkit)

An early .NET foundation for provider-independent AI contracts, with a deterministic provider, runnable sample, tests, and CI. Reusable abstractions should be extracted only after they are validated by a working application or focused example.

### [Fast Fair Wait-Free Locks](https://github.com/mahdiaghtaee/fast-fair-wait-free-locks)

An exploratory research-to-code project about randomized locking, contention, fairness, reproducible testing, and the limits of establishing algorithmic progress guarantees in Python.

### [Persian License Plate Recognition](https://github.com/mahdiaghtaee/persian-license-plate-recognition)

An archived computer-vision study project for Persian license-plate and character recognition, retained with explicit scope and reproducibility limitations.

## Technical Focus

**Backend:** C#, ASP.NET Core, REST APIs, SQL Server, PostgreSQL  
**Data and workflows:** transactions, durable jobs, lifecycle state, reporting, enterprise integrations  
**Security:** JWT authentication, RBAC, document ownership, access-policy testing  
**AI systems:** document processing, semantic search, RAG foundations, provider abstraction  
**Infrastructure:** Docker, Docker Compose, Redis, CI, background services, service boundaries  
**Engineering:** API contracts, architecture documentation, integration testing, reliability and security boundaries  
**Open source:** .NET, ASP.NET Core, technical documentation, focused maintenance contributions

## What I Can Discuss in an Interview

- designing atomic document and job persistence without orphaned database or storage state;
- safely claiming PostgreSQL jobs across multiple application instances with `SKIP LOCKED`;
- designing bounded retry, cancellation, graceful shutdown, and abandoned-work recovery;
- deriving document ownership from JWT identity and applying the same policy to listing, status, retrieval, and source text;
- designing negative tests that prove one user cannot retrieve another user's document chunks;
- deciding when a .NET application should call a Python service and when a modular application is simpler;
- designing a configurable semantic-index abstraction with in-memory and pgvector implementations;
- verifying persistence and authorization through container restart tests rather than documentation claims;
- building test paths that do not depend on paid or external AI providers;
- designing SQL-heavy workflows, reporting systems, and enterprise integrations;
- responding to maintainer review and improving code without expanding scope unnecessarily.

## Current Engineering Priorities

1. tenant or workspace isolation with database-enforced negative security tests;
2. audit logging, correlation identifiers, OpenTelemetry, and operational metrics;
3. reproducible retrieval-quality evaluation;
4. one provider-backed grounded-answer implementation while preserving the deterministic local mode;
5. safe PDF/DOCX extraction boundaries and file-signature validation.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
