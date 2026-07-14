# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, and **Docker**. My current work focuses on document processing, semantic retrieval, and AI-provider integration without losing the reliability, security boundaries, and testability expected from enterprise software.

I use this profile to document real project work, architecture decisions, technical trade-offs, and open-source contributions. I prefer small, reviewable changes and accurate engineering documentation over inflated claims or demo-only features.

## Current Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![GitHub stars](https://img.shields.io/github/stars/mahdiaghtaee/enterprise-ai-document-assistant?style=social)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/stargazers)
[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)

A local-first reference project for integrating document retrieval into an ASP.NET Core backend.

```text
Upload -> Persist metadata -> Extract -> Chunk -> Embed -> Search -> Answer with sources
```

The current implementation includes:

- ASP.NET Core for public APIs, PostgreSQL metadata, local extraction, chunking, deterministic embeddings, semantic retrieval, and source-aware answers;
- Python FastAPI as a separate health and indexing boundary for future Python-specific document or model integrations;
- PostgreSQL for document metadata;
- Redis as infrastructure for future caching or background work;
- Docker Compose, integration tests, health endpoints, Swagger, sample documents, and an end-to-end demo.

The current semantic index is in memory, processing is synchronous, and access control is not implemented. The next engineering steps are pgvector persistence, background indexing, authentication, audit logging, observability, and justified model-provider integrations.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Engineering case study](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/CASE_STUDY.md) · [Architecture](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ARCHITECTURE.md) · [Roadmap](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ROADMAP.md)

## Open-source Contributions

I contribute focused changes to established projects and work through maintainer feedback rather than treating pull requests as one-time submissions.

### Merged

- [dotnet/aspnetcore #67481](https://github.com/dotnet/aspnetcore/pull/67481) — clarified `ActionLink` URL-generation documentation for null protocol and host behavior.
- [dotnet/docs #54567](https://github.com/dotnet/docs/pull/54567) — documented `sizeof` behavior for enum types in the C# language reference.
- [dotnet/docs #54559](https://github.com/dotnet/docs/pull/54559) — corrected an ASP.NET workload typo in the .NET microservices documentation.

### In review

- [OrchardCore #19491](https://github.com/OrchardCMS/OrchardCore/pull/19491) — adds a safe breadcrumb back link using the existing local `returnUrl` flow.
- [SQLAlchemy #13417](https://github.com/sqlalchemy/sqlalchemy/pull/13417) — improves typing in the legacy serializer extension using protocols, explicit boundaries, and targeted casts.

## Other Projects

### [Enterprise AI Toolkit](https://github.com/mahdiaghtaee/enterprise-ai-toolkit)

An early .NET foundation for provider-independent AI contracts, with a runnable sample, tests, and CI.

### [Fast Fair Wait-Free Locks](https://github.com/mahdiaghtaee/fast-fair-wait-free-locks)

A research-to-code project about concurrency, fairness, and wait-free synchronization.

### [Persian License Plate Recognition](https://github.com/mahdiaghtaee/persian-license-plate-recognition)

An archived computer-vision study project for Persian license-plate and character recognition.

## Technical Focus

**Backend:** C#, ASP.NET Core, REST APIs, SQL Server, PostgreSQL  
**AI systems:** document processing, semantic search, RAG, provider abstraction  
**Infrastructure:** Docker, Docker Compose, Redis, CI, service-oriented architecture  
**Engineering:** API contracts, database workflows, architecture documentation, integration testing  
**Open source:** .NET, ASP.NET Core, OrchardCore, SQLAlchemy

## What I Can Discuss in an Interview

- deciding when a .NET application should call a separate Python service and when a modular application is simpler;
- evolving a deterministic local workflow toward durable vector storage and background processing;
- building test paths that do not depend on external AI providers;
- designing SQL-heavy workflows, reporting systems, and enterprise integrations;
- responding to maintainer review and improving code without expanding scope unnecessarily.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
