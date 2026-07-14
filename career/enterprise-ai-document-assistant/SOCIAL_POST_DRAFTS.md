# Project Sharing Drafts

These drafts describe the project without presenting unfinished work as production-ready.

## LinkedIn

I have been working on an Enterprise AI Document Assistant to explore how document retrieval fits into a real backend architecture, not only a chatbot demo.

The project combines ASP.NET Core, Python FastAPI, PostgreSQL, Redis, and Docker Compose. The current deterministic workflow runs in the .NET API and covers document upload, metadata persistence, text extraction, chunking, local embeddings, semantic retrieval, and source-aware answers. The Python service currently provides a separate HTTP boundary for future document and model integrations.

I deliberately started with a local deterministic pipeline so the complete system can be run and tested without external AI credentials. The current limitations are documented as well: the semantic index is in memory, processing is synchronous, and authentication and tenant isolation are future work.

The next technical milestone is persistent vector storage with PostgreSQL and pgvector, followed by background indexing, audit logging, and observability.

Repository: https://github.com/mahdiaghtaee/enterprise-ai-document-assistant

I would be interested in feedback on the current .NET implementation, the Python service boundary, and the planned pgvector design.

## Short GitHub / Community Post

I am building a local-first enterprise document-assistant reference project with ASP.NET Core, FastAPI, PostgreSQL, Redis, and Docker Compose.

It currently demonstrates upload, extraction, chunking, deterministic embeddings, semantic search, and source-aware answers without requiring a paid AI provider. The deterministic pipeline currently runs in .NET, while FastAPI provides a boundary for future Python-specific processing.

Repository: https://github.com/mahdiaghtaee/enterprise-ai-document-assistant

Technical feedback and focused contributions are welcome.

## Persian LinkedIn Draft

مدتی است روی یک نمونه‌پروژه «دستیار اسناد سازمانی» کار می‌کنم تا بررسی کنم قابلیت‌های جست‌وجوی معنایی و RAG چطور باید وارد یک معماری واقعی Backend شوند، نه اینکه فقط به شکل یک دموی چت‌بات باقی بمانند.

در نسخه فعلی، ASP.NET Core علاوه بر API و نگهداری متادیتا، مسیر قطعی استخراج متن، قطعه‌بندی، embedding محلی، بازیابی معنایی و پاسخ همراه با منبع را اجرا می‌کند. سرویس Python FastAPI فعلاً یک مرز HTTP مستقل برای پردازش‌ها و Providerهای آینده فراهم می‌کند. PostgreSQL برای متادیتای اسناد، Redis برای زیرساخت آینده و Docker Compose برای اجرای محیط محلی استفاده شده‌اند.

نسخه فعلی عمداً بدون سرویس پولی AI قابل اجرا و تست است. محدودیت‌ها نیز شفاف مستند شده‌اند: ایندکس برداری فعلاً in-memory است، پردازش هم‌زمان انجام می‌شود و احراز هویت و جداسازی tenant هنوز در نقشه راه قرار دارند.

مرحله بعدی، ذخیره‌سازی پایدار بردارها با PostgreSQL و pgvector و سپس پردازش پس‌زمینه، audit logging و observability است.

مخزن پروژه:
https://github.com/mahdiaghtaee/enterprise-ai-document-assistant
