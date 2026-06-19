# Git Quick Revision Notes

---

# Version Control

**Definition:**  
Version Control System (VCS) tracks file changes over time and allows restoring previous versions.

### Why?

- Track history
- Collaborate with team
- Recover mistakes

---

# Git

**Definition:**  
Git is a distributed version control system used to track and manage source code changes.

### Git vs GitHub

| Git | GitHub |
|------|--------|
| Tool/Software | Hosting Platform |
| Works locally | Works online |
| Tracks code changes | Stores Git repositories |

---

# Repository

**Definition:**  
A repository (repo) is a project folder tracked by Git.

```bash
git init
```

Creates `.git` directory.

---

# .git

Hidden folder that stores:

- Commit history
- Branches
- Configuration
- Git metadata

---

# .gitignore

Used to ignore files/folders from Git tracking.

```text
node_modules/
.env
dist/
```

---

# Git Workflow

```text
Working Directory
      ↓ git add
Staging Area
      ↓ git commit
Commit Area (Local Repo)
      ↓ git push
Remote Repository
```

---

# Core Concepts

| Concept | Meaning |
|----------|----------|
| Working Directory | Current files you edit |
| Staging Area | Changes prepared for commit |
| Commit | Snapshot of staged changes |
| Branch | Independent line of development |
| HEAD | Pointer to current commit |

---

# Basic Commands

| Command | Purpose |
|----------|----------|
| `git init` | Create repo |
| `git status` | Show current state |
| `git add .` | Stage all changes |
| `git commit -m` | Create commit |
| `git log` | Commit history |
| `git clone` | Copy remote repo |

---

# Configuration

```bash
git config --global user.name "Pratik"
git config --global user.email "mail@example.com"
```

---

# Commits

**Definition:**  
A commit is a snapshot of staged changes stored in Git history.

```bash
git commit -m "Added login page"
```

---

# Branches

**Definition:**  
A branch is an independent development line.

```bash
git branch
git switch branch-name
git switch -c feature-login
git checkout -b feature-login
```

---

# Branch Commands

| Command | Purpose |
|----------|----------|
| `git branch` | List branches |
| `git branch -m` | Rename branch |
| `git branch -d` | Delete merged branch |
| `git branch -D` | Force delete branch |

---

# HEAD

**Definition:**  
HEAD is a pointer to the currently checked-out commit.

```bash
HEAD → main → latest commit
```

---

# Detached HEAD

Occurs when HEAD points directly to a commit instead of a branch.

```bash
git checkout commitHash
```

{GPT Added}

Changes made in detached HEAD can be lost if not attached to a branch.

---

# Git Log

```bash
git log
git log --all --oneline --graph
```

Useful for viewing branch structure and history.

---

# Restore Commands

## Undo Unstaged Changes

```bash
git restore file.txt
```

## Unstage File

```bash
git restore --staged file.txt
```

---

# Reset vs Revert vs Restore

| Command | History Changed? | Use Case |
|----------|-----------------|----------|
| restore | No | Undo file changes |
| reset | Yes | Move HEAD backward |
| revert | No | Undo using new commit |

---

# Git Reset

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
```

| Type | Result |
|--------|--------|
| soft | Keep staged changes |
| mixed | Keep unstaged changes |
| hard | Delete everything |

---

# Git Revert

Creates a new commit that undoes a previous commit.

```bash
git revert commitHash
```

Safe for shared branches.

---

# Merge

Combines one branch into another.

```bash
git merge feature-branch
```

---

# Merge Conflict

Occurs when Git cannot automatically decide which change to keep.

### Common Cause

Same file + same lines modified in multiple branches.

---

# Rebase

Moves commits to a new base commit.

```bash
git rebase main
```

Produces cleaner history.

---

# Merge vs Rebase

| Merge | Rebase |
|---------|---------|
| Preserves history | Rewrites history |
| Creates merge commit | No merge commit |
| Safer | Cleaner |

---

# Remote Repository

## Add Remote

```bash
git remote add origin URL
```

## View Remote

```bash
git remote -v
```

## Change Remote URL

```bash
git remote set-url origin URL
```

## Remove Remote

```bash
git remote remove origin
```

---

# What is Origin?

**Definition:**  
Origin is the default nickname of the remote repository.

```text
origin → GitHub/GitLab Repo URL
```

---

# Push Commands

```bash
git push
git push origin main
git push -u origin main
```

### Difference

| Command | Meaning |
|----------|----------|
| push | Push to linked upstream |
| push origin main | Explicit push |
| push -u origin main | Push + set upstream |

---

# Fetch vs Pull

| Fetch | Pull |
|---------|---------|
| Downloads changes | Downloads + merges |
| Safe | Can create conflicts |

```bash
git fetch
git pull
```

---

# Clone

Creates a complete local copy of a repository.

```bash
git clone URL
```

---

# SSH vs Token

| SSH | Token |
|------|------|
| Key-based | Password replacement |
| Setup once | Used repeatedly |
| More secure | Easier initially |

### Test SSH

```bash
ssh -T git@gitlab.com
```

---

# Git Stash

Temporarily stores uncommitted work.

```bash
git stash
git stash pop
git stash list
git stash apply
git stash drop
git stash clear
```

---

# Cherry Pick

Copies a specific commit to another branch.

```bash
git cherry-pick commitHash
```

---

# Reflog (Git Time Machine)

Shows every HEAD movement.

```bash
git reflog --oneline --all
```

Recover lost commits using:

```bash
git reset HEAD@{n}
```

{GPT Added}

Most powerful recovery command in Git.

---

# Git RM

## Remove From Git + Disk

```bash
git rm file.txt
```

## Remove From Git Only

```bash
git rm --cached file.txt
```

## Recursive Delete

```bash
git rm -rf folder
```

---

# Common Rescue Scenarios

## Wrong Commit Message

```bash
git commit --amend
```

---

## Forgot File In Last Commit

```bash
git add file.txt
git commit --amend --no-edit
```

---

## Committed On Master

```bash
git branch feature-branch
git reset --hard HEAD~1
git switch feature-branch
```

---

## Committed To Wrong Branch

```bash
git reset --soft HEAD~1
git stash
git switch correct-branch
git stash pop
```

OR

```bash
git cherry-pick commitHash
```

---

## Undo Last 5 Commits

```bash
git reset --hard HEAD~5
```

---

## Undo Changes To File

```bash
git restore file.txt
```

---

# Review Keywords

```text
Git = Version Control System
Repository = Tracked Project
Commit = Snapshot
Branch = Independent Development Line
HEAD = Current Commit Pointer
Merge = Combine Branches
Rebase = Move Commit Base
Origin = Remote Alias
Fetch = Download
Pull = Download + Merge
Push = Upload Commits
Stash = Temporary Storage
Cherry-Pick = Copy Commit
Reflog = Recovery History
```
