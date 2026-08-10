# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, **Docker**, and **OpenTelemetry**. My current work focuses on durable workflows, managed tenant authorization, database-enforced isolation, safe document ingestion, separated service trust boundaries, auditable processing, measurable retrieval, and grounded AI answers.

I prefer reviewable changes, negative security tests, explicit failure modes, machine-readable evaluation, and documentation that matches the implemented system.

## Flagship Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)
[![Safe document formats](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/document-formats.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/document-formats.yml)
[![Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/observability.yml)
[![Retrieval quality](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/retrieval-evaluation.yml)
[![Grounded answers](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/answer-evaluation.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/answer-evaluation.yml)
[![CodeQL](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/codeql.yml)

A local-first reference implementation for managed multi-tenant document ingestion, independently deployed background processing, safe TXT/PDF/DOCX extraction, persistent semantic retrieval, provider-optional grounded answers, auditability, and reproducible evaluation.

```text
JWT subject/tenant -> Durable membership + PostgreSQL RLS -> Safe upload gates
                                                           |
Shared document volume <- Public API -----------------------+-> Privileged worker
                                                                 |
                                      TXT/PDF/DOCX extract/chunk/embed -> pgvector
                                                                 |
Tenant-scoped retrieval -> Evidence/citation gate -> Answer + independent sources
```

### Managed identity and authorization

- fail-closed JWT validation for issuer, audience, signature, lifetime, `sub`, `tenant_id`, and role;
- durable tenant, membership, and invitation lifecycle;
- immediate access revocation after membership removal or tenant deactivation;
- rejection of stale JWT Admin claims when durable membership is only `User`;
- final-active-Admin protection;
- subject-bound one-time invitations with SHA-256 digest-only persistence;
- forced PostgreSQL RLS and direct cross-tenant read/write rejection tests.

### Safe document ingestion

- exact extension/MIME agreement for `.txt`, `.pdf`, and `.docx`;
- actual `%PDF-` signature and parser validation before durable enqueue;
- bounded DOCX ZIP/OOXML validation with required Word parts, traversal rejection, expanded-byte limits, and secure XML parsing;
- strict UTF-8 TXT extraction plus bounded PdfPig PDF and WordprocessingML DOCX extraction in the independent Worker;
- configurable PDF page, DOCX archive/XML, and total extracted-character limits;
- explicit `ocr-required` outcome for image-only/scanned PDFs instead of silent empty indexing;
- optional ClamAV `INSTREAM` boundary that fails closed when enabled while remaining `Disabled` in the service-free local default;
- malware threat/unavailable outcomes happen before file persistence and durable document/job creation;
- raw scanner responses, threat-signature names, document bytes, and extracted text are excluded from audit/metric dimensions;
- dedicated Compose verification uploads real PDF/DOCX fixtures, waits for Worker completion, verifies retrieval, and rejects a spoofed PDF.

### Separated trust boundaries

- `document_app` for tenant-scoped public API operations;
- `document_platform` for lifecycle management, cross-tenant reads, and audit insertion;
- `document_privileged` for ingestion, retries, recovery, and vector/document mutations;
- all roles are non-superuser and do not have `BYPASSRLS`;
- the public API does not receive the privileged Worker credential;
- an independent Worker service has no published host port;
- API and Worker share only the named document-storage volume required for processing.

### Durable processing and retrieval

- atomic document metadata and initial ingestion-job persistence;
- PostgreSQL job claiming with `FOR UPDATE SKIP LOCKED`;
- bounded retries, graceful-shutdown requeue, and abandoned-job recovery;
- deterministic local embeddings and PostgreSQL/pgvector retrieval;
- tenant and owner identity preserved through enqueue, processing, chunks, status, Search, Ask, and sources.

### Grounded answer generation

- provider-neutral `IAnswerGenerator` and `IGroundedAnswerService` abstractions;
- deterministic local extractive generation as the credential-free default;
- optional OpenAI-compatible Chat Completions provider;
- bounded context/provider inputs and retrieved content treated as untrusted prompt data;
- mandatory request-local `[S#]` citations;
- explicit insufficient-evidence outcomes and controlled provider failures;
- source metadata constructed independently from generated output.

### Evaluation, audit, and observability

- retrieval baseline: `Precision@3 = 0.277778`, `Recall@3 = 0.75`, `MRR = 0.833333`, empty-query accuracy `1.0`;
- eight-case grounded-answer baseline requiring `1.0` across grounding, insufficient evidence, call behavior, and rejection gates;
- retained machine-readable CI artifacts rather than selected success-only demos;
- validated correlation IDs and W3C trace propagation;
- structured logging and OpenTelemetry traces/metrics for HTTP, Search, Ask, upload, provider generation, and Worker processing;
- append-only tenant audit storage with forced RLS;
- exclusion of document text, questions, queries, answers, scanner responses, invitation secrets, bearer tokens, and API keys from audit/metric dimensions.

The safe document boundary does not claim complete parser or malware safety. OCR execution, complex PDF layout/table reconstruction, password-protected document workflows, and operation of a production malware engine remain separate work. The retrieval and answer datasets are intentionally small and synthetic and do not establish production factual accuracy.

Remaining production boundaries include trusted invitation delivery, IdP/SCIM synchronization, managed token/key revocation, encrypted storage, centralized secrets, quotas, retention/export/deletion, audit archival, telemetry backends, production malware operations, representative multilingual evaluation, and reviewed OCR/layout processing.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Safe document extraction](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/TEXT_EXTRACTION_PIPELINE.md) · [Tenant lifecycle](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/TENANT_LIFECYCLE.md) · [Grounded Ask](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/RAG_ASK_ENDPOINT.md) · [Retrieval evaluation](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/RETRIEVAL_EVALUATION.md) · [Audit and observability](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/HEALTH_AND_OBSERVABILITY.md)

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
**Security:** JWT, durable membership authorization, tenant lifecycle, PostgreSQL RLS, secure upload boundaries, negative tests  
**Document processing:** TXT/PDF/DOCX inspection, bounded extraction, OOXML safety, optional malware-scanning boundary  
**Architecture:** API/Worker separation, least-privilege database identities, service trust boundaries  
**Observability:** correlation, structured logging, OpenTelemetry, liveness/readiness  
**AI systems:** semantic retrieval, RAG grounding, provider abstraction, controlled failures  
**Evaluation:** Precision@K, Recall@K, MRR, citation gates, insufficient-evidence cases, CI baselines  
**Infrastructure:** Docker Compose, Redis, CI, background services, pgvector  
**Open source:** .NET, ASP.NET Core, technical documentation, focused maintenance contributions

## What I Can Discuss in an Interview

- making durable tenant membership authoritative without trusting JWT role claims indefinitely;
- combining application authorization with forced PostgreSQL Row-Level Security;
- separating public API, platform management, and privileged Worker database identities;
- atomic document/job persistence and PostgreSQL job claiming with `SKIP LOCKED`;
- treating extension and MIME metadata as hints rather than a file-security boundary;
- validating PDF signatures and parsing before durable enqueue;
- defending DOCX processing against malformed OOXML, traversal paths, archive expansion, DTDs, external XML resolution, and oversized extracted text;
- designing cancellation and resource limits around document parsers;
- returning `ocr-required` instead of silently indexing image-only PDFs;
- integrating ClamAV with fail-closed semantics without exposing raw scanner responses or signature names;
- testing a malware-scanning protocol with an in-process TCP double rather than requiring a scanner in CI;
- proving PDF/DOCX ingestion end-to-end through an independent Worker and retrieval;
- designing append-only tenant audit storage and excluding sensitive content;
- provider-neutral grounded answer generation with evidence and citation gates;
- defining retrieval and answer baselines without overstating a synthetic corpus;
- using independent CI checks for lifecycle, RLS, audit, formats, persistence, retrieval, grounding, Dependency Review, and CodeQL.

## Current Engineering Priorities

1. audit retention, telemetry dashboards, alerts, SLOs, and operational runbooks;
2. a larger reviewed multilingual/adversarial retrieval and answer corpus plus one approved non-sensitive provider comparison;
3. production IdP/SCIM integration, domain verification, managed token/key revocation, and trusted invitation delivery;
4. centralized secret management, encrypted storage, tenant quotas, retention/export/deletion, and legal-hold workflows;
5. sandboxed OCR, advanced PDF layout/table extraction, and production malware-scanner operations where product requirements justify them.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
