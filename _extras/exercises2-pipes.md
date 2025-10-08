---
layout: page
title: "Practice: Pipes, Filters & Redirection"
---

Use **only** local files in `data//`. No internet/dependencies.

> ## Task 1 — Sample counts by population
>
> Build a descending table of samples per population from `samples.tsv`.
>
> ~~~
> tail -n +2 data/samples.tsv | cut -f3 | sort | uniq -c | sort -nr \
>   > results/samples_by_population.txt
> head results/samples_by_population.txt
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Lines like `N POP`, highest first.
> {: .solution}
{: .challenge}

> ## Task 2 — Unique country–population pairs
>
> Produce unique pairs and save as TSV.
>
> ~~~
> tail -n +2 data/samples.tsv | cut -f4,3 | sort | uniq \
>   > results/country_population.tsv
> head results/country_population.tsv
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Each line is `country<TAB>population`, no duplicates.
> {: .solution}
{: .challenge}

> ## Task 3 — Count VCF variant rows
>
> Count non-header lines in the VCF.
>
> ~~~
> zgrep -c -v '^#' data/variants_subset.vcf.gz | tee results/variant_count.txt
> ~~~
> {: .language-bash}
>
> > ## Solution
> > A small integer (≈120).
> {: .solution}
{: .challenge}

> ## Task 4 — Variants per chromosome
>
> Build a frequency table by chromosome.
>
> ~~~
> zgrep -v '^#' data/variants_subset.vcf.gz | cut -f1 | sort | uniq -c | sort -nr \
>   > results/variants_by_chrom.txt
> head results/variants_by_chrom.txt
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Counts keyed by chrom names (2L/2R/3L/3R/X).
> {: .solution}
{: .challenge}

> ## Task 5 — FILTER distribution + timestamp
>
> Count `FILTER` values and append the date.
>
> ~~~
> zgrep -v '^#' data/variants_subset.vcf.gz | cut -f7 | sort | uniq -c | sort -nr \
>   > results/filter_counts.txt
> date >> results/filter_counts.txt
> tail -n 3 results/filter_counts.txt
> ~~~
> {: .language-bash}
>
> > ## Solution
> > PASS/LowQual counts + a date at the end.
> {: .solution}
{: .challenge}

> ## Task 6 — Stdout vs stderr
>
> Capture normal output and errors separately.
>
> ~~~
> ls data/variants_subset.vcf.gz data/missing_file 1>results/ls.out 2>results/ls.err
> cat results/ls.out
> cat results/ls.err
> ~~~
> {: .language-bash}
>
> > ## Solution
> > `ls.out` shows the existing file; `ls.err` contains the error message.
> {: .solution}
{: .challenge}

> ## Task 7 — Transform ALT alleles (toy)
>
> Lowercase ALT column (col 5) and show first lines.
>
> ~~~
> zgrep -v '^#' data/variants_subset.vcf.gz | cut -f5 | tr 'A' 'a' | head
> ~~~
> {: .language-bash}
>
> > ## Solution
> > ALT values printed; any `A` becomes `a`.
> {: .solution}
{: .challenge}

> ## Task 8 — One-liner numbers 1..30 (practice)
>
> ~~~
> seq 1 30
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Prints 1 to 30, one per line.
> {: .solution}
{: .challenge}
