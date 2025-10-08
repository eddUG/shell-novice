---
title: "Capstone — Mariam’s Mini-AG1000G Pipeline (5 Days)"
teaching: 5*60
exercises: 5*60
questions:
- "How can we organize, inspect, summarize, and automate a small genomics project using just the shell?"
- "How do we combine pipes, filters, loops, and scripts into a reproducible workflow?"
objectives:
- "Work through five question-driven sessions to build a complete pipeline."
- "Capture results and logs; finish with a single driver script."
keypoints:
- "Question-first prompts encourage planning before typing."
- "One page, five anchors — easy to follow, easy to print."
---

> ## Data bundle
> - **Download:** [AG1000G Toy Bundle]({% link data/ag1000g-toy-bundle.zip %})
> - Unzip into `data/` so you have:
>   - `data/variants_subset.vcf.gz`
>   - `data/samples.tsv`
>   - `data/regions.bed`
{: .callout}

## Plan of attack
- **Day 1:** Setup & Orientation  
- **Day 2:** Metadata Summaries  
- **Day 3:** Variant Summaries  
- **Day 4:** Windows & Genotype Snapshot  
- **Day 5:** Automate, Package, Reflect

Jump to: [Day 1](#day-1-setup--orientation) • [Day 2](#day-2-metadata-summaries) • [Day 3](#day-3-variant-summaries) • [Day 4](#day-4-windows--genotype-snapshot) • [Day 5](#day-5-automate-package-reflect)

---

## Day 1 — Setup & Orientation

**Narrative.** Mariam refuses “mystery data.” She first verifies what she has, where it is, and records this in a log.

**Guiding prompts (answer with shell commands):**
1. How will you **create** the project subfolders (`results/`, `scripts/`, `logs/`) if they don’t exist?
2. How will you **start a day log** that includes the current date/time?
3. Which command(s) let you **list file sizes** in `data/` and **append** that listing to your log?
4. How can you **peek safely** at the first few lines of `samples.tsv` and **count** how many lines it has?
5. What’s a safe way to **count non-header records** in the compressed VCF?

> ### Deliverables
> - `logs/day1.log` with sizes, peeks, and counts you ran.
> - Confirmed folder structure.
{: .callout}

> ### Solution (collapsed)
> Instructors: include your reference commands here using Carpentries’ `.solution` block.
{: .solution}

---

## Day 2 — Metadata Summaries

**Narrative.** Before touching variants, Mariam needs context: how many samples per species, population, country?

**Guiding prompts:**
1. How can you build a **descending count table** of samples per **population** from `samples.tsv` (skipping the header)?
2. How will you build a **descending count table** of samples per **species**?
3. What pipeline will produce the list of **unique country–population pairs** as a two-column TSV?
4. How will you create a **sample→population map** (two columns) for joining later?
5. How can you extract the **VCF sample order** from the `#CHROM` header line as one sample ID **per line**?

> ### Deliverables
> - `results/samples_by_population.txt`  
> - `results/samples_by_species.txt`  
> - `results/country_population.tsv`  
> - `results/sample_to_pop.tsv`, `results/vcf_sample_order.txt`
{: .callout}

> ### Solution (collapsed)
> Instructors: place the reference pipelines here.
{: .solution}

---

## Day 3 — Variant Summaries

**Narrative.** Big-picture numbers help spot issues early.

**Guiding prompts:**
1. Which one-liner gives the **number of PASS variants** (column 7 equals `PASS`)?
2. How do you build a **frequency table by chromosome** from the VCF body?
3. How do you list the **top 5 ALT alleles** (column 5), most frequent first?
4. How do you tally the **FILTER field distribution** (column 7), most frequent first?

> ### Deliverables
> - `results/variants_by_chrom.txt`  
> - `results/top_alt_alleles.txt`  
> - `results/filter_counts.txt`  
> - A brief count in `logs/day3.log` stating total PASS variants
{: .callout}

> ### Solution (collapsed)
> Instructors: include your exemplar commands here.
{: .solution}

---

## Day 4 — Windows & Genotype Snapshot

**Narrative.** Windows locate concentration; a genotype snapshot links biology to metadata.

**Guiding prompts:**
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

---

## Day 5 — Automate, Package, Reflect

**Narrative.** One command should reproduce everything.

**Guiding prompts:**
1. What should the **preamble** of a robust shell script include to stop on errors and create needed folders?
2. In what **order** will you call your pipelines to regenerate every result from Days 2–4?
3. Where will you **tee** progress messages and **key counts** so they land in a single run log?
4. How will you **verify** that expected output files exist (and optionally how many lines they contain)?
5. What **three bullet points** would you write in a reflection about (a) what worked, (b) what felt limiting, (c) what you’d automate next?

> ### Deliverables
> - `scripts/run_all.sh` (executable)  
> - `logs/run_all.log`, `logs/reflection.md`  
> - All `results/` tables regenerated by the script
{: .callout}

> ### Solution (collapsed)
> Instructors: include a reference `run_all.sh` here or link to the instructor guide.
{: .solution}

---

## Tips for staying question-driven
- **Plan first, then type.** Write your pipeline in plain language before converting it to commands.
- **Prefer small steps.** Test each pipe segment on `head` output.
- **Log as you go.** Anything not captured in `results/` or `logs/` is easy to lose.


