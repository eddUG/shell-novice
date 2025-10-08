---
layout: page
title: "Practice: More Loops (Batching & Checks)"
---

Use `data/` files to practice robust loops that create tidy outputs in `results/`.

> ## Task 1 — Loop over inputs (practice shards)
>
> Pretend there are several VCF shards. Loop over the same file twice to learn the pattern and produce per-“shard” counts.
>
> ~~~
> for shard in data/variants_subset.vcf.gz data/variants_subset.vcf.gz; do
>   base=$(basename "$shard" .vcf.gz)
>   zgrep -c -v '^#' "$shard" > "results/${base}.rows.txt"
> done
> ls results/*rows.txt
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Two small `*.rows.txt` files with identical counts (practice artifact).
> {: .solution}
{: .challenge}

> ## Task 2 — Per-chromosome splits in a loop
>
> For each chromosome, write its first 3 variant rows to a file.
>
> ~~~
> for chrom in $(zgrep -v '^#' data/variants_subset.vcf.gz | cut -f1 | sort -u); do
>   out="results/first3_${chrom}.tsv"
>   zgrep -v '^#' data/variants_subset.vcf.gz | awk -v c="$chrom" '$1==c' | head -n 3 > "$out"
>   echo "Wrote $out"
> done
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Files like `results/first3_2L.tsv`, `results/first3_X.tsv`.
> {: .solution}
{: .challenge}

> ## Task 3 — Region PASS counts (from BED)
>
> Read regions from `data/regions.bed`, make one count file per region; skip empty results gracefully.
>
> ~~~
> while read chrom start end name; do
>   out="results/${name}.count.txt"
>   n=$(zgrep -v '^#' data/variants_subset.vcf.gz \
>       | awk -v c="$chrom" -v s="$start" -v e="$end" '($1==c && $2>=s && $2<=e && $7=="PASS")' \
>       | wc -l)
>   echo "$n" > "$out"
>   echo "Region $name: $n"
> done < data/regions.bed
> ~~~
> {: .language-bash}
>
> > ## Solution
> > One `*.count.txt` per region with a single integer inside.
> {: .solution}
{: .challenge}

> ## Task 4 — A simple driver loop
>
> Tie Tasks 1–3 into one executable script and run it.
>
> ~~~
> cat > scripts/run_loops.sh << 'EOF'
> #!/usr/bin/env bash
> set -euo pipefail
> mkdir -p results
> 
> # per-file rows (practice)
> for shard in data/variants_subset.vcf.gz data/variants_subset.vcf.gz; do
>   base=$(basename "$shard" .vcf.gz)
>   zgrep -c -v '^#' "$shard" > "results/${base}.rows.txt"
> done
> 
> # first 3 per chrom
> for chrom in $(zgrep -v '^#' data/variants_subset.vcf.gz | cut -f1 | sort -u); do
>   out="results/first3_${chrom}.tsv"
>   zgrep -v '^#' data/variants_subset.vcf.gz | awk -v c="$chrom" '$1==c' | head -n 3 > "$out"
> done
> 
> # region PASS counts
> while read chrom start end name; do
>   out="results/${name}.count.txt"
>   zgrep -v '^#' data/variants_subset.vcf.gz \
>     | awk -v c="$chrom" -v s="$start" -v e="$end" '($1==c && $2>=s && $2<=e && $7=="PASS")' \
>     | wc -l > "$out"
> done < data/regions.bed
> echo "Done."
> EOF
> 
> chmod +x scripts/run_loops.sh
> ./scripts/run_loops.sh
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Running the script creates several files under `results/` and exits with "Done."
> {: .solution}
{: .challenge}
