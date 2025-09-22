# Capturing Full Staged Changes with Git

This short note explains how to save all staged changes (not just file names) into a file for review, sharing, or later application.

## Motivation

By default, git status only shows which files are staged. To see the actual changes that will be committed, developers need to use git diff against the index. Redirecting this output allows saving a full patch for inspection or transfer.

## Core Command

To output all staged diffs into a patch file:

```bash
git diff --staged --no-color > staged.patch
```

Options to consider:

- `--no-color` → prevents ANSI color codes in the file.
- `--binary` → includes binary changes, useful for assets:

```bash
git diff --staged --no-color --binary > staged.patch
```

## Variants

- Unstaged changes only

```bash
git diff --no-color > unstaged.patch
```

- Everything vs HEAD (staged + unstaged)

```bash
git diff HEAD --no-color > working.patch
```

## Use Cases

- Share a patch with teammates without pushing a branch.
- Apply changes elsewhere using git apply staged.patch.
- Archive diffs for code reviews or audits.
