
---

## `docs/roadmap.md`

```md
# Roadmap

## Project Direction

Code-Doc-Indexer will be built in stages, with each stage delivering a usable improvement.

The goal is to get real retrieval value early rather than overbuild infrastructure first.

---

## Phase 0: Scaffold and baseline

### Goal
Create a clean project skeleton and working development loop.

### Deliverables
- repo structure in place
- Python project initialized
- CLI entry point created
- SQLite connection working
- basic docs in place
- test setup working
- lint/format tooling selected

### Done when
- project runs from CLI
- test command works
- database file can be created
- code layout is stable enough to begin feature work

---

## Phase 1: File crawl and metadata index

### Goal
Index local file metadata so the tool knows what exists.

### Deliverables
- recursive scan of target folder
- file classification
- path storage
- timestamp storage
- checksum or hash support
- skip rules for ignored files/directories

### Example commands
- `indexer scan ~/projects/myrepo`
- `indexer files`

### Done when
- files can be scanned and stored reliably
- re-running scan updates changed metadata cleanly

---

## Phase 2: Document full-text search

### Goal
Make documents and notes searchable.

### Deliverables
- markdown/txt extraction
- chunking strategy for text content
- FTS5 virtual table
- text search command
- readable search result formatting

### Example commands
- `indexer search text "MapManager"`
- `indexer docs "retry logic"`

### Done when
- document text can be searched quickly
- results point back to useful files or sections

---

## Phase 3: Symbol indexing for one language

### Goal
Support exact code symbol retrieval for at least one language.

### Deliverables
- Tree-sitter integration
- one language parser working
- symbol extraction
- symbol storage in database
- file outlines
- exact symbol lookup

### Example commands
- `indexer search symbol "runSimulation"`
- `indexer outline file src/example.py`
- `indexer show symbol "WorldClass.update"`

### Done when
- the tool can find and display exact implementations for indexed symbols

---

## Phase 4: Relationship-aware retrieval

### Goal
Support related-item queries beyond plain text and plain symbols.

### Deliverables
- parent-child symbol relationships
- basic import relationships
- symbol-to-document link support
- related-symbol query
- related-doc query where possible

### Example commands
- `indexer related symbol "MapManager"`
- `indexer links doc docs/architecture.md`

### Done when
- the tool can show meaningful related entities instead of isolated results only

---

## Phase 5: Incremental reindex and cleanup

### Goal
Reduce unnecessary reprocessing and improve reliability.

### Deliverables
- changed-file detection
- partial reindex support
- clearer error handling
- cleaner scan/update workflow
- better ignore/config behavior

### Done when
- repeated indexing is fast enough for normal use
- changed files can be updated without full rebuild every time

---

## Phase 6: UX and result quality improvements

### Goal
Make the tool nicer and more useful in daily use.

### Deliverables
- better CLI output formatting
- ranking improvements
- optional JSON output
- clearer result previews
- better error messages
- config file support if needed

### Done when
- the tool feels smooth enough to use regularly

---

## Deferred / Later Ideas

These are intentionally not V1 requirements.

### Semantic search
- embeddings
- fuzzy retrieval
- concept search beyond keywords

### More languages
- expand parser support once first language is solid

### More document formats
- extracted PDF text
- extracted DOCX text
- richer metadata handling

### Persistent service mode
- long-running daemon
- background watch mode
- optional API layer

### Alternate backend
- PostgreSQL if scaling or shared access becomes necessary

### Advanced relationship mapping
- deeper call graphs
- stronger reference tracking
- richer doc-to-code linking

---

## Build Order Recommendation

Use this build order:

1. scaffold project
2. crawl files
3. index docs
4. parse symbols for one language
5. support exact retrieval
6. add relationships
7. improve reindexing
8. improve UX

This keeps the project delivering value early.

---

## MVP Definition

The MVP should include:

- local scan
- file metadata storage
- text search for markdown/txt
- symbol search for one language
- exact implementation lookup
- file outline support
- basic relationship retrieval

That is enough to prove the concept.

---

## Anti-Bloat Rule

Do not add:
- semantic search
- graph database
- service mode
- multi-user support
- many languages
- fancy UI

before the MVP is genuinely useful.

---

## Success Checkpoint

The first serious checkpoint is reached when the tool can do this on a real repo:

- scan the repo
- search docs
- find a symbol
- show the implementation
- show related structure
- save time versus manual scanning

At that point, the project has earned the right to expand.
