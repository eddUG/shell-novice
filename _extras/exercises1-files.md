---
layout: page
title: "Practice: Files & Navigation (AG1000G Mini)"
---

These warm-ups build muscle memory for paths, safe file ops, and project hygiene.  
Assume you’re at the lesson root (e.g., `ag1000g-mini/`) with `data/`, `results/`, `scripts/`, and `logs/`.

> ## Task 1 — Where am I?
>
> Print your working directory and list its contents.
>
> ~~~
> pwd
> ls -lah
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Output varies; you should see the lesson root and folders like `data/`, `results/`, `scripts/`, `logs/`.
> {: .solution}
{: .challenge}

> ## Task 2 — Create project subfolders
>
> Create (if missing) `results/`, `scripts/`, and `logs/`, then confirm.
>
> ~~~
> mkdir -p results scripts logs
> ls -l
> ~~~
> {: .language-bash}
>
> > ## Solution
> > `results/`, `scripts/`, and `logs/` present and writable.
> {: .solution}
{: .challenge}

> ## Task 3 — Inspect the dataset
>
> List files in `data/` and check sizes.
>
> ~~~
> ls -lh data
> ~~~
> {: .language-bash}
>
> > ## Solution
> > You should see `variants_subset.vcf.gz`, `samples.tsv`, `regions.bed` (small sizes).
> {: .solution}
{: .challenge}

> ## Task 4 — Absolute vs relative paths
>
> 1. `cd` into `data/` and list files.  
> 2. Return to the lesson root using a **relative** path.  
> 3. Jump back to `data/` using an **absolute** path (edit for your system).
>
> ~~~
> cd data
> ls
> cd ..
> cd /absolute/path/to/ag1000g-mini/data    # replace with your actual path
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Relative: `cd ..` from `data/` returns to root. Absolute path depends on your system.
> {: .solution}
{: .challenge}

> ## Task 5 — Safe copy/move/remove
>
> Make a working copy of `samples.tsv`, then move and remove it safely.
>
> ~~~
> cp data/samples.tsv results/samples_copy.tsv
> ls results/
> mv results/samples_copy.tsv results/samples_copy.bak.tsv
> ls results/
> rm results/samples_copy.bak.tsv
> ls results/
> ~~~
> {: .language-bash}
>
> > ## Solution
> > Verify each step with `ls`; end with no extra file left behind.
> {: .solution}
{: .challenge}

> ## Task 6 — Help and file types
>
> - Open help for `grep`.  
> - Ask Unix to guess file content types.
>
> ~~~
> grep --help | head -n 5     # or: man grep
> file data/variants_subset.vcf.gz
> ~~~
> {: .language-bash}
>
> > ## Solution
> > `file` identifies compressed VCF, `grep --help` or `man grep` shows usage.
> {: .solution}
{: .challenge}
