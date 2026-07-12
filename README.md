# Mahdi Aghtaee

**Senior .NET Developer | Enterprise Backend Systems | AI-enabled Applications | SQL Server**

I design and build backend systems with **C#**, **ASP.NET Core**, **SQL Server**, **PostgreSQL**, **Redis**, and **Docker**. My current work focuses on adding document processing, semantic search, and retrieval-augmented generation to business applications without losing the reliability and structure expected from enterprise software.

I use this profile to document real project work, architecture decisions, technical trade-offs, and open-source contributions. I prefer small, reviewable changes and clear engineering documentation over inflated claims or demo-only features.

## Current Project

### [Enterprise AI Document Assistant](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant)

[![GitHub stars](https://img.shields.io/github/stars/mahdiaghtaee/enterprise-ai-document-assistant?style=social)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/stargazers)
[![CI](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/actions/workflows/ci.yml)

I built this project to show how a document assistant can fit into a real backend architecture instead of existing as an isolated chatbot demo.

```text
Upload -> Extract -> Chunk -> Embed -> Search -> Ask -> Grounded sources
```

The system combines:

- ASP.NET Core for public APIs, orchestration, and document metadata;
- Python FastAPI for extraction, chunking, embeddings, and retrieval;
- PostgreSQL for document metadata;
- Redis as a foundation for caching and background work;
- Docker Compose for a reproducible local environment;
- integration tests, health endpoints, Swagger, sample documents, and an end-to-end demo.

The current version deliberately uses deterministic local embeddings and an in-memory semantic index. This keeps the workflow easy to run and test while making the next engineering steps clear: pgvector persistence, background indexing, authentication, audit logging, observability, and provider abstractions.

[Repository](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant) · [Engineering case study](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/CASE_STUDY.md) · [Architecture](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant/blob/main/docs/ARCHITECTURE.md) · [Quick start](https://github.com/mahdiaghtaee/enterprise-ai-document-assistant#quick-start)

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

A .NET foundation for provider-independent AI services, with a runnable sample, tests, and CI.

### [Fast Fair Wait-Free Locks](https://github.com/mahdiaghtaee/fast-fair-wait-free-locks)

A research-to-code project about concurrency, fairness, and wait-free synchronization.

### [Persian License Plate Recognition](https://github.com/mahdiaghtaee/persian-license-plate-recognition)

A computer-vision project for Persian license-plate and character recognition.

## Technical Focus

**Backend:** C#, ASP.NET Core, REST APIs, SQL Server, PostgreSQL  
**AI systems:** document processing, semantic search, RAG, provider abstraction  
**Infrastructure:** Docker, Docker Compose, Redis, CI, service-oriented architecture  
**Engineering:** API contracts, database workflows, architecture documentation, integration testing  
**Open source:** .NET, ASP.NET Core, OrchardCore, SQLAlchemy

## What I Can Discuss in an Interview

- designing service boundaries between .NET business APIs and Python AI components;
- evolving a local prototype toward authentication, tenant isolation, background processing, and observability;
- building deterministic test paths for systems that may later use external AI providers;
- designing SQL-heavy workflows, reporting systems, and enterprise integrations;
- responding to maintainer review and improving code without expanding scope unnecessarily.

## Contact

- GitHub: [@mahdiaghtaee](https://github.com/mahdiaghtaee)
