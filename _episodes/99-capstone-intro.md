---
title: "Capstone — Mini-analysis Pipeline"
questions:
- "How can the Unix shell support a small but realistic bioinformatics workflow?"
- "How can we organize, inspect, summarize, and automate a small genomics project using just the shell?"
- "How do we combine pipes, filters, loops, and scripts into a reproducible workflow?"
objectives:
- "Work through five question-driven sessions to build a complete pipeline."
- "Capture results and logs; finish with a single script."
keypoints:
- "We will use only core Unix tools (no bioinformatics software installs)."
- "You’ll build a small, reproducible workflow over five one-hour sessions."
- "Results, scripts, and logs will document exactly what you did."
---

> ## Data bundle
> - **Download:** [Anopheles data bundle]({% link data/ag-bundle.zip %})
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

## Tips for staying question-driven
- **Plan first, then type.** Write your pipeline in plain language before converting it to commands.
- **Prefer small steps.** Test each pipe segment on `head` output.
- **Log as you go.** Anything not captured in `results/` or `logs/` is easy to lose.


