# Interview Guide

## One-minute Explanation

Enterprise AI Document Assistant is a local-first reference project for integrating document retrieval into an enterprise backend. ASP.NET Core owns the public API, document metadata, local extraction, chunking, deterministic embeddings, semantic retrieval, and source-aware answer construction. A separate Python FastAPI service currently provides an HTTP boundary for future document-intelligence work. PostgreSQL stores document metadata, Redis is included for future caching and background workflows, and Docker Compose runs the complete development environment.

## Why Include a Python Service?

The current deterministic workflow runs in .NET so it remains easy to test and inspect. The Python service establishes a replaceable boundary for future document libraries, embedding providers, or model integrations. This also makes the trade-off visible: a separate service adds network, deployment, and observability costs that are only justified when Python-specific capabilities require them.

## Why Deterministic Embeddings?

They keep the project runnable without provider credentials or cost and make test behavior repeatable. They are not presented as production-quality embeddings. A real deployment would compare retrieval quality, latency, privacy, and cost before selecting a model.

## Main Limitation

The semantic index is currently in memory. It is suitable for demonstrating the flow but not durable. The planned next step is a vector-store abstraction with PostgreSQL and pgvector.

## Production Changes

Before using the system with business documents, I would add authentication and authorization, tenant isolation, secure storage, malware scanning, background indexing with retries, pgvector persistence, audit logging, OpenTelemetry, secret management, TLS, backup and retention policies, and defenses against prompt injection and unauthorized retrieval.

## Questions I Expect

### Why services instead of one application?

The Python boundary demonstrates how provider-specific document or AI tooling could be isolated. For the current local implementation, the .NET API performs the deterministic pipeline. I would keep the system as a modular application until deployment, scaling, ownership, or library requirements justify moving more processing into the Python service.

### How would you make indexing reliable?

Persist an indexing job, process it asynchronously, use idempotent chunk writes, store processing states, apply bounded retries, and send repeated failures to a dead-letter path. The upload request should return a document ID and processing status rather than waiting for large files.

### How would you evaluate retrieval?

Create a representative question-and-document set and measure retrieval relevance, source coverage, ranking quality, latency, and failure cases. Provider decisions should be based on that evaluation rather than model popularity alone.
