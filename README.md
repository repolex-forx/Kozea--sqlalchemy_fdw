# Repolex Knowledge Graph of Kozea/sqlalchemy_fdw

RDF knowledge graph data for [Kozea/sqlalchemy_fdw](https://github.com/Kozea/sqlalchemy_fdw), parsed by [repolex](https://repolex.ai).

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
rlex download Kozea/sqlalchemy_fdw
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── eaa57336a8e6fad214a3b32c797aee12866a18ff
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── eaa57336a8e6fad214a3b32c797aee12866a18ff
│           └── chunk-001.nq.gz
├── blob
│   ├── 2340e2c6ab527c23ded33f6d64f0bc88d82dcff7.nq.gz
│   ├── 726587a3cf8731a429a55196d10bc379d470788e.nq.gz
│   ├── 89b4a700e3afa636561a974dce189ab280515a91.nq.gz
│   ├── c811341b8aacc1b215b89e3fa0c521c8c0be16d6.nq.gz
│   ├── db1c287b5f380d8e21de0e52f9ef5897efdbeb86.nq.gz
│   └── dcc1a49e6247fea43c356c1d9517934285f6b399.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── eaa57336a8e6fad214a3b32c797aee12866a18ff.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 13 files
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

[Kozea/sqlalchemy_fdw](https://github.com/Kozea/sqlalchemy_fdw)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
