# Git & github commands documentation

---
# 1. What is Git?

**Git** is a distributed version control system used to track changes in a project.

It allows you to:

- Save different versions of your work
- See what changed
- Create separate branches for features
- Undo mistakes
- Collaborate with other developers
- Connect your local project to GitHub

### Git vs GitHub

| Git | GitHub |
|---|---|
| Software installed on your computer | Online platform |
| Tracks project history | Hosts Git repositories |
| Works locally | Used for sharing/collaboration |
| Uses Git commands | Provides pull requests, issues, etc. |

---

# 2. Git Configuration

These commands are normally used when setting up Git for the first time.

## `git --version`

Checks whether Git is installed.

```bash
git --version
```

Example:

```text
git version 2.51.0
```

---

## `git config`

Used to configure Git settings.

### Set your username

```bash
git config --global user.name "Your Name"
```

### Set your email

```bash
git config --global user.email "you@example.com"
```

### View your configuration

```bash
git config --list
```

### Check a specific setting

```bash
git config user.name
git config user.email
```

> `--global` means the setting applies to all repositories on your computer.

---

# 3. Creating or Downloading a Repository

## `git init`

Creates a new Git repository in the current folder.

```bash
git init
```

Example:

```bash
mkdir student-project
cd student-project
git init
```

Git creates a hidden `.git` directory that stores the repository's history and configuration.

---

## `git clone`

Downloads an existing repository from GitHub or another Git server.

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/user/student-project.git
```

Then enter the project:

```bash
cd student-project
```

> Use `git clone` when the repository already exists online. Use `git init` when starting a new local project.

---

# 4. Checking the Repository

## `git status`

Shows the current state of your repository.

```bash
git status
```

It tells you:

- Current branch
- Modified files
- Untracked files
- Staged files
- Whether your branch is ahead or behind the remote

> **Tip:** When you don't know what to do next, run `git status`.

---

## `git diff`

Shows changes that have not been staged.

```bash
git diff
```

Example:

```bash
git diff index.html
```

---

## `git diff --staged`

Shows changes that are already staged.

```bash
git diff --staged
```

This is useful before committing to check exactly what will be included.

---

# 5. Understanding the Git Workflow

Git commonly follows this process:

```text
Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
  git commit
       ↓
Local Repository
       ↓
   git push
       ↓
Remote Repository (GitHub)
```

For example:

```bash
# 1. Make changes

# 2. Check them
git status

# 3. Stage them
git add .

# 4. Save them
git commit -m "Add login page"

# 5. Upload them
git push
```

---

# 6. Adding Changes

## `git add`

Moves changes to the staging area.

### Add one file

```bash
git add index.html
```

### Add multiple files

```bash
git add index.html style.css script.js
```

### Add all changes

```bash
git add .
```

> `git add .` stages changes in the current directory.

---

## `git add -A`

Stages all changes in the repository, including additions, modifications, and deletions.

```bash
git add -A
```

For most normal projects, `git add .` is convenient, while `git add -A` is useful when you specifically want everything staged.

---

# 7. Saving Changes

## `git commit`

Creates a permanent snapshot of staged changes.

```bash
git commit -m "Add login page"
```

`-m` means **message**.

A good commit message describes what changed.

```bash
git commit -m "Fix student login validation"
```

---

## `git commit -am`

Stages modified/deleted tracked files and commits them.

```bash
git commit -am "Update homepage"
```

> It does **not** include new untracked files. New files must be added first with `git add`.

---

## `git commit --amend`

Modifies the most recent commit.

For example, if you forgot to include a file:

```bash
git add missing-file.html
git commit --amend
```

To change only the commit message:

```bash
git commit --amend -m "Correct commit message"
```

> Be careful when amending commits that have already been pushed and shared with others.

---