# Project: Code-Doc-Indexer

## Project Type

Local-first developer tool

## Purpose

Code-Doc-Indexer is a local search and indexing tool for codebases and related documentation.

Its purpose is to make it easy to:

- find exact functions, classes, methods, and modules
- search documents and notes quickly
- retrieve targeted implementation instead of scanning large files
- connect code symbols to related code and related documents
- support structured exploration of a repository

This project is meant to be a practical developer tool, not a vague AI wrapper.

---

## Core Problem

Traditional repo exploration often requires:

- opening many large files
- scanning broad regions of code
- guessing where symbols are defined
- manually connecting docs to implementation
- re-reading context that could be indexed once

This project should reduce that friction by building a searchable local index over code and documents.

---

## Primary Goals

### 1. Exact code retrieval
Find specific symbols and jump to their implementation.

### 2. Document retrieval
Search markdown, notes, and extracted document text efficiently.

### 3. Structural understanding
Represent repo structure in a way that supports outlines, symbol lookup, and targeted bundles.

### 4. Relationship-aware lookup
Support related-item queries such as:
- what file owns this symbol
- what parent symbol contains this method
- what docs mention this symbol
- what symbols are related by imports, hierarchy, or references

### 5. Local-first operation
Run on Ubuntu locally without requiring a remote service.

---

## Non-Goals for V1

The first version should not try to be:

- a full IDE
- a hosted SaaS product
- a universal multi-user platform
- a full graph analytics platform
- a giant AI agent framework
- a perfect cross-language code intelligence engine on day one

It should solve a real local retrieval problem first.

---

## Target Users

Initial target user:
- me, working locally on Ubuntu/WSL

Possible future users:
- solo developers
- small internal teams
- anyone who wants better local repo and doc navigation

---

## Primary Use Cases

- find a function by name
- show the exact implementation of a symbol
- search a repo’s documentation by keyword
- inspect the outline of a file
- connect a design note to code symbols
- prepare context for an AI coding or analysis workflow
- reduce the need to manually scan large files

---

## Source of Truth Model

The filesystem remains the source of truth for:

- code files
- notes
- markdown docs
- extracted document text files

The database is an index and retrieval layer, not the canonical source of project content.

---

## Success Criteria for V1

V1 is successful if it can:

- scan a local repo
- index file metadata
- index markdown/text content
- parse at least one programming language for symbols
- support text search
- support symbol search
- show exact implementation ranges
- show file outlines
- support basic relationship queries

---

## Constraints

- should run locally
- should be simple enough to understand and maintain
- should be fast enough for real use on medium-sized repos
- should not require unnecessary infrastructure
- should prefer clear architecture over premature complexity

---

## Design Philosophy

This project should be:

- local-first
- searchable
- structured
- explainable
- incremental
- practical

Use the smallest architecture that cleanly supports the real retrieval tasks.

---

## Notes

This project is also a dogfooding project for the shared AI operating system in `~/ai`.

That means the project should be built using:

- clear architecture guidance
- explicit project rules
- reusable workflows
- specialist roles where useful

But the code itself should remain in its own project repo.
