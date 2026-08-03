# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, **Docker**, and **OpenTelemetry**. My current work focuses on durable workflows, database-enforced tenant isolation, auditable document processing, observable background services, measurable retrieval, and provider-optional grounded answers without losing the security and testability expected from enterprise software.

I use this profile to document implemented project work, architecture decisions, technical trade-offs, and focused open-source contributions. I prefer reviewable changes, negative security tests, measurable baselines, explicit failure modes, and accurate engineering documentation over inflated claims or demo-only features.

## Flagship Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml)
[![Retrieval quality](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml)
[![Grounded answers](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/answer-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/answer-evaluation.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)
[![GitHub stars](https://img.shields.io/github/stars/mahdiaghtaee/enterprise-ai-document-assistant?style=social)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/stargazers)

A local-first reference implementation for tenant-isolated document ingestion, durable background processing, persistent semantic retrieval, provider-optional grounded answers, auditable operations, and reproducible quality evaluation.

```text
JWT tenant/user -> Correlated RLS-scoped request -> Durable audit + enqueue ->
Background extract/chunk/embed -> Tenant-scoped retrieval -> Grounding gate -> Answer + sources
                                      |                         |
                                      +-> Retrieval baseline    +-> Answer baseline
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
- a versioned tenant-safe retrieval corpus with exact, ambiguous, vocabulary-mismatch, and empty queries;
- Precision@K, Recall@K, mean reciprocal rank, empty-query accuracy, and local latency metrics;
- a machine-readable observed retrieval baseline with reviewed thresholds and non-zero regression exit codes;
- `IAnswerGenerator` and `IGroundedAnswerService` abstractions;
- deterministic local extractive answers as the credential-free default;
- an optional OpenAI-compatible Chat Completions answer provider selected through fail-closed configuration;
- bounded question, source-count, context-character, timeout, and output-token limits;
- source content delimited as untrusted prompt data rather than instructions;
- mandatory request-local `[S#]` citations and controlled rejection of uncited or out-of-range answers;
- explicit `no_evidence`, `low_confidence`, `conflicting_evidence`, and `provider_declined` outcomes;
- controlled timeout, network, rate-limit, credential, malformed-response, empty-response, and grounding-failure mappings;
- retrieved source metadata preserved independently from generated text and provider failures;
- a versioned eight-case grounded-answer evaluation with `1.0` accuracy thresholds for grounding, insufficient evidence, provider-call behavior, and rejection gates;
- retained machine-readable retrieval and answer-evaluation CI artifacts rather than selected success-only demos;
- validated `X-Correlation-ID` handling and W3C trace-context propagation across ASP.NET Core, FastAPI, and optional provider calls;
- log-safe correlation hashing that prevents externally supplied identifiers from becoming raw log entries;
- structured JSON logging and OpenTelemetry traces/metrics for HTTP, Search, Ask, provider generation, upload, and background processing;
- liveness and dependency-aware readiness endpoints;
- an append-only PostgreSQL audit ledger protected by forced tenant RLS;
- atomic database-trigger audit for document and ingestion state transitions;
- correlated application audit for list, upload, status, Search, Ask, provider outcomes, and audit access;
- audit and telemetry controls that exclude document text, search queries, questions, generated answers, provider response bodies, bearer tokens, and API keys;
- Docker Compose, Swagger, an authenticated Web UI, sample documents, and an end-to-end demo;
- .NET, PostgreSQL, Python, retrieval-evaluation, answer-evaluation, audit-boundary, and runtime container tests, coverage floors, CodeQL, Dependency Review, Dependabot, and CODEOWNERS.

The retrieval version 1 baseline records `Precision@3 = 0.277778`, `Recall@3 = 0.75`, `MRR = 0.833333`, and empty-query accuracy `1.0`. The answer version 1 baseline requires `1.0` accuracy across all eight grounding-gate cases. Both datasets are small and synthetic: they detect controlled regressions but do not establish production factual accuracy.

The OpenAI-compatible path is optional and verified with in-memory HTTP doubles rather than a real provider account. Provider activation can transfer authorized questions and document excerpts outside the deployment boundary and therefore requires separate review of retention, residency, training terms, subprocessors, cost, secrets, and contractual controls.

Tenant lifecycle, privileged-worker separation, encrypted storage, centralized secret management, audit retention, production identity-provider integration, telemetry backends, and representative production-quality evaluation remain explicit limitations.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Grounded Ask](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/RAG_ASK_ENDPOINT.md) · [Retrieval evaluation](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/RETRIEVAL_EVALUATION.md) · [Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/HEALTH_AND_OBSERVABILITY.md) · [Tenant isolation](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/TENANT_ISOLATION.md) · [Authentication](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/AUTHENTICATION_AND_AUTHORIZATION.md) · [Architecture](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ARCHITECTURE.md) · [Roadmap](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ROADMAP.md)

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
**AI systems:** document processing, semantic retrieval, RAG grounding, provider abstraction, controlled provider errors  
**Evaluation:** relevance judgments, Precision@K, Recall@K, MRR, citation gates, insufficient-evidence cases, regression baselines  
**Infrastructure:** Docker, Docker Compose, Redis, CI, background services, service boundaries  
**Engineering:** API contracts, architecture documentation, integration testing, reliability, security, and operational diagnostics  
**Open source:** .NET, ASP.NET Core, technical documentation, focused maintenance contributions

## What I Can Discuss in an Interview

- designing atomic document and job persistence without orphaned database or storage state;
- safely claiming PostgreSQL jobs across multiple application instances with `SKIP LOCKED`;
- designing bounded retry, cancellation, graceful shutdown, and abandoned-work recovery;
- deriving owner and tenant identity from JWT claims without accepting security scope from client payloads;
- enforcing tenant isolation through both application context and PostgreSQL forced Row-Level Security;
- using separate non-superuser runtime and privileged database roles;
- designing append-only tenant audit storage with database triggers and RLS;
- separating durable audit records from diagnostic telemetry;
- propagating correlation and W3C trace context between ASP.NET Core, FastAPI, and outbound provider requests;
- preventing sensitive document, query, answer, provider-response, and credential content from entering audit or metric dimensions;
- defining a versioned retrieval corpus and explicit chunk-level relevance judgments;
- calculating and interpreting Precision@K, Recall@K, reciprocal rank, and latency without overstating a small corpus;
- preserving ambiguous and vocabulary-mismatch failures as measurable evidence rather than selecting only successful demos;
- designing a provider-neutral answer-generation abstraction with deterministic and OpenAI-compatible implementations;
- keeping retrieved source metadata independent from model-generated text;
- bounding provider context and treating retrieved document instructions as untrusted prompt data;
- enforcing request-local citations and rejecting unsupported provider answers;
- distinguishing insufficient evidence from retryable provider failure and permanent provider rejection;
- mapping provider timeout, rate limit, credential, malformed-response, and network failures into stable API contracts;
- testing provider protocol and grounding behavior without real API credentials;
- governing strict machine-readable answer-quality thresholds rather than claiming unmeasured factual accuracy;
- verifying persistence, authorization, audit isolation, recovery, retrieval quality, and grounding gates through independent automated checks;
- deciding when a .NET application should call a Python service and when a modular application is simpler;
- designing SQL-heavy workflows, reporting systems, and enterprise integrations;
- responding to automated security review and changing the design rather than suppressing findings.

## Current Engineering Priorities

1. tenant provisioning, membership lifecycle, invitation workflows, and separation of the privileged worker trust boundary;
2. audit retention, telemetry dashboards, alert rules, and operational runbooks;
3. safe PDF/DOCX extraction boundaries, malware scanning, and file-signature validation;
4. a larger reviewed multilingual retrieval/answer corpus and one approved non-sensitive external-provider comparison;
5. centralized secret management, managed key rotation, and provider-governance integration.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
