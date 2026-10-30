# Day 006 Notes: Branches, Merge, Restore

Read each theory block, then run its practice right away. Do the parts in order.

## Before you start
```powershell  , 
git status
```
You want a clean tree and "up to date with 'origin/main'". If it says "ahead", run `git push` first.

---

## Part 1: Branches

**Theory**
- A **branch** is a movable pointer to a commit. Creating one is instant and copies no files.
- Use branches so you can work without touching stable `main`.
- **HEAD** points to the branch you're on, and new commits move that branch forward.
- `git switch -c <name>` creates a branch and switches to it. `git branch` lists branches, and `*` marks the current one.

**Practice**
```powershell
git branch
git switch -c feature/notes
git branch
```
You should see `* feature/notes` now, with `main` listed below it.

Now make a commit **on the branch**. Create the file and commit it:
```powershell
New-Item Phase1/notes/day06.md -ItemType File
notepad Phase1/notes/day06.md
```
Type a few lines (for example "Day 6: branches"), save, close, then:
```powershell
git add Phase1/notes/day06.md
git commit -m "Add Day 006 notes on branches and merging"
git --no-pager log --oneline -3
```
You should see `HEAD -> feature/notes` on the top commit, with `main` one commit behind.

---

## Part 2: Restore (undo before commit)

**Theory**
- `git restore <file>` **discards** unstaged edits. This is destructive, and the edits can't be recovered.
- `git restore --staged <file>` **unstages** a file but keeps your edits.
- Run `git diff <file>` first to see what you would lose.
- It only works on changes that haven't been committed yet.

**Practice** (still on `feature/notes`)
```powershell
notepad Phase1/notes/day06.md
```
Add a line saying `THIS IS A MISTAKE`, save, close, then:
```powershell
git diff Phase1/notes/day06.md
git restore Phase1/notes/day06.md
git status
```
The mistake line should be gone, and the status should say clean.

Now try unstaging. Add the mistake line again, then:
```powershell
git add Phase1/notes/day06.md
git status
git restore --staged Phase1/notes/day06.md
git status
```
The first status shows the file under "Changes to be committed". The second shows it under "not staged". Your edit is still in the file, so finish with `git restore Phase1/notes/day06.md` to remove it.

---

## Part 3: Merge

**Theory**
- You always merge **into the branch you're standing on**. Switch to `main` first, then merge the feature branch.
- **Fast-forward**: `main` had no new commits, so Git just moves the pointer forward (no merge commit).
- **Conflict**: both branches changed the same lines, so you fix the file by hand, `git add` it, and commit. `git merge --abort` cancels the merge.
- After merging, delete the finished branch with `git branch -d`.

**Practice**
```powershell
git switch main
git merge feature/notes
git --no-pager log --oneline -3
```
The output should say `Fast-forward`, and `main` now includes your Day 006 commit.

Then publish and clean up:
```powershell
git push
git branch -d feature/notes
git branch
git status
```
Only `* main` should be left, and the status should say up to date.

---

## Quick reference

| Command | Meaning |
|---|---|
| `git branch` | List branches |
| `git switch -c x` | Create and switch to branch x |
| `git switch main` | Go back to main |
| `git merge x` | Merge x into the current branch |
| `git branch -d x` | Delete a merged branch |
| `git restore f` | Discard unstaged edits (destructive) |
| `git restore --staged f` | Unstage a file |

## Self-check
1. What does HEAD point to?
2. Which branch must you be on before running `git merge feature/notes`?
3. What is the difference between `git restore f` and `git restore --staged f`?

Go at your own pace. If anything errors out, paste the message and I'll help from there.