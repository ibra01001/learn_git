# Git Learning Session

A walkthrough of basic Git operations: initializing a repo, committing files, removing files, and configuring Git globals.

---

## 1. Initialize the Repository

```bash
git init
```

> Git initialized an empty repository in `/home/brahim/learn_git/.git/`.  
> Note: The default branch is named `master`. Starting with Git 3.0, it will default to `main`. To configure this globally:
> ```bash
> git config --global init.defaultBranch main
> ```

---

## 2. First Commit — Adding `third.txt`

```bash
git add third.txt
git commit -m "adding third.txt"
```

**Result:**
```
[master (root-commit) dc00861] adding third.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 third.txt
```

---

## 3. Second Commit — Adding `fourth.txt`

```bash
touch fourth.txt
git add fourth.txt
git commit -m "adding fourth.txt"
```

**Result:**
```
[master 8a58572] adding fourth.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 fourth.txt
```

---

## 4. Third Commit — Removing `third.txt`

```bash
rm third.txt
git add .        # Note: 'git add.' (without space) is not valid — always use 'git add .'
git commit -m "removing third.txt"
```

**Result:**
```
[master 06aa4b7] removing third.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 third.txt
```

> ⚠️ **Mistake caught:** `git add.` (no space) is not a valid Git command. The correct syntax is `git add .`

---

## 5. Viewing the Commit History

```bash
git log
```

**Output:**
```
commit 06aa4b7cc02d41aa88ae85260138d7a9235aa6ac (HEAD -> master)
Author: REMILI Brahim <mohamedremili5000@gmail.com>
Date:   Fri May 15 17:27:12 2026 +0100
    removing third.txt

commit 8a58572227c4394aa003c7ff6c4323b2b0f8ba00
Author: REMILI Brahim <mohamedremili5000@gmail.com>
Date:   Fri May 15 17:05:10 2026 +0100
    adding fourth.txt

commit dc00861e1c5fef4432fb592b867243a5b3c17e2a
Author: REMILI Brahim <mohamedremili5000@gmail.com>
Date:   Fri May 15 14:34:56 2026 +0100
    adding third.txt
```

---

## 6. Global Git Configuration

```bash
# Set pager to 'cat' so git log doesn't open in a scrollable viewer
git config --global core.pager cat

# List all global config values
git config --global --list
```

**Global config output:**
```
user.name=REMILI Brahim
user.email=mohamedremili5000@gmail.com
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
filter.lfs.clean=git-lfs clean -- %f
core.pager=cat
```

> ℹ️ `git config --global` alone does nothing — you must pair it with a key/value or a flag like `--list`.

---

## Commit History Summary

| # | Commit Hash | Message | Files Changed |
|---|-------------|---------|---------------|
| 1 | `dc00861` | adding third.txt | +third.txt |
| 2 | `8a58572` | adding fourth.txt | +fourth.txt |
| 3 | `06aa4b7` | removing third.txt | -third.txt |

---

## Key Takeaways

- `git init` — initializes a new local repository
- `git add <file>` or `git add .` — stages changes (note the space before `.`)
- `git commit -m "message"` — saves a snapshot with a message
- `git log` — shows the full commit history
- `git config --global` — manages user-level Git settings
