# Portfolio Summary

## Project

Enterprise AI Document Assistant

## Purpose

A local-first document assistant that demonstrates how deterministic retrieval can be integrated into an ASP.NET Core backend while preserving an explicit FastAPI boundary for future Python-specific processing.

## Current Contribution

The project currently covers:

- document upload and metadata management;
- PostgreSQL persistence for document metadata;
- .NET-based text extraction, chunking, deterministic embeddings, semantic retrieval, and source-aware answer construction;
- a FastAPI health and indexing boundary for future Python processing;
- Docker Compose orchestration;
- a small Web UI and Swagger documentation;
- integration tests, health checks, sample documents, and demo scripts.

## Engineering Decisions

- Kept the current deterministic workflow in ASP.NET Core for inspectability and repeatable tests.
- Preserved an HTTP boundary for future Python-specific libraries without claiming those capabilities are already implemented.
- Used deterministic local embeddings to avoid provider setup and cost.
- Kept current limitations explicit instead of presenting the project as production-ready.
- Documented the path toward pgvector, background processing, authentication, observability, and audit logging.

## Resume-ready Description

Designed and implemented a local-first enterprise document-assistant reference system using ASP.NET Core, Python FastAPI, PostgreSQL, Redis, and Docker Compose. Built document upload, metadata persistence, text extraction, chunking, deterministic embeddings, semantic retrieval, source-aware answers, integration tests, health endpoints, and reproducible local demos. Documented the current FastAPI boundary and the path toward pgvector, background indexing, authentication, audit logging, and observability.
