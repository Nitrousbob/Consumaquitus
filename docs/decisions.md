# Decisions

## D-001: Filesystem is the source of truth
Status: Accepted

The filesystem remains the canonical source for code and documents.
The database is a derived index for retrieval.

Why:
- simpler mental model
- easier reindexing
- safer than duplicating canonical content into the database

---

## D-002: SQLite is the v1 index backend
Status: Accepted

Use SQLite for local metadata, symbols, chunks, and relationships.

Why:
- local-first
- simple deployment
- single-file storage
- enough power for v1

---

## D-003: FTS5 is the v1 text search layer
Status: Accepted

Use SQLite FTS5 for full-text search over document chunks and selected symbol text.

Why:
- efficient local text search
- no extra service required
- fits the local-first architecture

---

## D-004: Tree-sitter is the v1 code structure layer
Status: Accepted

Use Tree-sitter to parse at least one language for symbol extraction and outlines.

Why:
- structural retrieval
- exact symbol boundaries
- better than plain text scanning for code navigation

---

## D-005: Semantic search is deferred to v2
Status: Accepted

Do not build embeddings/vector search into the first version.

Why:
- exact, structural, and relational retrieval are higher-value first
- keeps v1 simpler
- avoids premature complexity
