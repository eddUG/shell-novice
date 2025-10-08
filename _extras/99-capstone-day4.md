---
layout: page
title: session 4 —  Windows and Genotype snapshot
---

Windows locate concentration; a genotype snapshot links biology to metadata.

**Assignment:**
1. Reading rows from `regions.bed`, how will you **count PASS variants per window** and write one table with `region_name<TAB>count`?
2. What sequence of steps will you use to **select the first PASS variant row** and **extract just the `GT` calls** (one per sample, same order as the VCF header)?
3. How can you **join GT calls to populations** (using your Day 2 maps) and **count non-reference carriers** (`0/1` or `1/1`) per population?

> ### Deliverables
> - `results/pass_variants_by_region.tsv`  
> - `results/first_variant_gts.txt`  
> - `results/first_variant_carriers_by_population.txt`
{: .callout}

> ### Solution (collapsed)
> Instructors: include reference loops and `awk` predicates here.
{: .solution}
