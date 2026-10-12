# Repolex Knowledge Graph of scrapy/dirbot

RDF knowledge graph data for [scrapy/dirbot](https://github.com/scrapy/dirbot), parsed by [repolex](https://repolex.ai).

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
rlex download scrapy/dirbot
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 8e995447361ad83f6693d2e07d17d90912268ace
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 8e995447361ad83f6693d2e07d17d90912268ace
│           └── chunk-001.nq.gz
├── blob
│   ├── 0d20b6487c61e7d1bde93acf4a14b7a89083a16d.nq.gz
│   ├── 4742811219526e703a2db061d9c0ccdbdfe7b2ec.nq.gz
│   ├── 59d02a55f48849ef92d31ab907b2ca80c22f6872.nq.gz
│   ├── 6ecb2ffcda20432d055d03d70851ff2e969417f8.nq.gz
│   ├── 9955c530fd7212200587b1957b3128688d388d88.nq.gz
│   ├── b1e341f6f4d54969b8e628ba5cef10b61660dc4c.nq.gz
│   ├── b6d886d54cfc9929e7f1fa2188f1442d6383f224.nq.gz
│   ├── be305663f621919adae79019f96de10a05ce55d0.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── fac72ad14314e4c78d777c79ca4b5e6c09e99887.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 8e995447361ad83f6693d2e07d17d90912268ace.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 17 files
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

[scrapy/dirbot](https://github.com/scrapy/dirbot)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
