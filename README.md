# Nucleoside Gel RAG

Retrieval-augmented prediction of nucleoside-derived gel formation, with interactive evaluation dashboards and reproducible analyses.

## Overview

Whether a nucleoside-derived molecule forms a gel depends on both its molecular structure and the experimental conditions. This project studies how retrieved experimental examples and mechanistic explanations inform language-model predictions of gel formation.

The repository brings together a local prediction application, precomputed evaluation results, and analysis code. It supports exploration of prediction accuracy, semantic similarity between model rationales and literature-derived mechanisms, and overlap among retrieved reference sets.

## Explore the results

Two interactive dashboards provide access to the precomputed results:

| Dashboard | What you can explore |
| --- | --- |
| [Prediction evaluation](nucleoside-gel-rag-evaluation-dashboard/README.md) | Compare accuracy across models, retrieval strategies, and retrieval depths; inspect experimental conditions and the corresponding model inputs and outputs. |
| [Rationale similarity](nucleoside-gel-rag-text-embedding-3-large-similarity-dashboard/README.md) | Explore similarity scores calculated with `text-embedding-3-large`, compare strategies, and inspect individual molecule–experiment samples. |

To use either dashboard, download or clone this repository and open `index.html` inside the corresponding dashboard folder. Keep its `details/` folder alongside the main page. Both dashboards run locally in a browser without installation or API credentials.

The evaluation dashboard includes 12,900 molecule-round records. The similarity dashboard includes 650 model/sample detail pages. Similarity scores measure semantic alignment with reference text; they do not by themselves establish scientific correctness.

## Run a prediction

The [prediction web application](nucleoside-gel-rag-webapp/README.md) accepts a molecule as a SMILES string and one experimental condition, retrieves relevant examples, and requests a gel/no-gel prediction from an OpenAI-compatible language-model API.

It supports four strategies:

| Strategy | Retrieved context |
| --- | --- |
| S0 | No retrieved examples |
| S1 | Structurally similar molecules selected using 24 molecular descriptors |
| S2 | Structurally similar molecules, prioritizing matching experimental conditions |
| S3 | Condition-aware retrieval with mechanistic explanations |

With Python 3.10 or later and RDKit installed, start the application from the repository root:

```bash
cd nucleoside-gel-rag-webapp
python server.py
```

Open **http://127.0.0.1:8777** and enter your API settings in **Config**. Built-in molecules use the bundled descriptor values. Predicting an unfamiliar molecule requires a configured alvaDesc installation to calculate its descriptors. See the [application guide](nucleoside-gel-rag-webapp/README.md) for setup and usage details.

## Reproduce the analyses

### Reference-set overlap

The [reference overlap analysis](overlap-summary/README.md) compares references selected by descriptor-based and Morgan-fingerprint retrieval, with and without condition-aware selection. It reports Jaccard overlap and same-literature statistics at retrieval depths of 3, 5, and 6.

The folder includes the molecular database, precomputed descriptors, literature DOI mappings, analysis scripts, and summary tables. Follow its [reproduction instructions](overlap-summary/README.md#run) to regenerate the results.

### Quantitative linguistic analysis

The [quantitative linguistic analysis](quantitative-linguistic-analysis/README.md) contains the data and scripts for four complementary views of model rationales:

- **3a — Similarity distributions:** semantic similarity and alignment across retrieval strategies.
- **3b — Mean rationale–mechanism similarity:** comparisons by prediction outcome.
- **3c — Transition-group trajectories:** changes between adjacent retrieval strategies.
- **3d — Local mechanistic discrimination:** comparison with candidate reference mechanisms.

The bundled CSV files are sufficient to regenerate the figures without calling an embedding API. For recalculation from the underlying text, the folder also provides compressed source records and scripts for generating OpenAI, Gemini, and SemCSE embeddings. See the [analysis guide](quantitative-linguistic-analysis/README.md) for dependencies and commands.

## Get the repository

```bash
git clone https://github.com/wying001/nucleoside-gel-rag.git
cd nucleoside-gel-rag
```

You can also select **Code → Download ZIP** on GitHub. The repository includes complete offline detail pages and figure data, so allow the download to finish before opening the dashboards.
