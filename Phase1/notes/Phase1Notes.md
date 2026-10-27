# Days 1-3 Summary: Setup, Git and Terminal

## Big idea
- Learn → Build → Push → Explain. Every topic follows this loop.
- An automation engineer writes code that runs tests automatically. This reduces manual errors and saves time.
- Tools: VS Code is where I write. Node.js runs my code. Git saves versions. GitHub keeps the online copy.

## Git (save points)
- git add .  → choose what to save
- git commit -m "message"  → save it with a label
- git push  → send it to GitHub
- git status  → see what changed
- First time only: git init, git remote add origin URL, git push -u origin main
- Errors I fixed: "No configured push destination" (no remote saved) and "Repository not found" (typo in the URL, fixed with git remote set-url origin).

## Terminal commands
- pwd  → where am I
- ls  → list files and folders (the Mode column: d = folder, a = normal file)
- cd folder / cd ..  → go in / go up one level
- mkdir  → create a folder
- New-Item file -ItemType File  → create a file
- cat  → show what is inside a file

        cat Phase1\notes\day02.md
        cat Phase1\notes\day01.md, Phase1\notes\day02.md
        Get-Content Phase1\notes\day02.md -TotalCount 3
        Get-Content Phase1\notes\day02.md -Tail 3
- cp  → copy
- mv  → move, or rename
- rm  → delete permanently (no Recycle Bin), so run pwd and ls first
- clear  → wipe the screen
- Tab completes names. Up arrow brings back old commands.
- node hello.js  → Node reads my file and runs it

## Paths
- Absolute path: full address from the drive, e.g. D:\qspiders\bible\playwright. Works from anywhere.
- Relative path: address from where I am, e.g. notes\day02.md.
- . means here, .. means one level up.

## Things to remember
- Git does not save empty folders, so I put a small file inside each one.
- Quotes always come in pairs. If I see >>, a quote is still open: press Ctrl+C.
- Run Git commands from the top folder (Playwright-Learning), not from inside Phase1.
- Commit every day, even if it is small.

mv "D:\qspiders\bible\playwright\Playwright-Learning\Phase1Notes.md" Phase1\notes\
PS D:\qspiders\bible\playwright\Playwright-Learning> 