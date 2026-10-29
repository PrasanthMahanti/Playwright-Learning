New-Item Phase1\notes\day04.md -ItemType File

# Day 4: Git & GitHub

## 1. Git vs GitHub
| | Git | GitHub |
|---|---|---|
| What it is | A program on my computer | A website that stores my project online |
| Job | Saves versions (save points) | Backup, sharing, teamwork |
| Internet | Not needed | Needed |
| Works alone? | Yes | No, it needs Git |

- Camera 📷 = Git (takes the photos). Album 🖼️ = GitHub (stores and shares them).
- Saving a file in VS Code does NOT put it on GitHub. It needs add, commit, push.

## 2. The 3 places a file passes through, Chapter 2: Where does a file travel?
Working folder --git add--> Staging area (the box) --git commit--> Repository (history) --git push--> GitHub

- Working folder = files I edit in VS Code.
- Box = I choose what goes into the next save point.
- Repository = all save points, in the hidden .git folder (never edit it).
- A commit = snapshot + who + when + message + unique ID.

## 3. File states
| State | Meaning | How it happens |
|---|---|---|
| Untracked | New file Git is not watching | I just created it |
| Staged | In the box | git add . |
| Committed (tracked) | Saved in history | git commit |
| Modified | Tracked file I edited after the last commit | I edit it again |

Working tree clean = nothing changed since the last commit.

## 4. Steps I practiced (from the top folder, never run git init twice) Chapter 3: Create a new file and save it
| Step | Command | What it does |
|---|---|---|
| 1 | git --version, git config --global --list | Check Git, my name and email |
| 2 | git status | See where things stand |
| 3 | New-Item file -ItemType File, then Set-Content file "text" | Create a file and write in it |
| 4 | git add . | Put changed files in the box |
| 5 | git commit -m "message" | Seal the box with a label |
| 6 | git push | Send my commits to GitHub |
| 7 | Add-Content file "text" | Edit a saved file (it becomes modified) |
| 8 | git diff | See what changed (not in the box yet) |
| 9 | git diff --staged | Check what is in the box before committing |
| 10 | git log --oneline, git show | Read my history (press q to leave) |

## Chapter 5: Read my history
- git log --oneline = list of all commits, newest first.
- git show = details of the latest commit (who, when, what changed).
- If I see : or (END), press q.


## 5. Differences to remember
| Compare | Difference |
|---|---|
| Set-Content vs Add-Content | Set-Content replaces the whole file. Add-Content adds a line at the end and keeps the old text. |
| git status vs git diff | status shows WHICH files changed. diff shows WHAT changed inside them. |
| git diff vs git diff --staged | diff = changes not in the box yet. diff --staged = changes in the box. |
| Untracked vs Modified | Untracked = new file Git never saw. Modified = a known file I edited. |
| git add vs git commit | add puts files in the box. commit seals the box into history. |
| git commit vs git push | commit saves on my computer. push uploads to GitHub. |
| git log vs git show | log lists all commits. show gives details of one commit. |
| + vs - in git diff | + is an added line. - is a removed line. |

## 6. Reading git status
| I see | Meaning | Next |
|---|---|---|
| Untracked files | New file, not watched | git add . |
| Changes not staged for commit | Edited, not in the box | git add . |
| Changes to be committed | In the box | git commit -m "..." |
| Branch is ahead of origin/main | Committed, not pushed | git push |
| working tree clean | Nothing to save | Relax |

## 7. My daily cycle
edit file --> git status --> git add . --> git diff --staged --> git commit -m "..." --> git push
(Like packing a parcel: write, check the table, put in the box, look inside, seal with a label, post.)

## 8. Remember
- Save the file (Ctrl+S) before git status. Git cannot see unsaved edits.
- Run Git commands from the top folder, not from Phase1.
- git diff --staged = last check before sealing, because a commit is permanent.
- If a screen shows : or (END), press q.
- Commit small, commit daily.

## 9. My own words (fill in)
- Learned:
- Confused:
- Built:
- Explained (Git vs GitHub in 2 lines): git is a version control tool
                                        github is the onlilne platform to store the work