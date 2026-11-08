# Repolex Knowledge Graph of canonical/provd-snap

RDF knowledge graph data for [canonical/provd-snap](https://github.com/canonical/provd-snap), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download canonical/provd-snap
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9758ea877f830144e8394733359f8893a72f38b5
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9758ea877f830144e8394733359f8893a72f38b5
│           └── chunk-001.nq.gz
├── blob
│   ├── 2b60a26f73e4587797cdbc05d91740736d4197c9.nq.gz
│   ├── 3477ee9a5b7da4f8a64af7d5a910ddb8ea565bc8.nq.gz
│   ├── 9ed6d53a828b3aaefeb9f3d56d3d7a2b628250bf.nq.gz
│   ├── ea8b3d611c694889908c3cff25977c09b7f87118.nq.gz
│   └── f8720a0335bb0a9d1032fe093a1c4f6735df787b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9758ea877f830144e8394733359f8893a72f38b5.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 12 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[canonical/provd-snap](https://github.com/canonical/provd-snap)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
