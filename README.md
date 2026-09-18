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

# 8. Viewing Commit History

## `git log`

Shows the commit history.

```bash
git log
```

---

## `git log --oneline`

Shows commits in a shorter format.

```bash
git log --oneline
```

Example:

```text
a82f31c Add login page
72ab921 Create homepage
43cd221 Initial commit
```

---

## `git log --oneline --graph --all`

Displays branches and commits visually.

```bash
git log --oneline --graph --all
```

Example:

```text
* a82f31c Add login
| * 72ab921 Add dashboard
|/
* 43cd221 Initial commit
```

---

## `git show`

Displays information about a specific commit.

```bash
git show <commit-id>
```

Example:

```bash
git show a82f31c
```

To show the latest commit:

```bash
git show HEAD
```

---

# 9. Branches

A **branch** is a separate line of development.

For example:

```text
main
 │
 ├── feature-login
 │
 └── feature-dashboard
```

Branches allow you to work on features without directly changing `main`.

---

## `git branch`

Lists local branches.

```bash
git branch
```

Example:

```text
* main
  feature-login
  feature-dashboard
```

`*` indicates the branch you are currently using.

---

## Create a branch

```bash
git branch feature-login
```

This creates the branch but does not switch to it.

---

## `git switch`

Switches to another branch.

```bash
git switch feature-login
```

---

## Create and switch to a branch

```bash
git switch -c feature-login
```

`-c` means **create**.

---

## `git checkout`

Older Git command that can also switch branches.

```bash
git checkout feature-login
```

Create and switch:

```bash
git checkout -b feature-login
```

Modern Git generally recommends `git switch` for switching branches.

---

# 10. Renaming Branches

## `git branch -M`

Renames the current branch.

```bash
git branch -M main
```

`-M` means forcefully rename the branch.

A common use is changing:

```text
master → main
```

---

# 11. Deleting Branches

## Delete a local branch

```bash
git branch -d feature-login
```

`-d` safely deletes a branch that has been merged.

---

## Force delete a local branch

```bash
git branch -D feature-login
```

`-D` forces deletion even if the branch has unmerged changes.

> Use `-D` carefully.

---

# 12. Remote Repositories

A **remote** is a repository stored somewhere else, usually on GitHub.

## `git remote -v`

Shows connected remote repositories.

```bash
git remote -v
```

Example:

```text
origin  https://github.com/user/project.git (fetch)
origin  https://github.com/user/project.git (push)
```

---

## `git remote add`

Connects your local repository to a remote repository.

```bash
git remote add origin <repository-url>
```

Example:

```bash
git remote add origin https://github.com/user/project.git
```

### What is `origin`?

`origin` is the conventional name for the main remote repository. It is simply a name that points to the remote URL.

---

## `git remote remove`

Removes a remote connection.

```bash
git remote remove origin
```

---

## `git remote rename`

Renames a remote.

```bash
git remote rename origin upstream
```

---

## `git remote get-url`

Shows the URL of a remote.

```bash
git remote get-url origin
```

---

# 13. Pushing to GitHub

## `git push`

Uploads local commits to the remote repository.

```bash
git push
```

---

## `git push -u origin main`

Pushes the `main` branch and establishes an upstream connection.

```bash
git push -u origin main
```

### Understanding the command

```text
git push -u origin main
          │      │
          │      └── remote branch
          └──────── remote name
```

`-u` means **set upstream**.

After doing this once, you can usually simply use:

```bash
git push
```

---

## Push a new branch

```bash
git push -u origin feature-login
```