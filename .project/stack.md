# Stack

## Primary Language

Python

## Why Python

Python is the best fit for V1 because it supports:

- fast iteration
- strong filesystem tooling
- good SQLite support
- easy CLI development
- integration with parsing libraries and shell workflows
- low friction for experimentation and refactoring

The goal is to build a useful working tool quickly without unnecessary language overhead.

---

## Core Technologies

### Python
Used for:
- orchestration
- crawling
- parsing coordination
- indexing
- search query handling
- CLI commands

### SQLite
Used for:
- local metadata storage
- symbol storage
- relationship storage
- chunk storage
- fast local queries

Why:
- simple
- local-first
- single-file database
- low operational overhead

### SQLite FTS5
Used for:
- full-text search over document chunks
- searching notes, markdown, extracted text, and possibly symbol text fields

### Tree-sitter
Used for:
- parsing source code
- extracting symbols
- supporting structural queries and file outlines

This is the core of the code intelligence layer.

---

## Likely Python Libraries

These are expected candidates, not final law.

### CLI
- `typer` or `argparse`

### Database
- built-in `sqlite3`
- possibly a light query or migration helper later if needed

### Parsing
- Tree-sitter Python bindings
- language grammars for selected languages

### File handling
- `pathlib`
- `hashlib`
- `os`
- `shutil`
- `mimetypes` if needed

### Testing
- `pytest`

---

## Initial File Types to Support

### Code
- Python
- possibly one additional language later

### Documents
- Markdown
- TXT

### Later
- extracted PDF text
- extracted DOCX text
- config files
- code comments/docstrings as indexed material

---

## Operating Environment

Primary environment:
- Ubuntu

Secondary environment:
- WSL2 Ubuntu

The tool should be designed to run well in a terminal-first environment.

---

## Storage Model

### Filesystem
Stores:
- actual repo files
- documents
- notes
- project content

### SQLite index
Stores:
- file metadata
- checksums
- chunks
- symbols
- relationships
- retrieval metadata

The database is an index layer, not the main content source.

---

## Search Model

V1 should support three retrieval styles:

### 1. Lexical search
Exact or near-exact text matching

### 2. Structural search
Symbol and outline retrieval

### 3. Relationship-aware search
Related symbols, documents, parents, and ownership

Semantic/vector search is not required for V1.

---

## Deferred Technology

These may be good later, but are not day-one requirements:

- PostgreSQL
- pgvector
- graph database
- background indexing daemon
- web UI
- language server protocol integration
- multi-user network service

---

## Why Not Start with PostgreSQL

PostgreSQL is powerful, but V1 does not need:

- a running database server
- networked service complexity
- multi-user concurrency
- extra infrastructure

SQLite is a better fit until real scaling pressure appears.

---

## Why Not Start with a Graph Database

A graph database may become useful later, but V1 can model relationships well enough with relational tables such as:

- symbols
- edges
- document links

That keeps the system simpler and easier to reason about.

---

## Formatting and Quality Tools

These are good candidates for the project itself:

- formatter: `ruff format` or `black`
- linting: `ruff`
- testing: `pytest`

Exact tooling can be finalized once the repo is scaffolded.

---

## Summary

V1 stack:

- Python
- SQLite
- SQLite FTS5
- Tree-sitter
- terminal CLI
- pytest
- lightweight lint/format tooling

This stack is intentionally simple, local, and strong enough for the real task.
