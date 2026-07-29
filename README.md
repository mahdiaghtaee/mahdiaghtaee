# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, and **Docker**. My current work focuses on durable workflows, tenant-isolated data access, authenticated semantic retrieval, and AI-provider integration without losing the security boundaries, observability, and testability expected from enterprise software.

I use this profile to document implemented project work, architecture decisions, technical trade-offs, and focused open-source contributions. I prefer small, reviewable changes and accurate engineering documentation over inflated claims or demo-only features.

## Flagship Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)
[![GitHub stars](https://img.shields.io/github/stars/mahdiaghtaee/enterprise-ai-document-assistant?style=social)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/stargazers)

A local-first reference implementation for tenant-isolated document ingestion, durable background processing, persistent semantic retrieval, and source-aware answers in an ASP.NET Core backend.

```text
JWT tenant/user -> RLS-scoped upload -> Atomic enqueue -> Background extract/chunk/embed -> Tenant-scoped retrieval -> Answer with sources
```

The implementation includes:

- fail-closed JWT validation for issuer, audience, signature, lifetime, `sub`, `tenant_id`, and role;
- tenant-scoped `User` and `Admin` roles plus explicit cross-tenant `PlatformAdmin` access;
- immutable document ownership and tenant identity derived from JWT claims rather than client input;
- owner-filtered listing, status, search, answers, and source text for ordinary users;
- tenant-wide access for tenant administrators without cross-tenant visibility;
- forced PostgreSQL Row-Level Security on documents, semantic chunks, and ingestion jobs;
- separate non-superuser PostgreSQL roles for tenant runtime access and privileged worker/platform operations;
- composite tenant/document foreign keys and fail-closed transaction-local tenant context;
- direct negative tests for cross-user reads, cross-tenant reads and writes, and missing tenant context;
- ASP.NET Core APIs and a hosted document-ingestion worker;
- atomic document metadata and initial job creation in PostgreSQL;
- durable `Pending`, `Processing`, `Completed`, and `Failed` lifecycle states;
- transactional job claiming with PostgreSQL `FOR UPDATE SKIP LOCKED`;
- bounded retries, graceful-shutdown requeue, and abandoned-job recovery;
- plain-text extraction, fixed-size chunking, and deterministic local embeddings;
- persistent PostgreSQL/pgvector semantic indexing with cosine retrieval;
- deterministic source-aware Search and Ask endpoints without paid AI credentials;
- Docker Compose, Swagger, an authenticated Web UI, sample documents, and an end-to-end demo;
- .NET, PostgreSQL, Python, and runtime container tests, coverage floors, CodeQL, Dependency Review, Dependabot, and CODEOWNERS.

The deterministic embedding model is intended for reproducible development rather than production retrieval quality. Tenant lifecycle, audit logging, encrypted storage, production identity-provider integration, privileged-worker separation, and provider-backed answer generation remain explicit next milestones.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Tenant isolation](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/TENANT_ISOLATION.md) · [Authentication](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/AUTHENTICATION_AND_AUTHORIZATION.md) · [Architecture](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ARCHITECTURE.md) · [Background ingestion](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/BACKGROUND_INGESTION.md) · [Roadmap](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ROADMAP.md)

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
**Security:** JWT authentication, RBAC, document ownership, tenant isolation, PostgreSQL RLS, negative authorization testing  
**AI systems:** document processing, semantic search, RAG foundations, provider abstraction  
**Infrastructure:** Docker, Docker Compose, Redis, CI, background services, service boundaries  
**Engineering:** API contracts, architecture documentation, integration testing, reliability, observability, and security boundaries  
**Open source:** .NET, ASP.NET Core, technical documentation, focused maintenance contributions

## What I Can Discuss in an Interview

- designing atomic document and job persistence without orphaned database or storage state;
- safely claiming PostgreSQL jobs across multiple application instances with `SKIP LOCKED`;
- designing bounded retry, cancellation, graceful shutdown, and abandoned-work recovery;
- deriving owner and tenant identity from JWT claims without accepting security scope from client payloads;
- distinguishing tenant-scoped `Admin` from explicit cross-tenant `PlatformAdmin` access;
- enforcing tenant isolation twice: application access context plus PostgreSQL forced Row-Level Security;
- setting transaction-local tenant context and making missing context fail closed;
- using separate non-superuser runtime and privileged database roles instead of relying on application filters alone;
- designing negative tests that prove cross-user and cross-tenant retrieval and writes are blocked;
- verifying persistence and authorization through container restart tests rather than documentation claims;
- deciding when a .NET application should call a Python service and when a modular application is simpler;
- designing SQL-heavy workflows, reporting systems, and enterprise integrations;
- responding to maintainer review and improving code without expanding scope unnecessarily.

## Current Engineering Priorities

1. durable audit logging, correlation identifiers, OpenTelemetry traces, and operational metrics;
2. tenant provisioning, membership lifecycle, invitation workflows, and separation of the privileged worker trust boundary;
3. reproducible retrieval-quality evaluation;
4. one provider-backed grounded-answer implementation while preserving the deterministic local mode;
5. safe PDF/DOCX extraction boundaries, malware scanning, and file-signature validation.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
