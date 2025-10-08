---
title: "Capstone: mini-analysis pipeline"
instruction: 10
exercises: 50
questions:
- "How can the Unix shell support a small but realistic bioinformatics workflow?"
- "How can we organize, inspect, summarize, and automate a small genomics project using just the shell?"
- "How do we combine pipes, filters, loops, and scripts into a reproducible workflow?"
objectives:
- "Motivate shell use through a realistic genomics story."
- "Outline the pipeline we’ll assemble and the skills required."
keypoints:
- "We will use only core Unix tools (no bioinformatics software installs)."
- "You’ll build a small reproducible workflow, to be rerun on new data with minimal effort."
- "Results, scripts and logs will document exactly what you did."
---

### Mariam’s Pipeline: A Typical Bioinformatics Problem

**Mariam Okello**, an entomologist working on malaria vectors, has just returned from a season of field collections across East and West Africa. She sequenced dozens of *Anopheles* samples and now has a folder of **VCF files** plus **sample metadata** describing species, populations, and sites. Her task is to summarize variation across chromosomes, check quality filters and produce a few region-based counts for a short report due next week.

If Mariam tries to do this by hand—opening each file, copying counts into a spreadsheet and repeating steps for every region, she’ll waste hours of attention and introduce mistakes. If each per-file summary takes just 30 seconds and she has 300 files, that’s **2.5+ hours of mindless work**, not counting fixes and re-runs. With the **Unix shell**, Mariam can instead **script the pipeline once**, run it for **all files** (and future data), and spend her time interpreting results and writing.

This mini project has been structured around five short sessions to show how Mariam assembles this pipeline. She will:

- use the command shell to **run small tools** on text-based genomics files,
- **chain commands** together to build concise, testable workflows,
- and use **loops** to automate the repetitive step of feeding many files and regions through the same commands.

As a bonus, once she has put the pipeline together, she can **reuse it** whenever new sequencing data arrive; changing only input paths or parameters.

### In order to achieve her task, Mariam needs to know how to:

- **navigate to a file/directory** (`pwd`, `ls`, `cd`);
- **create a file/directory** and keep tidy project structure (`mkdir`, redirection, `cp`, `mv`, `rm`);
- **check the length of a file** and peek safely (`wc`, `head`, `tail`, `less`);
- **chain commands together** with **pipes** and **redirection** (`|`, `>`, `>>`);
- **retrieve a set of files** using globs and simple find/filters (`*.vcf.gz`, `find`, `grep`);
- **iterate over files** and regions with **loops** (`for`, `while read …`);
- **run a shell script** containing her pipeline (`chmod +x`, `./run_all.sh`) and capture logs (`tee`).

Over the capstone, you’ll step into Mariam’s role. You’ll organize a small anopheles genomics project, inspect and summarize variants and metadata with core shell tools, automate the repetitive parts, and finish with a single script that reproduces your analysis end-to-end.


> ## Data bundle
> - **Download:** [Anopheles data bundle]({{ page.root }}/data/ag-bundle.zip)
> - Unzip into `data/` so you have:
>   - `data/variants_subset.vcf.gz`
>   - `data/samples.tsv`
>   - `data/regions.bed`
{: .callout}

Jump to:
- **Day 1:** [Setup & Orientation]({{page.root}}/_extras/99-capstone-day1.md) {% link {{page.root}}/_extras/99-capstone-day1.md %}

Jump to: [Day 1](#day-1-setup--orientation) > [Day 2](#day-2-metadata-summaries) > [Day 3](#day-3-variant-summaries) > [Day 4](#day-4-windows--genotype-snapshot) > [Day 5](#day-5-automate-package-reflect)

> ## Tips for staying on course
> - **Plan first, then type.** Write your pipeline in plain language before converting it to commands.
> - **Prefer small steps.** Test each pipe segment on `head` output.
> - **Log as you go.** Anything not captured in `results/` or `logs/` is easy to lose.
{: .callout}

