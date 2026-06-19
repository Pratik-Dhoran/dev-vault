Git Quick Revision Notes

⸻

Version Control

Definition:
Version Control System (VCS) tracks file changes over time and allows restoring previous versions.

Why?

* Track history
* Collaborate with team
* Recover mistakes

⸻

Git

Definition:
Git is a distributed version control system used to track and manage source code changes.

Git vs GitHub

Git	GitHub
Tool/Software	Hosting Platform
Works locally	Works online
Tracks code changes	Stores Git repositories

⸻

Repository

Definition:
A repository (repo) is a project folder tracked by Git.

git init

Creates .git directory.

⸻

.git

Hidden folder that stores:

* Commit history
* Branches
* Configuration
* Git metadata

⸻

.gitignore

Used to ignore files/folders from Git tracking.

node_modules/
.env
dist/

⸻

Git Workflow

Working Directory
      ↓ git add
Staging Area
      ↓ git commit
Commit Area (Local Repo)
      ↓ git push
Remote Repository

⸻

Core Concepts

Concept	Meaning
Working Directory	Current files you edit
Staging Area	Changes prepared for commit
Commit	Snapshot of staged changes
Branch	Independent line of development
HEAD	Pointer to current commit

⸻

Basic Commands

Command	Purpose
git init	Create repo
git status	Show current state
git add .	Stage all changes
git commit -m	Create commit
git log	Commit history
git clone	Copy remote repo

⸻

Configuration

git config --global user.name "Pratik"
git config --global user.email "mail@example.com"

⸻

Commits

Definition:
A commit is a snapshot of staged changes stored in Git history.

git commit -m "Added login page"

⸻

Branches

Definition:
A branch is an independent development line.

git branch
git switch branch-name
git switch -c feature-login
git checkout -b feature-login

⸻

Branch Commands

Command	Purpose
git branch	List branches
git branch -m	Rename branch
git branch -d	Delete merged branch
git branch -D	Force delete branch

⸻

HEAD

Definition:
HEAD is a pointer to the currently checked-out commit.

HEAD → main → latest commit

⸻

Detached HEAD

Occurs when HEAD points directly to a commit instead of a branch.

git checkout commitHash

{GPT Added}

Changes made in detached HEAD can be lost if not attached to a branch.

⸻

Git Log

git log
git log --all --oneline --graph

Useful for viewing branch structure and history.

⸻

Restore Commands

Undo Unstaged Changes

git restore file.txt

Unstage File

git restore --staged file.txt

⸻

Reset vs Revert vs Restore

Command	History Changed?	Use Case
restore	No	Undo file changes
reset	Yes	Move HEAD backward
revert	No	Undo using new commit

⸻

Git Reset

git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1

Type	Result
soft	Keep staged changes
mixed	Keep unstaged changes
hard	Delete everything

⸻

Git Revert

Creates a new commit that undoes a previous commit.

git revert commitHash

Safe for shared branches.

⸻

Merge

Combines one branch into another.

git merge feature-branch

⸻

Merge Conflict

Occurs when Git cannot automatically decide which change to keep.

Common Cause

Same file + same lines modified in multiple branches.

⸻

Rebase

Moves commits to a new base commit.

git rebase main

Produces cleaner history.

⸻

Merge vs Rebase

Merge	Rebase
Preserves history	Rewrites history
Creates merge commit	No merge commit
Safer	Cleaner

⸻

Remote Repository

Add Remote

git remote add origin URL

View Remote

git remote -v

Change Remote URL

git remote set-url origin URL

Remove Remote

git remote remove origin

⸻

What is Origin?

Definition:
Origin is the default nickname of the remote repository.

origin → GitHub/GitLab Repo URL

⸻

Push Commands

git push
git push origin main
git push -u origin main

Difference

Command	Meaning
push	Push to linked upstream
push origin main	Explicit push
push -u origin main	Push + set upstream

⸻

Fetch vs Pull

Fetch	Pull
Downloads changes	Downloads + merges
Safe	Can create conflicts

git fetch
git pull

⸻

Clone

Creates a complete local copy of a repository.

git clone URL

⸻

SSH vs Token

SSH	Token
Key-based	Password replacement
Setup once	Used repeatedly
More secure	Easier initially

Test SSH

ssh -T git@gitlab.com

⸻

Git Stash

Temporarily stores uncommitted work.

git stash
git stash pop
git stash list
git stash apply
git stash drop
git stash clear

⸻

Cherry Pick

Copies a specific commit to another branch.

git cherry-pick commitHash

⸻

Reflog (Git Time Machine)

Shows every HEAD movement.

git reflog --oneline --all

Recover lost commits using:

git reset HEAD@{n}

{GPT Added}

Most powerful recovery command in Git.

⸻

Git RM

Remove From Git + Disk

git rm file.txt

Remove From Git Only

git rm --cached file.txt

Recursive Delete

git rm -rf folder

⸻

Common Rescue Scenarios

Wrong Commit Message

git commit --amend

⸻

Forgot File In Last Commit

git add file.txt
git commit --amend --no-edit

⸻

Committed On Master

git branch feature-branch
git reset --hard HEAD~1
git switch feature-branch

⸻

Committed To Wrong Branch

git reset --soft HEAD~1
git stash
git switch correct-branch
git stash pop

OR

git cherry-pick commitHash

⸻

Undo Last 5 Commits

git reset --hard HEAD~5

⸻

Undo Changes To File

git restore file.txt

⸻

Review Keywords

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