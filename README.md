# Repolex Knowledge Graph of twisted/newsbuilder

RDF knowledge graph data for [twisted/newsbuilder](https://github.com/twisted/newsbuilder), parsed by [repolex](https://repolex.ai).

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
rlex download twisted/newsbuilder
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5de0b3d90f0a06f54e820f8b3520364e96b7111c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5de0b3d90f0a06f54e820f8b3520364e96b7111c
│           └── chunk-001.nq.gz
├── blob
│   ├── 16abedc6086245773455ef56f4bf8330ffd4af3e.nq.gz
│   ├── 1712aa033f96869465d0bf7b33aabb555f73524b.nq.gz
│   ├── 2610bc0e89fe06cf8625fcba01858f708b4f0e22.nq.gz
│   ├── 2cacf9b72c607b7242b1a5a58e76f2ca2feef911.nq.gz
│   ├── 365e3bc04ecec2f150e3753b2f12ed64d4a3d104.nq.gz
│   ├── 3c05052c3c328b46e85ebf52e5817f4c32f751bd.nq.gz
│   ├── 5d7e4eb9c124ef798f54a948df7d0181471e73f9.nq.gz
│   ├── 64d460da8e27cfd6fcfa51adf63b122c5265921a.nq.gz
│   ├── 7cfcc7f7ab13f6c8d2420f4639d4c661a1b2d172.nq.gz
│   ├── a5ac945ded6792d3bec5c02a4868e18437a3c580.nq.gz
│   ├── c3884dd8e47d744316a4ef0f68719d38e647b4c2.nq.gz
│   ├── e3ffb015840b2178dd2df22a7648ea947b22cae4.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f4b5a3c58f04e12fd0954e3948df22d084ee7ac6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5de0b3d90f0a06f54e820f8b3520364e96b7111c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[twisted/newsbuilder](https://github.com/twisted/newsbuilder)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
