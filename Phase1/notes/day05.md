# Day 005: Git & GitHub

## Three areas
- **Working directory**: your files on disk
- **Staging area**: changes chosen for the next commit
- **Repository**: saved commit history

File states: Untracked → Modified → Staged → Committed

## git status
- Shows which files are changed, staged, or untracked
- Read-only, never changes anything
- `git status -s` gives the short format
- Run it before and after `add` and `commit`

## git diff
- Shows the exact line changes (`status` shows files, `diff` shows lines)

| Command | Compares |
|---|---|
| `git diff` | Working dir vs staging (unstaged changes) |
| `git diff --staged` | Staging vs last commit (what will be committed) |
| `git diff HEAD` | Working dir vs last commit (everything) |

- `-` = removed line, `+` = added line
- `git diff` shows nothing if everything is already staged
- `git diff` ignores untracked files

## git log --oneline
- Compact history: short hash + message, one line per commit
- `-5` shows the last 5, `--graph` shows branches, `--all` shows all branches
- **HEAD** = pointer to the commit/branch you are on
- Flag is `--oneline` (not `--online`)
- Press `q` to exit the pager

## .gitignore
- A file listing what Git should never track
- Used for secrets (`.env`), dependencies (`node_modules/`), build output, and OS junk (`Thumbs.db`)
- Patterns: `*.log` (any log), `folder/` (a folder), `!file` (exception), `#` (comment)
- Only works on **untracked** files. For already-tracked files, use `git rm --cached <file>`
- Commit it early

## Good commit messages
1. Imperative mood: "Add", not "Added"
2. Subject around 50 characters, no period
3. Explain what and why, not how
4. One logical change per commit
5. Add a body only when the reason isn't obvious

Test: "If applied, this commit will ___"

| Bad | Good |
|---|---|
| `some random change` | `Add Day 005 notes on git status and diff` |
| `fix` | `Fix crash when username is empty` |

## Practical done today
- Commit 1: `Add .gitignore for env files, dependencies, and test output`
- Commit 2: `Add Day 005 notes on git status, diff, log, and .gitignore`
- `git push` uploads commits to GitHub
- "Ahead by 2 commits" = only on laptop. "Up to date" = laptop and GitHub match

## Self-check answers
1. `git diff` = unstaged changes. `git diff --staged` = staged changes.
2. It shows nothing when the changes are already staged.
3. `.gitignore` only affects untracked files, and a committed file is already tracked.
4. Split into: `Fix crash when username is empty` and `Add email field to signup form`
5. HEAD is a pointer to the commit/branch you're currently on.

Save this as `Phase1/notes/day05.md`. If that file already has your own notes, you can add this below them.

When you're ready, tell me what `git status` said after `git push`, and we'll do the branch step.