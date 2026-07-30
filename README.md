# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, **Docker**, and **OpenTelemetry**. My current work focuses on durable workflows, database-enforced tenant isolation, auditable document processing, observable background services, and measurable AI retrieval without losing the security and testability expected from enterprise software.

I use this profile to document implemented project work, architecture decisions, technical trade-offs, and focused open-source contributions. I prefer reviewable changes, negative security tests, measurable baselines, and accurate engineering documentation over inflated claims or demo-only features.

## Flagship Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml)
[![Retrieval quality](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)
[![GitHub stars](https://img.shields.io/github/stars/mahdiaghtaee/enterprise-ai-document-assistant?style=social)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/stargazers)

A local-first reference implementation for tenant-isolated document ingestion, durable background processing, persistent semantic retrieval, source-aware answers, auditable operations, and reproducible retrieval-quality evaluation.

```text
JWT tenant/user -> Correlated RLS-scoped request -> Durable audit + enqueue ->
Background extract/chunk/embed -> Tenant-scoped retrieval -> Answer with sources
                                      |
                                      +-> Versioned corpus + regression baseline
```

The implementation includes:

- fail-closed JWT validation for issuer, audience, signature, lifetime, `sub`, `tenant_id`, and role;
- tenant-scoped `User` and `Admin` roles plus explicit cross-tenant `PlatformAdmin` access;
- immutable document ownership and tenant identity derived from JWT claims rather than client input;
- forced PostgreSQL Row-Level Security on documents, semantic chunks, ingestion jobs, and audit events;
- separate non-superuser PostgreSQL roles for tenant runtime access and privileged worker/platform operations;
- composite tenant/document foreign keys and fail-closed transaction-local tenant context;
- direct negative tests for cross-user access, cross-tenant reads and writes, and missing tenant context;
- atomic document metadata and initial ingestion-job persistence;
- transactional job claiming with PostgreSQL `FOR UPDATE SKIP LOCKED`;
- durable lifecycle states, bounded retries, graceful-shutdown requeue, and abandoned-job recovery;
- plain-text extraction, fixed-size chunking, deterministic local embeddings, and PostgreSQL/pgvector retrieval;
- deterministic source-aware Search and Ask endpoints without paid AI credentials;
- a versioned tenant-safe corpus with exact, ambiguous, vocabulary-mismatch, and empty queries;
- explicit document/chunk relevance judgments and a repeatable provider-free .NET evaluation command;
- Precision@K, Recall@K, mean reciprocal rank, empty-query accuracy, mean latency, and p95 latency metrics;
- a machine-readable observed baseline with reviewed regression thresholds and non-zero failure exit codes;
- retained CI report artifacts that expose successful queries and known misses rather than hiding weak cases;
- validated `X-Correlation-ID` handling and W3C trace-context propagation across ASP.NET Core and FastAPI;
- log-safe correlation hashing that prevents externally supplied identifiers from becoming raw log entries;
- structured JSON logging with trace, span, tenant, document, and ingestion-job scopes;
- OpenTelemetry traces and metrics for HTTP, HttpClient, runtime, Search, Ask, upload, and background processing;
- optional OTLP/HTTP export while retaining collector-free local execution;
- liveness and dependency-aware readiness endpoints;
- an append-only PostgreSQL audit ledger protected by forced tenant RLS;
- atomic database-trigger audit for document and ingestion state transitions;
- correlated application audit for list, upload, status, Search, Ask, and audit access;
- tenant-admin audit visibility and explicit PlatformAdmin cross-tenant visibility;
- audit and telemetry controls that exclude document text, search queries, questions, bearer tokens, and file content;
- Docker Compose, Swagger, an authenticated Web UI, sample documents, and an end-to-end demo;
- .NET, PostgreSQL, Python, retrieval-evaluation, audit-boundary, and runtime container tests, coverage floors, CodeQL, Dependency Review, Dependabot, and CODEOWNERS.

The version 1 retrieval baseline records `Precision@3 = 0.277778`, `Recall@3 = 0.75`, `MRR = 0.833333`, and empty-query accuracy `1.0`. The small synthetic corpus is useful for deterministic regression detection, not production-accuracy claims. It deliberately records that the ambiguous query retrieves one of two relevant chunks and the vocabulary-mismatch query currently misses at `K = 3`.

The deterministic embedding model remains intended for reproducible development rather than production retrieval quality. Tenant lifecycle, privileged-worker separation, encrypted storage, audit retention, production identity-provider integration, telemetry backends, and provider-backed answer generation remain explicit limitations.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Retrieval evaluation](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/RETRIEVAL_EVALUATION.md) · [Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/HEALTH_AND_OBSERVABILITY.md) · [Tenant isolation](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/TENANT_ISOLATION.md) · [Authentication](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/AUTHENTICATION_AND_AUTHORIZATION.md) · [Architecture](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ARCHITECTURE.md) · [Roadmap](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ROADMAP.md)

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
**Security:** JWT, RBAC, tenant isolation, PostgreSQL RLS, append-only audit, negative authorization testing  
**Observability:** correlation strategy, structured logging, OpenTelemetry traces and metrics, liveness/readiness  
**AI systems:** document processing, semantic retrieval, RAG foundations, provider abstraction, measurable evaluation  
**Evaluation:** relevance judgments, Precision@K, Recall@K, MRR, regression baselines, machine-readable CI artifacts  
**Infrastructure:** Docker, Docker Compose, Redis, CI, background services, service boundaries  
**Engineering:** API contracts, architecture documentation, integration testing, reliability, security, and operational diagnostics  
**Open source:** .NET, ASP.NET Core, technical documentation, focused maintenance contributions

## What I Can Discuss in an Interview

- designing atomic document and job persistence without orphaned database or storage state;
- safely claiming PostgreSQL jobs across multiple application instances with `SKIP LOCKED`;
- designing bounded retry, cancellation, graceful shutdown, and abandoned-work recovery;
- deriving owner and tenant identity from JWT claims without accepting security scope from client payloads;
- distinguishing tenant-scoped `Admin` from explicit cross-tenant `PlatformAdmin` access;
- enforcing tenant isolation through both application context and PostgreSQL forced Row-Level Security;
- using separate non-superuser runtime and privileged database roles;
- designing append-only tenant audit storage with database triggers and RLS;
- committing base audit records atomically with document and ingestion state changes;
- separating durable audit records from diagnostic telemetry;
- propagating correlation and W3C trace context between ASP.NET Core and FastAPI;
- preventing user-controlled identifiers and sensitive document/query content from entering logs or telemetry;
- choosing low-cardinality metrics and instrumenting background workflows with meaningful spans;
- designing liveness and dependency-aware readiness checks;
- defining a versioned retrieval corpus and explicit chunk-level relevance judgments;
- calculating and interpreting Precision@K, Recall@K, reciprocal rank, and latency without overstating a small corpus;
- preserving known ambiguous and vocabulary-mismatch failures as measurable evidence rather than selecting only successful demos;
- designing threshold governance so an intended ranking change requires an explicit corpus or baseline review;
- using machine-readable CI artifacts to compare retrieval changes before integrating external providers;
- using CI to expose hidden privilege inheritance and prove append-only database behavior;
- verifying persistence, authorization, audit isolation, recovery, and retrieval quality through independent automated checks;
- deciding when a .NET application should call a Python service and when a modular application is simpler;
- designing SQL-heavy workflows, reporting systems, and enterprise integrations;
- responding to automated security review and changing the design rather than suppressing findings.

## Current Engineering Priorities

1. one optional provider-backed grounded-answer implementation while preserving deterministic local mode and source metadata;
2. answer-quality evaluation for insufficient, conflicting, and unsupported evidence;
3. tenant provisioning, membership lifecycle, invitation workflows, and separation of the privileged worker trust boundary;
4. audit retention, telemetry dashboards, alert rules, and operational runbooks;
5. safe PDF/DOCX extraction boundaries, malware scanning, and file-signature validation.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
