---
title: "Introducing the Shell (Entomology Edition)"
teaching: 15
exercises: 45
questions:
- "What is the shell?"
- "How can it help me as an entomologist?"
- "How do I access it?"
objectives:
- "Explain what the shell is and why to use it in entomology."
- "Open a shell on Windows/macOS/Linux."
- "Run simple navigation commands: pwd, ls, cd."
keypoints:
- "The shell is a program that runs other programs."
- "It is efficient and reproducible for large entomology datasets."
- "pwd, ls, and cd help you orient and navigate."
---

The **shell** lets you give instructions to your computer by typing commands.
Instead of clicking through folders to open insect trap data, mosquito genome files,
or specimen images, you can issue precise, repeatable instructions.

When you open the shell, you will see a prompt like `$` — the shell's way of saying
*I'm ready for a command.*

> ## Exercise: Where Am I?
>
> Show your current working directory.
> ```bash
> pwd
> ```
> > ## Solution
> > Output will vary, e.g. `/Users/you/entomology-shell-lesson-data`.
{: .challenge}

> ## Exercise: Moving Around
>
> Change into the `sequences` folder, list its files, then return.
> ```bash
> cd sequences
> ls
> cd ..
> ```
> > ## Solution
> > You should see `.fastq` files listed and then return to the lesson root.
{: .challenge}

> ## Callout: Tab Completion & History
>
> Press **Tab** to auto-complete paths and filenames (handy for long species names).
> Use **↑** to repeat commands from history.
{: .callout}

> ## Key Points
>
> - The shell is a program that runs other programs.
> - It is efficient and reproducible for large entomology datasets.
> - `pwd`, `ls`, and `cd` help you orient and navigate.
{: .keypoints}
