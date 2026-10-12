# Repolex Knowledge Graph of fabric/patchwork

RDF knowledge graph data for [fabric/patchwork](https://github.com/fabric/patchwork), parsed by [repolex](https://repolex.ai).

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
rlex download fabric/patchwork
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6768f7880c23d041a6cd3a36d0f2660b50b183a4
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6768f7880c23d041a6cd3a36d0f2660b50b183a4
│           └── chunk-001.nq.gz
├── blob
│   ├── 0b64402d12377dab8c62a962a1fa085f6da52c59.nq.gz
│   ├── 0e92cb501f85115b136be3326d89c896e82fca6e.nq.gz
│   ├── 1e6851227161acfe7aee1c0f769aec18925d4b87.nq.gz
│   ├── 27e880d48b41a1d063c5e6a4d1663d25159ced9b.nq.gz
│   ├── 313eff74e5377a184dba645457f070fd6ed7b32b.nq.gz
│   ├── 324732d13b1f5a17ecb0d3a82d1b9b21347ec7f8.nq.gz
│   ├── 56652a9be637a7bcb592fd2084c2b9fb690372b9.nq.gz
│   ├── 5d7356fd6de592a34a5635b0642af055c913ab34.nq.gz
│   ├── 5fc9d52bad132750122442a97be0e798b60e469f.nq.gz
│   ├── 6a3ed99ca7eb4bf5dd57a7fb5b7c57970384c864.nq.gz
│   ├── 705a4753ad5738b01707629ee7d4cdbbc8e926a6.nq.gz
│   ├── 767fe738f16964c65b0cdaea1b8c9e2fb3140e9b.nq.gz
│   ├── 79ffeff358eed74c42d4171f026fc257b03f67a7.nq.gz
│   ├── 7a11eeb4ea839c60ffd7267814104449742c002b.nq.gz
│   ├── 7a8a6f1a650660b4014e212cc8e5853b9013049c.nq.gz
│   ├── a639370fa957540c5bbfeedc3cd0aa5e3e5458fb.nq.gz
│   ├── aa4cff51b44255cbdca3719be6a43140878e76e8.nq.gz
│   ├── ad388277b0cfc5bb078a0338d31663601565b3e6.nq.gz
│   ├── ae3560aa83b38023bbb19c139d53a4f033822428.nq.gz
│   ├── b7e1ca4b8c8401a1472974442158e3dc4f85822f.nq.gz
│   ├── c4443897dda9104e2d64326755bbda73ff369266.nq.gz
│   ├── ce6763a8a05bf56def0c966288e252c73802535d.nq.gz
│   ├── d5329c8f1637e7c3e2cdfde4ee3b0b476b65bb57.nq.gz
│   ├── d737d945aae910fa37c2c94c54d11ae4e111715c.nq.gz
│   ├── d9065d110d51388d7105c672a74024af75f7185b.nq.gz
│   ├── da9c516dd744b6c88dd8c91f58f7bcf8f7e8341b.nq.gz
│   ├── dbf725ae30feab2da3e87956403adcfc36cdf615.nq.gz
│   ├── ded49aedb17c31baca094d152a5738782f421283.nq.gz
│   ├── e26e4a1989fd12a46da08aa9ff0d7dfe330613ee.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e7224a4bacec2259b599e0283fc7b1618334601d.nq.gz
│   ├── e7292da1bbfbcdf7984af90ae8ce380d260be47d.nq.gz
│   └── f32b3147a10fe6b92bd7ee3ea55369c23ced2f74.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6768f7880c23d041a6cd3a36d0f2660b50b183a4.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 41 files
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

[fabric/patchwork](https://github.com/fabric/patchwork)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
