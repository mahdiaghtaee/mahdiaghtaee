# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, **Docker**, and **OpenTelemetry**. My current work focuses on durable workflows, managed tenant authorization, database-enforced isolation, auditable processing, separated service trust boundaries, measurable retrieval, and grounded AI answers.

I prefer reviewable changes, negative security tests, explicit failure modes, machine-readable evaluation, and documentation that matches the implemented system.

## Flagship Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml)
[![Retrieval quality](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml)
[![Grounded answers](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/answer-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/answer-evaluation.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)

A local-first reference implementation for managed multi-tenant document ingestion, independently deployed background processing, persistent semantic retrieval, provider-optional grounded answers, auditability, and reproducible evaluation.

```text
JWT subject/tenant -> Durable tenant + membership policy -> PostgreSQL RLS -> API enqueue
                                                               |
Shared document volume <- Public API ---------------------------+-> Privileged worker
                                                                     |
                                                   Extract/chunk/embed -> pgvector
                                                                     |
Tenant-scoped retrieval -> Evidence/citation gate -> Answer + independent sources
```

### Managed identity and authorization

- fail-closed JWT validation for issuer, audience, signature, lifetime, `sub`, `tenant_id`, and role;
- durable `tenants`, `tenant_memberships`, and `tenant_invitations` storage;
- PlatformAdmin provisioning, deactivation, and reactivation APIs;
- atomic tenant and initial Admin creation;
- active tenant and active membership checks on protected operations;
- immediate access revocation after membership removal or tenant deactivation;
- rejection of stale JWT Admin claims when durable membership is only `User`;
- member listing, role changes, removal, and final-active-Admin protection;
- subject-bound, one-time, expiry-aware, revocable invitations;
- invitation secrets generated from 32 random bytes with SHA-256 digest-only persistence;
- forced PostgreSQL RLS and direct cross-tenant read/write rejection tests.

### Separated trust boundaries

- `document_app` for tenant-scoped public API operations;
- `document_platform` for lifecycle management, cross-tenant reads, and audit insertion;
- `document_privileged` for ingestion, retries, recovery, and vector/document mutations;
- all roles are non-superuser and do not have `BYPASSRLS`;
- the public API does not receive the privileged worker credential;
- an independent Worker service has no published host port;
- API and Worker share only the named document-storage volume required for processing;
- explicit `Api`, `Worker`, and compatibility `Combined` hosting modes.

### Durable processing and retrieval

- atomic document metadata and initial ingestion-job persistence;
- PostgreSQL job claiming with `FOR UPDATE SKIP LOCKED`;
- bounded retries, graceful-shutdown requeue, and abandoned-job recovery;
- plain-text extraction, fixed-size chunking, deterministic local embeddings, and PostgreSQL/pgvector retrieval;
- tenant and owner identity preserved through enqueue, processing, chunks, status, Search, Ask, and sources.

### Grounded answer generation

- `IAnswerGenerator` and `IGroundedAnswerService` abstractions;
- deterministic local extractive generation as the credential-free default;
- optional OpenAI-compatible Chat Completions provider;
- bounded question, source-count, context-character, timeout, and output-token limits;
- retrieved document content treated as untrusted prompt data;
- mandatory request-local `[S#]` citations;
- rejection of uncited and out-of-range provider answers;
- explicit `no_evidence`, `low_confidence`, `conflicting_evidence`, and `provider_declined` outcomes;
- controlled timeout, rate-limit, network, credential, malformed-response, empty-response, and grounding-failure mappings;
- source metadata constructed independently from generated output.

### Evaluation, audit, and observability

- versioned retrieval corpus with Precision@K, Recall@K, MRR, empty-query accuracy, and local latency metrics;
- retrieval baseline: `Precision@3 = 0.277778`, `Recall@3 = 0.75`, `MRR = 0.833333`, empty-query accuracy `1.0`;
- eight-case grounded-answer baseline requiring `1.0` across grounding, insufficient evidence, call behavior, and rejection gates;
- retained machine-readable CI artifacts rather than selected success-only demos;
- validated correlation IDs and W3C trace propagation across ASP.NET Core, FastAPI, and optional provider calls;
- structured logging and OpenTelemetry traces/metrics for HTTP, Search, Ask, provider generation, upload, and worker processing;
- append-only tenant audit storage with forced RLS;
- audit events for document, ingestion, tenant, membership, invitation, provider, and audit operations;
- exclusion of document text, questions, queries, answers, provider bodies, invitation secrets, bearer tokens, and API keys from audit/metric dimensions.

The retrieval and answer datasets are intentionally small and synthetic. They detect controlled regressions but do not establish production factual accuracy. External-provider activation requires separate privacy, residency, retention, training, subprocessor, cost, and contractual review.

Remaining production boundaries include trusted invitation delivery, domain verification, IdP/SCIM synchronization, managed token/key revocation, encrypted storage, centralized secrets, quotas, retention/export/deletion, audit archival, production telemetry backends, and representative multilingual evaluation.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Tenant lifecycle](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/TENANT_LIFECYCLE.md) · [Grounded Ask](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/RAG_ASK_ENDPOINT.md) · [Retrieval evaluation](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/RETRIEVAL_EVALUATION.md) · [Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/HEALTH_AND_OBSERVABILITY.md) · [Architecture](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ARCHITECTURE.md)

## Open-source Contributions

I contribute focused changes to established projects and work through maintainer feedback.

### Merged

- [dotnet/aspnetcore #67481](https://github.com/dotnet/aspnetcore/pull/67481) — clarified `ActionLink` URL-generation documentation for null protocol and host behavior.
- [dotnet/docs #54567](https://github.com/dotnet/docs/pull/54567) — documented `sizeof` behavior for enum types in the C# language reference.
- [dotnet/docs #54559](https://github.com/dotnet/docs/pull/54559) — corrected an ASP.NET workload typo in the .NET microservices documentation.

## Supporting Projects

### [Enterprise AI Toolkit](https://github.com/mahdiaghtaee/enterprise-ai-toolkit)

An early .NET foundation for provider-independent AI contracts, with a deterministic provider, runnable sample, tests, and CI.

### [Fast Fair Wait-Free Locks](https://github.com/mahdiaghtaee/fast-fair-wait-free-locks)

An exploratory research-to-code project about randomized locking, contention, fairness, reproducible testing, and the limits of establishing algorithmic progress guarantees in Python.

### [Persian License Plate Recognition](https://github.com/mahdiaghtaee/persian-license-plate-recognition)

An archived computer-vision study project retained with explicit scope and reproducibility limitations.

## Technical Focus

**Backend:** C#, ASP.NET Core, REST APIs, SQL Server, PostgreSQL  
**Data and workflows:** transactions, durable jobs, lifecycle state, reporting, enterprise integrations  
**Security:** JWT, durable membership authorization, tenant lifecycle, PostgreSQL RLS, invitation security, negative tests  
**Architecture:** API/Worker separation, least-privilege database identities, service trust boundaries  
**Observability:** correlation, structured logging, OpenTelemetry, liveness/readiness  
**AI systems:** document processing, semantic retrieval, RAG grounding, provider abstraction, controlled failures  
**Evaluation:** Precision@K, Recall@K, MRR, citation gates, insufficient-evidence cases, CI baselines  
**Infrastructure:** Docker Compose, Redis, CI, background services, pgvector  
**Open source:** .NET, ASP.NET Core, technical documentation, focused maintenance contributions

## What I Can Discuss in an Interview

- making durable tenant membership authoritative without trusting JWT role claims indefinitely;
- implementing immediate application revocation independently of token expiration;
- preventing removal or downgrade of the final tenant administrator transactionally;
- designing subject-bound invitation secrets with digest-only persistence and replay protection;
- combining application authorization with forced PostgreSQL Row-Level Security;
- separating tenant runtime, platform management, and privileged worker database identities;
- removing the ingestion credential from the public API process;
- sharing document storage between independently deployed enqueue and processing services;
- atomic document/job persistence and PostgreSQL job claiming with `SKIP LOCKED`;
- bounded retries, cancellation, graceful shutdown, and abandoned-work recovery;
- designing append-only tenant audit storage and excluding sensitive content;
- provider-neutral grounded answer generation with evidence and citation gates;
- testing provider protocol and failure behavior without real credentials;
- defining retrieval and answer baselines without overstating a synthetic corpus;
- using independent CI checks for lifecycle, RLS, audit, persistence, recovery, retrieval, grounding, and CodeQL.

## Current Engineering Priorities

1. audit retention, telemetry dashboards, alerts, SLOs, and operational runbooks;
2. safe PDF/DOCX extraction, file-signature validation, malware-scanning boundaries, and extraction limits;
3. a larger reviewed multilingual retrieval/answer corpus and one approved non-sensitive provider comparison;
4. production IdP/SCIM integration, domain verification, managed token/key revocation, and trusted invitation delivery;
5. centralized secret management, encrypted storage, tenant quotas, retention/export/deletion, and legal-hold workflows.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
