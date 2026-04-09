# Code-Doc-Indexer

Local-first code and document indexing tool for exact symbol lookup, document search, and relationship-aware retrieval.

## Goals

- find functions, classes, and methods quickly
- search markdown and notes
- retrieve exact implementations instead of scanning large files
- connect symbols to related symbols and related docs

## V1 stack

- Python
- SQLite
- SQLite FTS5
- Tree-sitter

## Status

Early scaffold / architecture phase

## Core idea

The filesystem is the source of truth.
The database is a searchable index over code and documents.
