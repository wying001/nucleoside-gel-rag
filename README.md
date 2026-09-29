# Nucleoside Gel RAG

Tools, precomputed results, and interactive dashboards for retrieval-augmented prediction of nucleoside gel formation.

## Contents

| Folder | Purpose | Getting started |
| --- | --- | --- |
| [Evaluation dashboard](nucleoside-gel-rag-evaluation-dashboard/) | Compare prediction accuracy and inspect model inputs and outputs | Open its `index.html` in a browser |
| [Semantic similarity dashboard](nucleoside-gel-rag-text-embedding-3-large-similarity-dashboard/) | Explore precomputed text-embedding-3-large similarity scores | Open its `index.html` in a browser |
| [Prediction web app](nucleoside-gel-rag-webapp/) | Run S0-S3 predictions with bundled molecular descriptors | Run `python server.py` in that folder; see its README for dependencies and API configuration |
| [Reference overlap analysis](overlap-summary/) | Compare retrieved reference sets and literature overlap | See the folder README for Python commands |
| [Quantitative linguistic analysis](quantitative-linguistic-analysis/) | Reproduce Figure 3a-d from bundled CSV files | See the folder README for dependencies and commands |

## Download and use

Clone or download the complete repository, keeping the directory structure intact. The static dashboards include 13,550 detail pages in total and work locally without API keys or a Python server. Allow the download to finish before opening them.

The prediction web app requires a local Python server and an OpenAI-compatible API configuration. Credentials and prediction history stay in local files excluded from Git.

The analysis folders include their required input tables and precomputed results. Embedding caches are excluded; the quantitative analysis README describes optional cache regeneration. Its subfolders share data and helper modules, so keep them together.

Maintainer-only dashboard generation scripts, duplicate dashboard JSON, Python caches, credentials, and local run history are not part of this distribution.
