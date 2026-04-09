# Architecture

## Architecture Summary

Code-Doc-Indexer should use a modular local-first architecture with clear separation between:

- crawling
- parsing
- indexing
- search
- relationship linking
- CLI interaction

This project does not need heavy enterprise layering, but it does need clean boundaries so it can grow without becoming tangled.

---

## Architecture Style

Recommended style:

**Modular pipeline architecture with a local index backend**

This means the system is organized into cooperating modules with clear responsibilities rather than deep abstract layers.

The flow is roughly:

1. discover files
2. classify files
3. extract content and structure
4. store normalized index data
5. query the index through targeted search commands

---

## Core Architectural Decision

The filesystem is the source of truth.

The database is a derived searchable index.

This means:
- files are read from disk
- metadata and extracted structure are stored in SQLite
- re-indexing is possible
- the tool does not try to replace the file system with a database-backed content store

This keeps the architecture simple and robust.

---

## Main Components

### 1. Crawler
Responsible for:
- walking directories
- identifying candidate files
- classifying file types
- recording paths, timestamps, and checksums
- determining what changed and needs reindexing

### 2. Parsers
Responsible for:
- extracting structural information from code
- extracting searchable text from documents
- breaking content into chunks where appropriate
- preserving source location references where useful

Different parser implementations may exist for:
- code files
- markdown/text documents
- future extracted document formats

### 3. Indexer
Responsible for:
- normalizing parsed results
- writing them into SQLite
- maintaining document, chunk, symbol, and edge tables
- managing updates and refreshes

### 4. Search Layer
Responsible for:
- full-text search
- symbol lookup
- implementation lookup
- outline retrieval
- relationship queries

The search layer should be query-focused, not mixed with parsing logic.

### 5. Link Layer
Responsible for:
- connecting code symbols and documents
- tracking parent-child symbol relationships
- storing symbol-to-symbol edges
- storing document-to-symbol relationships

### 6. CLI Layer
Responsible for:
- presenting commands
- receiving user query input
- displaying results in readable formats
- routing commands to the right internal modules

---

## Suggested Package Layout

```text
src/code_doc_indexer/
├── cli/
├── crawl/
├── parse/
├── index/
├── search/
├── links/
├── models/
└── util/
