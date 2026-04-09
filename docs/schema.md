# Schema Draft

## documents
- id
- path
- kind
- language
- checksum
- modified_at

## chunks
- id
- document_id
- chunk_type
- heading_path
- text

## symbols
- id
- document_id
- kind
- name
- qualified_name
- parent_symbol_id
- start_byte
- end_byte
- signature
- docstring

## edges
- id
- src_symbol_id
- dst_symbol_id
- edge_type

## doc_links
- id
- document_id
- symbol_id
- link_type

## fts_chunks
FTS5 table over chunk text and possibly symbol text fields.
