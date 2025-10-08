---
title: "Capstone Introduction — Mini-AG1000G with the Unix Shell"
teaching: 10
exercises: 5
questions:
- "How can the Unix shell support a small but realistic bioinformatics workflow?"
- "What data will we use and what will we produce by the end?"
objectives:
- "Understand the scope and deliverables of the capstone."
- "Review prerequisites and confirm the project directory layout."
- "Know where the toy AG1000G data live and what each file contains."
keypoints:
- "We will use only core Unix tools (no bioinformatics software installs)."
- "You’ll build a small, reproducible workflow over five one-hour sessions."
- "Results, scripts, and logs will document exactly what you did."
---

### Motivation

You’ve practiced navigation, pipes & filters, loops, and shell scripts. This **capstone** pulls those skills together on a **tiny, AG1000G-style** dataset to model a realistic genomics task while keeping runtime and complexity low.

We will **lean on core shell utilities** to organize a project, inspect data, summarize variants and metadata, automate steps, and record what we did so the work is **repeatable and auditable**.

### What we will build (big picture)

Over five days (≈1 hour/day), you will:

1. **Set up** a clean project (folders, logs).
2. **Explore metadata** and create tidy summaries (species, population, country).
3. **Summarize variants** by chromosome, filter, and ALT allele.
4. **Query regions** and take a **genotype snapshot** mapped to populations.
5. **Automate** the workflow with a driver script and **reflect** on benefits/limits.

All outputs land in `results/`, and your commands are captured in `logs/`.  
The final script `scripts/run_all.sh` recreates the analysis end-to-end.

### Prerequisites

- Completed the **Unix shell** episodes: navigation, globbing, pipes & filters, loops, simple scripts.
- Comfortable running commands like `grep`, `cut`, `sort`, `uniq`, `awk`, `wc`, `head`, `tail`, `less`, `find`, `xargs`, and using `|`, `>`, `>>`.
- You have the practice data unzipped and can `cd` into the project root.

### Data (small AG1000G bundle)

Place these files under `data/`:

- **`variants_subset.vcf.gz`** — miniature, multi-chromosome VCF (≈120 variants) with `CHROM, POS, REF, ALT, QUAL, FILTER, INFO, FORMAT` and per-sample columns. The only FORMAT field is `GT` (genotype: `0/0`, `0/1`, `1/1`).
- **`samples.tsv`** — sample metadata (columns: `sample_id, species, population, country, latitude, longitude`).
- **`regions.bed`** — small windows to summarize by (columns: `chrom, start, end, name`).

> The dataset is synthetic and intentionally tiny so commands run instantly on any laptop.

### Project structure

We will use the following layout:
>```bash
> ag1000g-mini/
> ├── data/ # input files (read-only)
> ├── results/ # derived outputs (created during the capstone)
> ├── scripts/ # your shell scripts
> └── logs/ # run logs and notes
>```

```bash
ag1000g-mini/
├── data/ # input files (read-only)
├── results/ # derived outputs (created during the capstone)
├── scripts/ # your shell scripts
└── logs/ # run logs and notes
```

ag1000g-mini/
├── data/ # input files (read-only)
├── results/ # derived outputs (created during the capstone)
├── scripts/ # your shell scripts
└── logs/ # run logs and notes
