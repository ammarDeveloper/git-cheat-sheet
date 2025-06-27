# Git Command Cheatsheet

## Setup & Configuration
```bash
# Install Git
# Windows: Download from git-scm.com
# macOS: brew install git
# Linux: sudo apt-get install git

# Configuration
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global core.editor "code --wait"
git config --list
```

## Repository Basics
```bash
# Create & Clone
git init                    # Initialize a new repository
git clone <url>             # Clone an existing repository

# Status & Information
git status                  # Show working tree status
git log                     # Show commit history
git log --oneline           # Compact history view
git log --graph             # Graphical history view
git diff                    # Show changes between commits, commit and working tree, etc.
git diff --staged           # Show changes in the staging area
```

## Basic Workflow
```bash
# Stage & Commit
git add <file>              # Add file to staging area
git add .                   # Add all files to staging area
git commit -m "message"     # Commit changes with message
git commit -am "message"    # Add tracked files and commit in one command
```

## Branching & Merging
```bash
# Branches
git branch                  # List branches
git branch <branch-name>    # Create new branch
git checkout <branch-name>  # Switch to a branch
git checkout -b <branch>    # Create and switch to new branch
git branch -d <branch>      # Delete branch

# Merging
git merge <branch>          # Merge branch into current branch
```

## Remote Repositories
```bash
# Remote Management
git remote -v                       # List remotes
git remote add <name> <url>         # Add a remote
git remote remove <name>            # Remove a remote

# Push & Pull
git fetch <remote>                  # Fetch from remote
git pull <remote> <branch>          # Pull from remote
git push <remote> <branch>          # Push to remote
git push -u origin <branch>         # Push and set upstream
```

## Reset Commands
```bash
# Reset
git reset                           # Reset staging area (unstage all files)
git reset <file>                    # Unstage a specific file
git reset --soft HEAD~1             # Undo last commit, keep changes staged
git reset HEAD~1                    # Undo last commit, keep changes unstaged
git reset --hard HEAD~1             # Undo last commit, discard changes
git reset b1b9566cb7fecc47d47c614d00a4c73b2fcfb142   # Reset to specific commit (keep changes)
git reset --hard 139c749c93749a8d3b85eda7abf9c797d868ce04  # Reset to specific commit (discard changes)
```

## Stash Commands
```bash
# Stashing
git stash                           # Stash changes
git stash list                      # List stashed changes
git stash push -m "this file1" file1.txt   # Stash specific file with message
git stash pop                       # Apply and remove most recent stash
git stash apply                     # Apply most recent stash (keep in stash)
git stash apply stash@{1}           # Apply specific stash
git stash drop                      # Remove most recent stash
git stash clear                     # Remove all stashes
```

## Tagging
```bash
# Tags
git tag                             # List tags
git tag <tag-name>                  # Create lightweight tag
git tag -a <tag-name> -m "message"  # Create annotated tag
git push origin <tag-name>          # Push tag to remote
```

## Advanced Commands
```bash
# Cherry-pick & Rebase
git cherry-pick <commit>            # Apply commit from another branch
git rebase <branch>                 # Reapply commits on top of another branch
git rebase -i HEAD~3                # Interactive rebase for last 3 commits

# Searching & Investigation
git grep "pattern"                  # Search working directory for pattern
git blame <file>                    # Show who changed what in a file
git bisect start                    # Start binary search for bugs
git reflog                          # Show reference logs
```

## Maintenance & Recovery
```bash
# Cleanup & Verification
git gc                              # Garbage collection
git fsck                            # Check repository integrity
git prune                           # Remove unreachable objects

# Recovery
git checkout -- <file>              # Discard changes in working directory
git restore <file>                  # Discard changes (modern syntax)
git clean -fd                       # Remove untracked files and directories
```

## How to revert the changes back to certain commit with out modifying the commit history
```bash
# 1. Reset your working directory to the desired commit state
git reset --hard 67875fc9a99afbef94998075cbf66bec826fba28

# 2. Reset back to HEAD but keep the changes staged
git reset --soft HEAD@{1}

# 3. Create a commit with a descriptive message
git commit -m "revert: Manually revert changes to commit 67875fc9
```

|> Note: It modifies the CHANGELOG.md file. Its better to create a new branch and copy paste the changes from the reverted branch 
