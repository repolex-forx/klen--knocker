# Repolex Knowledge Graph of klen/knocker

RDF knowledge graph data for [klen/knocker](https://github.com/klen/knocker), parsed by [repolex](https://repolex.ai).

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
rlex download klen/knocker
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e6fc5188a7558fbc0e7b56f92162d8e944e4c746
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e6fc5188a7558fbc0e7b56f92162d8e944e4c746
│           └── chunk-001.nq.gz
├── blob
│   ├── 0ed413be3087cf5a0255ab409026b36d361b42b5.nq.gz
│   ├── 12161b4ecfced0b93f61159c5ae4adc1845a8210.nq.gz
│   ├── 18f22059c90aba88e55cbd6f8bde155e036b0bfd.nq.gz
│   ├── 20c850c6a393ec7d20a769f5602ead5f785d716d.nq.gz
│   ├── 236d95ef8670c7a96007807354d5e9edc0270ae9.nq.gz
│   ├── 23b6ebab49a6e61700b57db56449c323f9575820.nq.gz
│   ├── 33708980d57dbc08ad8ee60820ab1b7cbbcb9891.nq.gz
│   ├── 4159579acef0ac1242de9cee76c93e14e995beed.nq.gz
│   ├── 457dd694fa6f3a2f8a09ffc1c722aa79853aaaca.nq.gz
│   ├── 4ad98f70ec9cad20b737f9ed217bc29484b7faa8.nq.gz
│   ├── 5a0fa186dfa9d20dceb69b1f898c1eb1ba7a8ba8.nq.gz
│   ├── 5af9ab6e8fe6237ff42688e0513132149b7852d5.nq.gz
│   ├── 6700891209d8d7b81c74c786ca0f5d3374ab434b.nq.gz
│   ├── 7918ffe5f01d8fde7fa4eb36914a27e24649f989.nq.gz
│   ├── 856a8981120e969dd557ca86fdb99d6a2f55dcf8.nq.gz
│   ├── 94dbe2053518658a98a4d5de968fb74d2362313a.nq.gz
│   ├── a6ba41ccb9af8e2b44c47a6c89f783c87746a33a.nq.gz
│   ├── c0a49734dcf0e47aca61728277f727b9d8eaf2f2.nq.gz
│   ├── cb8cc2635ad715dc9006d26effd8cdc3aa75b7f5.nq.gz
│   ├── d99163591079a07442bf4cac2066cc4a24bfafc2.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f057ebf989d2b32f43e7a667028feb79d20ce5c5.nq.gz
│   ├── fbef9aabb7cf98851078c250cd0e462ae6511a04.nq.gz
│   └── fd3ad459fcdb974fd487cd6579025198626e5c54.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e6fc5188a7558fbc0e7b56f92162d8e944e4c746.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 31 files
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

[klen/knocker](https://github.com/klen/knocker)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
