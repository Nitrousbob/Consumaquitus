# Rules

## Implementation Rules

1. Keep filesystem discovery separate from parsing.
2. Keep parsing separate from database writes.
3. Keep search logic separate from CLI formatting.
4. Do not treat the database as the canonical source of file content.
5. Support one language well before supporting many languages poorly.
6. Avoid plugin systems until multiple real parsers require them.
7. Preserve source references such as path and byte range where practical.
8. Prefer simple modules and clear composition over premature abstraction.
9. Add semantic search only after lexical, structural, and relational retrieval are useful.
10. Keep v1 understandable by one person without extra explanation.
