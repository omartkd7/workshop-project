# GitHub Commands A to Z — Complete Reference Guide

> A complete cheat sheet covering Git & GitHub commands from A to Z.

---

## Table of Contents
- [A — Add, Amend](#a)
- [B — Branch, Blame](#b)
- [C — Clone, Commit, Checkout, Cherry-pick](#c)
- [D — Diff, Delete](#d)
- [E — Extra remote operations](#e)
- [F — Fetch, Fork](#f)
- [G — Git init, Git config](#g)
- [H — Help, History](#h)
- [I — Init, Ignore](#i)
- [J — Jump (checkout)](#j)
- [L — Log, List branches](#l)
- [M — Merge, Move](#m)
- [N — New branch](#n)
- [O — Origin, Open PR](#o)
- [P — Pull, Push, Pull Request](#p)
- [R — Rebase, Reset, Revert, Remote](#r)
- [S — Status, Stash, Submodule](#s)
- [T — Tag](#t)
- [U — Undo, Update](#u)
- [V — View log graph](#v)
- [W — Worktree](#w)

---

## A

### Add — Stage files for commit
```bash
git add <file>          # Stage a specific file
git add .               # Stage all changes in current directory
git add -p              # Interactively stage chunks (patch mode)
```

### Amend — Modify the last commit
```bash
git commit --amend                  # Edit last commit message
git commit --amend --no-edit        # Add staged changes to last commit without changing message
```

---

## B

### Branch — Manage branches
```bash
git branch                          # List local branches
git branch -a                       # List local + remote branches
git branch <name>                   # Create a new branch
git branch -d <name>                # Delete a branch (safe)
git branch -D <name>                # Force delete a branch
git branch -m <old> <new>           # Rename a branch
```

### Blame — See who changed each line
```bash
git blame <file>                    # Show who last changed each line
git blame -L 10,20 <file>           # Blame lines 10–20 only
```

---

## C

### Clone — Copy a repository
```bash
git clone <url>                     # Clone a repo into a new folder
git clone <url> <folder>            # Clone into a specific folder
git clone --depth 1 <url>           # Shallow clone (latest snapshot only)
```

### Commit — Save staged changes
```bash
git commit -m "message"             # Commit with inline message
git commit -am "message"            # Stage tracked files + commit in one step
git commit --allow-empty -m "msg"   # Create empty commit (useful for triggering CI)
```

### Checkout — Switch branches or restore files
```bash
git checkout <branch>               # Switch to a branch
git checkout -b <branch>            # Create and switch to new branch
git checkout -- <file>              # Discard changes in working directory
git checkout <commit> -- <file>     # Restore file from a specific commit
```

### Cherry-pick — Apply a specific commit
```bash
git cherry-pick <commit-hash>       # Apply a specific commit onto current branch
git cherry-pick <hash1>..<hash2>    # Apply a range of commits
```

---

## D

### Diff — Show changes
```bash
git diff                            # Unstaged changes
git diff --staged                   # Staged (cached) changes
git diff <branch1>..<branch2>       # Difference between two branches
git diff <commit> <commit>          # Difference between two commits
```

### Delete — Remove files
```bash
git rm <file>                       # Remove file and stage deletion
git rm --cached <file>              # Untrack file without deleting it from disk
```

---

## E

### Extra Remote Operations
```bash
git remote prune origin             # Remove stale remote-tracking branches
git fetch --prune                   # Fetch + prune in one step
git push origin --delete <branch>   # Delete a remote branch
```

---

## F

### Fetch — Download from remote (no merge)
```bash
git fetch                           # Fetch all remotes
git fetch origin                    # Fetch from origin
git fetch origin <branch>           # Fetch a specific branch
```

### Fork (GitHub CLI)
```bash
gh repo fork <owner>/<repo>         # Fork a repo on GitHub
gh repo fork <owner>/<repo> --clone # Fork and clone locally
```

---

## G

### Git Init — Start a new repository
```bash
git init                            # Initialize a repo in current folder
git init <folder>                   # Initialize a repo in a new folder
```

### Git Config — Set preferences
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor "code --wait"   # Set VS Code as editor
git config --list                               # View all config settings
```

---

## H

### Help
```bash
git help <command>                  # Open man page for a command
git <command> --help
```

### History — View commit history
```bash
git log                             # Full commit history
git log --oneline                   # Compact one-line format
git log --oneline --graph --all     # Visual branch graph
git log -n 5                        # Last 5 commits
git log --author="name"             # Filter by author
git log --since="2024-01-01"        # Filter by date
```

---

## I

### Init — See G (Git Init)

### Ignore — .gitignore patterns
```bash
# Create a .gitignore file and add patterns:
echo "node_modules/" >> .gitignore
echo ".env"          >> .gitignore
echo "*.log"         >> .gitignore

git check-ignore -v <file>          # Debug why a file is ignored
```

---

## J

### Jump (Checkout / Switch to a commit)
```bash
git checkout <commit-hash>          # Detach HEAD to a specific commit
git switch -                        # Switch back to previous branch
```

---

## L

### Log — See H (History)

### List branches
```bash
git branch -a                       # All branches (local + remote)
git branch --merged                 # Branches merged into current
git branch --no-merged              # Branches NOT yet merged
```

---

## M

### Merge — Combine branches
```bash
git merge <branch>                  # Merge branch into current
git merge --no-ff <branch>          # Merge with a merge commit (no fast-forward)
git merge --abort                   # Abort a merge in progress
git merge --squash <branch>         # Squash all commits into one before merging
```

### Move — Rename a file
```bash
git mv <old-file> <new-file>        # Rename/move file and stage the change
```

---

## N

### New Branch
```bash
git checkout -b <branch>            # Old way: create + switch
git switch -c <branch>              # New way: create + switch
git switch -c <branch> origin/<b>   # Create tracking a remote branch
```

---

## O

### Origin — Manage remotes
```bash
git remote -v                       # View remotes
git remote add origin <url>         # Add remote named "origin"
git remote set-url origin <url>     # Change the URL of origin
git remote rename origin upstream   # Rename remote
git remote remove <name>            # Remove remote
```

### Open Pull Request (GitHub CLI)
```bash
gh pr create                        # Interactive PR creation
gh pr create --title "Title" --body "Description"
gh pr create --base main --head feature-branch
```

---

## P

### Pull — Fetch + merge from remote
```bash
git pull                            # Pull current branch from origin
git pull origin main                # Pull main branch from origin
git pull --rebase                   # Pull and rebase instead of merge
```

### Push — Upload to remote
```bash
git push                            # Push current branch
git push -u origin <branch>         # Push and set upstream tracking
git push --force-with-lease         # Force push (safer than --force)
git push origin --tags              # Push all tags
```

### Pull Request (GitHub CLI)
```bash
gh pr list                          # List open PRs
gh pr view <number>                 # View a PR
gh pr checkout <number>             # Check out a PR locally
gh pr merge <number>                # Merge a PR
gh pr close <number>                # Close a PR
gh pr review --approve <number>     # Approve a PR
gh pr review --request-changes <number> -b "Feedback"
```

---

## R

### Rebase — Replay commits on another base
```bash
git rebase main                     # Rebase current branch onto main
git rebase -i HEAD~3                # Interactive rebase: last 3 commits
git rebase --abort                  # Abort a rebase
git rebase --continue               # Continue after resolving conflicts
```

### Reset — Undo commits
```bash
git reset --soft HEAD~1             # Undo commit, keep changes staged
git reset --mixed HEAD~1            # Undo commit, keep changes unstaged (default)
git reset --hard HEAD~1             # Undo commit and DISCARD all changes
```

### Revert — Safely undo a commit (creates new commit)
```bash
git revert <commit-hash>            # Revert a specific commit
git revert HEAD                     # Revert the latest commit
```

### Remote — See O (Origin)

---

## S

### Status — See what has changed
```bash
git status                          # Full status
git status -s                       # Short/compact status
```

### Stash — Temporarily save work
```bash
git stash                           # Stash current changes
git stash push -m "description"     # Stash with a name
git stash list                      # List all stashes
git stash pop                       # Apply latest stash and remove it
git stash apply stash@{2}           # Apply a specific stash
git stash drop stash@{0}            # Delete a specific stash
git stash clear                     # Delete all stashes
```

### Submodule — Embed another repo
```bash
git submodule add <url> <path>      # Add a submodule
git submodule update --init         # Initialize submodules after clone
git submodule update --remote       # Update submodules to latest
```

---

## T

### Tag — Mark releases
```bash
git tag                             # List all tags
git tag v1.0.0                      # Create a lightweight tag
git tag -a v1.0.0 -m "Release 1.0" # Create annotated tag
git push origin v1.0.0              # Push a specific tag
git push origin --tags              # Push all tags
git tag -d v1.0.0                   # Delete a local tag
git push origin --delete v1.0.0    # Delete a remote tag
```

---

## U

### Undo — Various ways to undo
```bash
git restore <file>                  # Discard unstaged changes (modern)
git restore --staged <file>         # Unstage a file
git revert <hash>                   # Undo commit (safe, keeps history)
git reset --soft HEAD~1             # Undo commit, keep staged
git reset --hard HEAD~1             # Undo commit, lose all changes
```

### Update — Sync with remote
```bash
git fetch --all --prune             # Update all remote references
git pull --rebase origin main       # Rebase local work on top of remote
```

---

## V

### View — Log graph
```bash
git log --oneline --graph --all --decorate
# Tip: add this alias to your config:
git config --global alias.graph "log --oneline --graph --all --decorate"
git graph                           # Use after alias is set
```

---

## W

### Worktree — Multiple working directories
```bash
git worktree add <path> <branch>    # Check out branch in new folder
git worktree list                   # List all worktrees
git worktree remove <path>          # Remove a worktree
```

---

## GitHub CLI (gh) Quick Reference

```bash
# Auth
gh auth login                       # Log in to GitHub
gh auth status                      # Check login status

# Repos
gh repo create <name>               # Create a new repo
gh repo clone <owner>/<repo>        # Clone a repo
gh repo view                        # View current repo in browser

# Issues
gh issue list                       # List issues
gh issue create                     # Create an issue
gh issue view <number>              # View an issue
gh issue close <number>             # Close an issue

# Actions / CI
gh run list                         # List workflow runs
gh run view <id>                    # View a specific run
gh run watch                        # Watch a run in real-time
```

---

## Common Workflows

### Start a new feature
```bash
git switch -c feature/my-feature    # Create feature branch
# ... make changes ...
git add .
git commit -m "feat: add my feature"
git push -u origin feature/my-feature
gh pr create --title "Add my feature" --body "Description here"
```

### Sync fork with upstream
```bash
git remote add upstream <original-repo-url>
git fetch upstream
git merge upstream/main
git push origin main
```

### Fix a merge conflict
```bash
git merge <branch>                  # Conflict occurs
# Edit conflicting files, then:
git add <resolved-file>
git commit                          # Complete the merge
```

### Squash commits before PR
```bash
git rebase -i HEAD~<N>              # Replace N with number of commits
# Mark all but first as "squash" or "s", save and exit
git push --force-with-lease
```

---

## Export This as PDF

To convert this README to PDF:

1. **VS Code**: Install "Markdown PDF" extension → right-click the file → `Markdown PDF: Export (pdf)`
2. **Command line**: `npm install -g md-to-pdf` then `md-to-pdf README.md`
3. **GitHub**: View this file on GitHub → `Ctrl+P` → Print → Save as PDF
4. **Pandoc**: `pandoc README.md -o github-commands.pdf`

---

*Last updated: 2026-04-09 | Reference covers Git 2.x and GitHub CLI (gh) 2.x*
