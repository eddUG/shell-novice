---
layout: page
title: "Practice: FASTQ Essentials (Self-contained)"
---

We’ll create a tiny FASTQ and practice safe text processing. No external downloads.

> ## Task 0 — Create a tiny FASTQ
>
> Make `data/reads.fastq` with two reads.
>
> ~~~
> cat > data/reads.fastq << 'EOF'
> @read1
> ACGTACGTACGTACGTACGT
> +
> FFFFFFFFFFFFFFFFFFFF
> @read2
> TTTTCCCCAAAAGGGGTTTT
> +
> FFFFAAAALLLLJJJJFFFF
> EOF
> ls -lh data/reads.fastq
> ~~~
> {: .language-bash}
>
> > ## Solution
> > File exists and is small (≈100 bytes).
> {: .solution}
{: .challenge}

> ## Task 1 — Count reads and bases
>
> - Reads: lines starting with `@` (record headers).  
> - Bases: length of sequence lines (2nd line of each 4-line block).
>
> ~~~
> grep -c '^@' data/reads.fastq
> awk 'NR%4==2{bases+=length($0)} END{print bases}' data/reads.fastq
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Reads: `2`; bases: `40` total.
> {: .solution}
{: .challenge}

> ## Task 2 — Extract sequences only
>
> Write sequences (no headers/quals) to `results/reads.seqs.txt`.
>
> ~~~
> awk 'NR%4==2' data/reads.fastq > results/reads.seqs.txt
> cat results/reads.seqs.txt
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Two lines of sequences (one per read).
> {: .solution}
{: .challenge}

> ## Task 3 — GC content (simple)
>
> Compute fraction of `G` or `C` across all sequences.
>
> ~~~
> awk 'NR%4==2{seq=$0; total+=length(seq); for(i=1;i<=length(seq);i++){c=substr(seq,i,1); if(c=="G"||c=="C") gc++}} END{printf "GC=%.2f%%\n",(gc/total)*100}' data/reads.fastq
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Prints a percentage (value depends on sequences).
> {: .solution}
{: .challenge}

> ## Task 4 — Quality line length check
>
> Verify each quality line length equals its sequence length.
>
> ~~~
> awk 'NR%4==2{L=length($0)} NR%4==0{if(length($0)!=L) err++} END{if(err) print "Mismatch"; else print "OK"}' data/reads.fastq
> ~~~
> {: .language-bash}
>
> > ## Solution
> > `OK` if lengths match.
> {: .solution}
{: .challenge}
