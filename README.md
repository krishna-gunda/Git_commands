# 🧠 Git & GitHub Commands Guide for Beginners

> A practical, beginner-friendly reference for students, freshers, and developers working on software, machine learning, MLOps, and open-source projects.

![Git](https://img.shields.io/badge/Git-2.x-orange?logo=git) ![GitHub](https://img.shields.io/badge/GitHub-Beginner--Friendly-blue?logo=github) ![License](https://img.shields.io/badge/License-MIT-green)

---

## 📌 Table of Contents

- [What is Git?](#-what-is-git)
- [What is GitHub?](#-what-is-github)
- [Setup: Installing Git](#️-setup-installing-git)
- [Core Commands Reference](#-core-commands-reference)
  - [git init](#1-git-init)
  - [git clone](#2-git-clone)
  - [git status](#3-git-status)
  - [git add](#4-git-add)
  - [git commit -m](#5-git-commit--m)
  - [git push origin main](#6-git-push-origin-main)
  - [git pull](#7-git-pull)
  - [git branch](#8-git-branch)
  - [git checkout -b](#9-git-checkout--b)
  - [git checkout main](#10-git-checkout-main)
  - [git log](#11-git-log)
  - [git diff](#12-git-diff)
  - [git stash](#13-git-stash)
  - [git merge](#14-git-merge)
  - [git remote -v](#15-git-remote--v)
- [Git Workflow Diagram](#-git-workflow-diagram)
- [Daily Git Workflow Used by Real Developers](#-daily-git-workflow-used-by-real-developers)
- [Common Mistakes Beginners Make](#-common-mistakes-beginners-make)
- [Best Practices](#-best-practices)
- [Cheat Sheet](#-cheat-sheet)

---

## 🔍 What is Git?

**Git** is a free, open-source **version control system** that tracks changes in your code over time. Think of it like a "save history" for your project — you can go back to any previous version at any time.

- Created by **Linus Torvalds** in 2005
- Works **locally** on your machine (no internet needed)
- Used by virtually every professional developer and data scientist

---

## 🐙 What is GitHub?

**GitHub** is a cloud-based platform that hosts your Git repositories online. It lets you:

- 🗂️ Store and share your code publicly or privately
- 🤝 Collaborate with teammates on the same project
- 🔄 Contribute to open-source projects
- 🚀 Deploy projects and showcase your portfolio

> **Analogy:** Git is like Microsoft Word's "Track Changes" feature. GitHub is like Google Drive — where you store and share those Word documents online.

---

## ⚙️ Setup: Installing Git

```bash
# Ubuntu / Debian (Linux)
sudo apt update
sudo apt install git

# Verify installation
git --version
```

```bash
# Configure your identity (one-time setup)
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"

# Verify configuration
git config --list
```

---

## 📚 Core Commands Reference

---

### 1. `git init`

#### 📖 What it does
Initializes a **brand new Git repository** in your current folder. This creates a hidden `.git` folder that Git uses to track everything.

#### 🤔 Why developers use it
When starting a new project from scratch, you use `git init` to tell Git: *"Start tracking this folder."*

#### 🌍 Real-world use case
You just started a new ML project and want to track your Jupyter notebooks and model scripts.

#### 💻 Example

```bash
mkdir my-ml-project
cd my-ml-project
git init
```

**Output:**
```
Initialized empty Git repository in /home/user/my-ml-project/.git/
```

#### ⚠️ Important Notes
- Only run this **once** per project — in the root folder
- Do **not** run `git init` inside a folder that's already a Git repo

---

### 2. `git clone`

#### 📖 What it does
Downloads (copies) a **complete remote repository** from GitHub to your local machine, including all files, history, and branches.

#### 🤔 Why developers use it
To get a copy of an existing project — either your own or someone else's — so you can work on it locally.

#### 🌍 Real-world use case
You want to contribute to a popular open-source ML library like `scikit-learn`, so you clone the repo first.

#### 💻 Example

```bash
# Clone a GitHub repository
git clone https://github.com/username/repository-name.git

# Clone into a specific folder name
git clone https://github.com/username/repo.git my-folder-name

# Navigate into the cloned project
cd repository-name
```

#### ⚠️ Important Notes
- Cloning automatically sets up the `origin` remote connection
- You don't need to run `git init` after cloning — it's already a Git repo

---

### 3. `git status`

#### 📖 What it does
Shows the **current state of your working directory** — which files are new, modified, deleted, or ready to be committed.

#### 🤔 Why developers use it
It's your go-to command to see *what's changed* before you commit anything. Think of it as checking your to-do list.

#### 🌍 Real-world use case
Before committing, you run `git status` to make sure you're only including the right files.

#### 💻 Example

```bash
git status
```

**Output:**
```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)

        modified:   train.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        model_v2.pkl
```

#### ⚠️ Important Notes
- **Red** = changes not yet staged
- **Green** = changes staged and ready to commit
- Run this command often — it's the safest habit in Git

---

### 4. `git add`

#### 📖 What it does
**Stages** (prepares) files for the next commit. It tells Git: *"Include these changes in my next save."*

#### 🤔 Why developers use it
Git doesn't automatically save everything — you choose exactly which changes to include in each commit.

#### 🌍 Real-world use case
You updated three files but only want to commit changes to two of them right now.

#### 💻 Example

```bash
# Stage a single file
git add train.py

# Stage multiple files
git add train.py config.yaml

# Stage ALL changed files at once
git add .

# Stage a whole folder
git add src/
```

#### ⚠️ Important Notes
- `git add .` stages **everything** in the current folder — use carefully
- Staging is not committing — you still need to run `git commit` after this
- Use `git status` after `git add` to verify what's staged

---

### 5. `git commit -m`

#### 📖 What it does
**Saves a snapshot** of your staged changes to the local repository history, with a descriptive message explaining what changed.

#### 🤔 Why developers use it
Every commit is like a checkpoint — a point in time you can return to if something breaks.

#### 🌍 Real-world use case
After finishing a feature or fixing a bug, you commit your work with a clear message so teammates (and your future self) understand what changed.

#### 💻 Example

```bash
# Basic commit with a message
git commit -m "Add data preprocessing pipeline"

# Stage all modified tracked files AND commit in one step
git commit -am "Fix bug in model evaluation script"
```

#### ⚠️ Important Notes
- Write **meaningful messages** — `"fixed stuff"` is bad; `"Fix NaN handling in preprocessing step"` is good
- Keep messages **short but descriptive** (under 72 characters)
- A commit only saves to your **local** repo — use `git push` to send it to GitHub

---

### 6. `git push origin main`

#### 📖 What it does
**Uploads** your local commits to the remote repository on GitHub. `origin` is the nickname for your GitHub repo, and `main` is the branch name.

#### 🤔 Why developers use it
To share your code with teammates or back it up to GitHub in the cloud.

#### 🌍 Real-world use case
After finishing your day's work on a data pipeline, you push your commits so your team can see and review your changes.

#### 💻 Example

```bash
# Push local commits to the main branch on GitHub
git push origin main

# Push a specific branch
git push origin feature/data-cleaning

# First-time push (set upstream tracking)
git push -u origin main
```

#### ⚠️ Important Notes
- You must have committed changes **before** pushing
- If your teammate pushed changes since your last pull, Git may reject your push — run `git pull` first
- `origin` = the default name Git gives to the remote GitHub URL

---

### 7. `git pull`

#### 📖 What it does
**Downloads and merges** the latest changes from the remote GitHub repository into your current local branch.

#### 🤔 Why developers use it
To stay in sync with your team — especially before starting new work each day.

#### 🌍 Real-world use case
Your teammate merged a hotfix overnight. You run `git pull` in the morning to get those updates before writing new code.

#### 💻 Example

```bash
# Pull latest changes from the main branch
git pull origin main

# Pull from the currently tracked branch (shorthand)
git pull
```

#### ⚠️ Important Notes
- `git pull` = `git fetch` + `git merge` combined
- Always pull before starting new work to avoid **merge conflicts**
- If you have uncommitted local changes, Git may ask you to commit or stash them first

---

### 8. `git branch`

#### 📖 What it does
**Lists, creates, or deletes branches** in your repository. Branches let you work on separate features without affecting the main codebase.

#### 🤔 Why developers use it
To isolate new features, bug fixes, or experiments from the stable `main` branch.

#### 🌍 Real-world use case
Your team has one branch for `feature/user-auth`, another for `bugfix/login-crash`, and a clean `main` for production.

#### 💻 Example

```bash
# List all local branches (* marks current branch)
git branch

# List all branches including remote
git branch -a

# Create a new branch
git branch feature/model-training

# Delete a branch (after merging)
git branch -d feature/model-training

# Force delete an unmerged branch
git branch -D feature/model-training
```

#### ⚠️ Important Notes
- Creating a branch does NOT switch to it — use `git checkout -b` to create AND switch
- Never work directly on `main` — always use feature branches
- Branch names use lowercase with hyphens by convention: `feature/add-login`

---

### 9. `git checkout -b`

#### 📖 What it does
**Creates a new branch AND immediately switches** to it in a single command.

#### 🤔 Why developers use it
It's the fastest way to start working on a new feature or fix.

#### 🌍 Real-world use case
You're assigned a new ML task. You create a new branch for it so your changes don't affect the main codebase.

#### 💻 Example

```bash
# Create and switch to a new branch
git checkout -b feature/add-lstm-model

# Create a new branch based on another branch
git checkout -b hotfix/data-leak origin/main
```

**Output:**
```
Switched to a new branch 'feature/add-lstm-model'
```

#### ⚠️ Important Notes
- Modern Git (2.23+) also supports `git switch -c branch-name` as an alternative
- Always create feature branches from an up-to-date `main`
- Verify your current branch anytime with `git branch`

---

### 10. `git checkout main`

#### 📖 What it does
**Switches back** to the `main` branch from whichever branch you're currently on.

#### 🤔 Why developers use it
To return to the stable codebase after finishing (or pausing) feature work.

#### 🌍 Real-world use case
You've finished your feature branch and want to switch back to `main` to merge or start a new task.

#### 💻 Example

```bash
# Switch to main branch
git checkout main

# Switch to any other existing branch
git checkout develop

# Modern alternative (Git 2.23+)
git switch main
```

#### ⚠️ Important Notes
- If you have **unsaved changes**, Git will warn you — commit or stash them first
- After switching, always run `git pull` to get the latest `main`
- If your default branch is `master` instead of `main`, replace accordingly

---

### 11. `git log`

#### 📖 What it does
Shows the **complete history of commits** in the current branch — who made each change, when, and what the commit message was.

#### 🤔 Why developers use it
To audit changes, understand the project history, or find a specific commit to roll back to.

#### 🌍 Real-world use case
A model suddenly broke. You check `git log` to find the commit that introduced the regression.

#### 💻 Example

```bash
# Full commit history
git log

# Condensed one-line format (great for quick scans)
git log --oneline

# Visual branch graph
git log --oneline --graph --all

# Show last 5 commits only
git log -5

# Filter commits by author
git log --author="Ravi"
```

**Output (oneline):**
```
3a2f1bc Add dropout to LSTM layers
9e4d7aa Fix data normalization bug
c120bfe Initial model architecture
```

#### ⚠️ Important Notes
- Press `q` to exit the log view in the terminal
- Each commit has a unique **hash** (like `3a2f1bc`) — you need this to revert or reset
- Use `git log --oneline` daily; full `git log` is verbose

---

### 12. `git diff`

#### 📖 What it does
Shows the **exact line-by-line differences** between your current changes and the last committed version.

#### 🤔 Why developers use it
To review exactly what changed before committing — so you don't accidentally commit debug code or API keys.

#### 🌍 Real-world use case
Before committing, you use `git diff` to double-check that you only changed what you intended to.

#### 💻 Example

```bash
# Show unstaged changes
git diff

# Show staged changes (already added with git add)
git diff --staged

# Compare two branches
git diff main feature/new-model

# Compare a specific file
git diff train.py
```

**Output:**
```diff
- learning_rate = 0.01
+ learning_rate = 0.001
```

#### ⚠️ Important Notes
- **Red lines (-)** = removed content
- **Green lines (+)** = added content
- `git diff` shows unstaged changes; `git diff --staged` shows staged changes

---

### 13. `git stash`

#### 📖 What it does
**Temporarily saves** your uncommitted work (staged and unstaged) so you can switch branches without committing unfinished code.

#### 🤔 Why developers use it
When you're mid-task and urgently need to switch branches (e.g., a hotfix), stash lets you park your work safely.

#### 🌍 Real-world use case
You're halfway through writing a feature when a production bug is reported. You stash your work, fix the bug, then come back and restore your stash.

#### 💻 Example

```bash
# Stash your current changes
git stash

# Stash with a descriptive label
git stash save "WIP: LSTM training loop"

# List all stashed entries
git stash list

# Restore the most recent stash (and keep it in stash list)
git stash apply

# Restore AND remove from stash list
git stash pop

# Drop a specific stash
git stash drop stash@{0}
```

#### ⚠️ Important Notes
- Stashes are **local** — they are not pushed to GitHub
- `git stash pop` = `apply` + `drop` (most common usage)
- Untracked (new) files are NOT stashed by default — use `git stash -u` to include them

---

### 14. `git merge`

#### 📖 What it does
**Combines the history** of one branch into another. Typically used to bring a completed feature branch into `main`.

#### 🤔 Why developers use it
To integrate finished work from a feature branch back into the main codebase.

#### 🌍 Real-world use case
Your `feature/data-augmentation` branch is reviewed and approved. You merge it into `main` to release the feature.

#### 💻 Example

```bash
# Step 1: Switch to the branch you want to merge INTO
git checkout main

# Step 2: Merge the feature branch into main
git merge feature/data-augmentation

# Merge with a commit message even if fast-forward is possible
git merge --no-ff feature/data-augmentation
```

**Output:**
```
Updating 9e4d7aa..3a2f1bc
Fast-forward
 data_loader.py | 15 +++++++++++++++
 1 file changed, 15 insertions(+)
```

#### ⚠️ Important Notes
- **Merge conflicts** happen when both branches edited the same line — Git will ask you to resolve them manually
- Use `--no-ff` (no fast-forward) to always create a merge commit — this preserves branch history
- After merging, you can safely delete the feature branch with `git branch -d`

---

### 15. `git remote -v`

#### 📖 What it does
**Lists all remote connections** (like GitHub) linked to your local repository, showing their names and URLs.

#### 🤔 Why developers use it
To verify your repo is connected to the correct GitHub URL — especially after cloning or setting up a new project.

#### 🌍 Real-world use case
You're not sure if your local repo is pointing to the right GitHub repository. You run `git remote -v` to confirm.

#### 💻 Example

```bash
# List all remote connections
git remote -v

# Add a new remote
git remote add origin https://github.com/username/my-project.git

# Change remote URL (e.g., switch from HTTPS to SSH)
git remote set-url origin git@github.com:username/my-project.git

# Remove a remote
git remote remove origin
```

**Output:**
```
origin  https://github.com/username/my-project.git (fetch)
origin  https://github.com/username/my-project.git (push)
```

#### ⚠️ Important Notes
- `origin` is just a default **nickname** for your remote — you can rename it
- If `git remote -v` returns nothing, your local repo isn't connected to GitHub yet
- Use SSH URL (`git@github.com:...`) instead of HTTPS for passwordless authentication

---

## 🗺️ Git Workflow Diagram

```
Your Computer (Local)                   GitHub (Remote)
─────────────────────────────────────────────────────────────

  [Working Directory]
        │
        │  git add
        ▼
  [Staging Area]
        │
        │  git commit -m "message"
        ▼
  [Local Repository]  ──── git push ──────────►  [Remote Repo]
        ▲                                               │
        │                                               │
        └────────────── git pull ───────────────────────┘

─────────────────────────────────────────────────────────────

Branch Workflow:

  main ─────●─────────────────────────────●────► (production)
              \                           /
               ● git checkout -b         ● git merge
                \                       /
  feature ───────●──────●──────●───────►  (feature work)

─────────────────────────────────────────────────────────────
```

---

## 🔄 Daily Git Workflow Used by Real Developers

This is the workflow professional developers (and ML engineers) follow every single day:

```bash
# ── START OF DAY ──────────────────────────────────────────

# Step 1: Switch to main and get the latest code from GitHub
git checkout main
git pull origin main

# Step 2: Create a new branch for today's task
git checkout -b feature/improve-model-accuracy

# ── DURING WORK ───────────────────────────────────────────

# Step 3: Work on your code...
# (edit files, write functions, train models, etc.)

# Step 4: Check what changed
git status
git diff

# Step 5: Stage and commit your work
git add .
git commit -m "Tune hyperparameters: increase epochs to 50"

# (Repeat Steps 3–5 as many times as needed)

# ── END OF DAY / FEATURE COMPLETE ─────────────────────────

# Step 6: Push your branch to GitHub
git push origin feature/improve-model-accuracy

# Step 7: Open a Pull Request on GitHub for code review
# (done via the GitHub website)

# Step 8: After review & approval, merge into main
git checkout main
git merge feature/improve-model-accuracy

# Step 9: Push merged main to GitHub
git push origin main

# Step 10: Clean up the feature branch
git branch -d feature/improve-model-accuracy

# ──────────────────────────────────────────────────────────
```

---

## ❌ Common Mistakes Beginners Make

### 1. Working directly on `main`
Never commit directly to `main`. Always create a feature branch. One bad push can break everyone's work.

```bash
# ❌ Don't do this
git checkout main
# ... make changes ...
git commit -m "added stuff"
git push origin main

# ✅ Do this instead
git checkout -b feature/my-task
# ... make changes ...
git commit -m "Add feature: describe what you did"
git push origin feature/my-task
```

### 2. Not pulling before pushing
Always pull the latest changes before pushing to avoid rejection errors.

```bash
# ✅ Always pull first
git pull origin main
git push origin main
```

### 3. Vague commit messages
A commit history of `"fix"`, `"update"`, `"changes"` is useless to your future self and your team.

```bash
# ❌ Bad
git commit -m "fix"

# ✅ Good
git commit -m "Fix NaN value crash in preprocessing.py line 42"
```

### 4. Staging everything blindly with `git add .`
Always check `git status` and `git diff` before `git add .` to avoid committing debug code, passwords, or large binary files.

### 5. Committing sensitive information
Never commit API keys, passwords, or `.env` files. Add them to `.gitignore` immediately.

```bash
# Create a .gitignore file
echo ".env" >> .gitignore
echo "*.pkl" >> .gitignore
echo "__pycache__/" >> .gitignore
git add .gitignore
git commit -m "Add .gitignore to exclude secrets and cache files"
```

### 6. Panicking during merge conflicts
Merge conflicts are normal. Read them calmly, choose the correct version, then stage and commit the resolved file.

---

## ✅ Best Practices

### Commit Often, Push Regularly
Small, frequent commits are easier to review and debug than one giant commit at the end of the week.

### Write Meaningful Commit Messages
Follow this format for professional commits:

```
<type>: <short description>

Types: feat, fix, docs, style, refactor, test, chore

Examples:
  feat: Add BERT-based text classifier
  fix: Handle empty DataFrame in data loader
  docs: Update README with setup instructions
  refactor: Simplify training loop logic
```

### Always Use `.gitignore`
Exclude files that should never be committed:

```gitignore
# Python
__pycache__/
*.pyc
*.pyo
.env
venv/
.venv/

# Jupyter
.ipynb_checkpoints/

# ML artifacts
*.pkl
*.h5
*.pt
models/checkpoints/

# OS files
.DS_Store
Thumbs.db

# Credentials
*.env
secrets.yaml
config/credentials.json
```

### Use Branches for Everything
One branch per feature, bug fix, or experiment. This keeps `main` always in a deployable state.

### Review Before You Commit
Run `git status` and `git diff --staged` before every commit to catch mistakes early.

### Pull Requests Over Direct Merges
On team projects, always use Pull Requests (PRs) on GitHub so teammates can review your code before it reaches `main`.

---

## 📋 Cheat Sheet

| Command | What It Does | When to Use It |
|---|---|---|
| `git init` | Initialize a new local repo | Starting a brand new project |
| `git clone <url>` | Copy a remote repo locally | Getting an existing project from GitHub |
| `git status` | See changed/staged files | Constantly — before every add/commit |
| `git add .` | Stage all changes | Before committing |
| `git add <file>` | Stage a specific file | When committing partial changes |
| `git commit -m "msg"` | Save a snapshot with a message | After staging your changes |
| `git push origin main` | Upload commits to GitHub | After committing, to share your work |
| `git pull` | Download + merge latest from GitHub | Start of day, before pushing |
| `git branch` | List all branches | To see where you are |
| `git checkout -b <name>` | Create + switch to new branch | Starting a new feature or fix |
| `git checkout main` | Switch to main branch | After finishing feature work |
| `git log --oneline` | View compact commit history | Reviewing past changes |
| `git diff` | Show unstaged line-by-line changes | Before staging, to review edits |
| `git diff --staged` | Show staged line-by-line changes | After `git add`, before committing |
| `git stash` | Temporarily save uncommitted work | When switching branches mid-task |
| `git stash pop` | Restore stashed work | Coming back to a paused task |
| `git merge <branch>` | Merge a branch into current branch | Integrating finished feature into main |
| `git remote -v` | Show remote GitHub connections | Verifying your repo's remote URL |

---

## 🚀 Quick Setup Checklist (New Project)

```bash
# 1. Create your project folder
mkdir my-project && cd my-project

# 2. Initialize Git
git init

# 3. Create your files
touch README.md .gitignore

# 4. Stage and commit
git add .
git commit -m "Initial commit"

# 5. Connect to GitHub (create repo on GitHub first)
git remote add origin https://github.com/yourusername/my-project.git

# 6. Push to GitHub
git push -u origin main
```

---

## 📎 Additional Resources

- 📘 [Official Git Documentation](https://git-scm.com/doc)
- 🐙 [GitHub Docs](https://docs.github.com)
- 🎮 [Learn Git Branching (Interactive)](https://learngitbranching.js.org/)
- 📺 [GitHub Skills (Free Courses)](https://skills.github.com/)

---

<div align="center">

**Made with ❤️ for students, freshers, and developers learning Git**

*Version control is a superpower — use it on every project, no matter how small.*

</div>
