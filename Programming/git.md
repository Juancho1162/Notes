---
id: git
aliases: []
tags: []
---

### Basic GIT commands
- **git init** - initializes a new git repository
- **git status** - shows the status of the repository
- **git checkout -b new_branch_name** - creates a new branch and switches to it
- **git add file_name** - adds a file to the staging area
- **git commit -m "commit message"** - commits the changes in the staging area
- **git add .** - adds all files to the staging area
- **git diff** - shows the differences between the working directory and the staging area
- **git diff --staged** - shows the differences between the staging area and the repository
- **git log** - shows the commit history
- **git log --oneline** - shows the commit history in one line
- **git branch** - shows the branches in the repository
- **git branch branch_name** - creates a new branch
- **git checkout branch_name** - switches to a branch
- **git merge branch_name** - merges a branch into the current branch
- **git branch -d branch_name** - deletes a branch
- **git rebase branch_name** - rebases the current branch onto another branch, replaying the commits on top of the other branch

### Git workflow
##### New branch workflow 
- 1. Create a new branch (git checkout -b new_branch_name)
- 2. Make changes to the code (git add file_name, git commit -m "commit message")
- 3. Merge the changes into the main branch (git checkout main, git merge new_branch_name)
- 4. Delete the branch (git branch -d new_branch_name)

##### 2 parallel branches workflow (branch_1, branch_2) (rebase)
- 1. Create a new branch (git checkout -b branch_1)
- 2. Make changes to the code (git add file_name, git commit -m "commit message")
- 3. Create a new branch (git checkout -b branch_2)
- 4. Make changes to the code (git add file_name, git commit -m "commit message")
- 5. Switch to branch_1 (git checkout branch_1)
- 6. Rebase branch_1 onto branch_2 (git rebase branch_2)
- 7. Merge the changes into the main branch (git checkout main, git merge branch_1)
- 8. Delete the branches (git branch -d branch_1, git branch -d branch_2)


#### Commit messages
- **feat:** - a new feature
- **fix:** - a bug fix
- **docs:** - changes to documentation
- **style:** - formatting, missing semi colons, etc; no code change
- **refactor:** - refactoring production code
- **test:** - adding tests, refactoring test; no production code change
- **chore:** - updating build tasks, package manager configs, etc; no production code change

#### Branching
- **main** - the main branch
- **feat/new_feature** - a new feature branch
- **fix/new_bug** - a bug fix branch



