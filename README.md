# Git and GitHub Notes

**Name:** Piotr Ozga  
**Date:** 26 November 2025  
**Purpose:** A personal reference to organize and review Git and GitHub knowledge in the future.  
**Contact:** piotr.ozga.bio@outlook.com  
**Description:** This repository contains my personal notes for Git and GitHub. 

## Table of Contents
- [Git vs GitHub](#git-vs-github)
- [How to configure Git and GitHub?](#how-to-configure-git-and-github)
- [Basic commands](#basic-commands)
- [Undoing and Restoring](#undoing-and-restoring)
- [Branching and Merging](#branching-and-merging)
---

# Git vs GitHub
Git is a version control system to track changes in code or files. GitHub, on the other hand, is a cloud platform for hosting your Git repositories.

# How to configure Git and GitHub?
1. The first time you use Git on a new machine, you need to configure it:
```
git config --global user.name "your_username"
git config --global user.email youremail@example.com
git config --list
```
2. Then set up an SSH key - this allows you to push changes to your GitHub account without providing password every time:
```
ls -al ~/.ssh
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
```
3. Add the SSH key to your GitHub account.  
- Go to GitHub -> Settings -> SSH and GPG keys -> New SSH key  
- Paste the generated SSH key into the "key" field

4. Test the connection:
```
ssh -T git@github.com
```

# Basic commands
- Clone a remote repository using SSH:
```
git clone <ssh_url>
```
*Cloning gives you a local copy of the project to work on independently. The clone includes the entire commit history, so you can explore and revert to older versions.*

- Initialize a new local repository:
```
git init 
```
*Initializing creates a new Git repository in your folder. It is a good idea to check if there is already Git repository in your folder to avoid nested repositories (you can use git status for this).*
- Show modified and staged files:
```
git status
```
*If there is no Git repository in your current working directory, Git will display a relevant message.*
- Stage a single file:
```
git add <file_name>
```
- Stage all files:
```
git add .
```
- Stage only tracked files:
```
git add -u
```
- Commit changes:
```
git commit -m "commit message"
```
- Push changes to GitHub:
```
git push origin main
```
- Show differences (working directory vs staging):
```
git diff
```
- Show differences (staging vs last commit):
```
git diff --staged
```
# Undoing and Restoring
- Show commit history:
```
git log
```
*Viewing the log helps track changes and understand the evolution of the project. Each commit has a unique ID you can reference.*
- Display a concise, one-line-per-commit history:
```
git log --oneline
```
- Find the commit ID you want to restore:
```
git checkout <commit_id>
```
- If you want to continue work on that state, create new branch:
```
git checkout -b <new_branch_name>
```
- Restore a single file:
```
git checkout <commit_id> -- <file_name>
```
- Undo the last commit (keep changes staged):
```
git reset --soft HEAD~1
```
- Undo the last commit (discard changes):
```
git reset --hard HEAD~1
```
# Branching and Merging
- Create a new branch:
```
git branch <new_branch_name>
```
*Branches allow you to work on new features without affecting the main codebase. This is essential for testing and experimentation.*
- Create a new branch and switch to it:
```
git checkout -b <new_branch_name>
```
- List all branches:
```
git branch
```
- Switch to a branch:
```
git checkout <new_branch_name> 
```
- Switch to a branch (new syntax):
```
git switch <branch>
```
- Compare branches:
```
git diff main..<new_branch_name>
```
- Merge branches (performed from the branch you want to merge into)
```
git checkout main
git merge <new_branch_name>
```
- Show commits involved in merge conflict:
```
git log --merge
```
*This command helps identify which commits are causing the conflict, making resolution easier. Merge conflicts occur when changes in different branches affect the same part of a file. They must be resolved manually before completing the merge, as Git cannot automatically decide which changes to keep.*
