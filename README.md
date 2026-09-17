# 27. Recovering Lost Work

## `git reflog`

Shows where `HEAD` and branch references have previously pointed.

```bash
git reflog
```

It can help recover commits after commands such as:

```bash
git reset
```

or accidental branch changes.

Example:

```text
a82f31c HEAD@{0}: commit: Add login
72ab921 HEAD@{1}: reset: moving to HEAD~1
```

You can then inspect or recover an earlier state using the commit ID.

---
# 28. Finding Bugs With `git bisect`

`git bisect` helps find which commit introduced a bug.

Start:

```bash
git bisect start
```

Mark the current version as bad:

```bash
git bisect bad
```

Mark a known working commit as good:

```bash
git bisect good <commit-id>
```

Git will check commits between the good and bad versions.

After finding the problematic commit:

```bash
git bisect reset
```

---
# 29. Cleaning Untracked Files

## `git clean -n`

Shows which untracked files would be removed without actually removing them.

```bash
git clean -n
```

---

## `git clean -f`

Deletes untracked files.

```bash
git clean -f
```

---
# 30. Git Aliases

Aliases allow you to create shorter commands.

Example:

```bash
git config --global alias.st status
```

Now:

```bash
git st
```

does the same thing as:

```bash
git status
```

Another example:

```bash
git config --global alias.co checkout
```

Then:

```bash
git co main
```

---

# 31. Useful Git Information Commands

## `git branch -vv`

Shows local branches and their upstream branches.

```bash
git branch -vv
```

Useful for seeing which remote branch your local branch is connected to.

---

## `git remote show`

Shows information about a remote repository.

```bash
git remote show origin
```

---

## `git ls-files`

Lists files currently tracked by Git.

```bash
git ls-files
```

---

## `git rev-parse`

Can be used to inspect Git references and repository information.

Example:

```bash
git rev-parse --show-toplevel
```

Shows the root directory of the repository.

---

# 32. Getting Help

## `git help`

Displays general Git documentation.

```bash
git help
```

For a specific command:

```bash
git help commit
```

You can also use:

```bash
git commit --help
```

---

# 33. GitHub Collaboration Commands

When working with other developers, a common workflow is:

```text
main
  │
  ├── feature-login
  │
  ├── feature-dashboard
  │
  └── feature-profile
```

Each developer can work on a separate branch.

Typical process:

```bash
git pull
git switch -c feature-login

# Make changes

git status
git add .
git commit -m "Add login page"
git push -u origin feature-login
```

The branch can then be reviewed and merged into `main` through a **Pull Request** on GitHub.

---

# 34. Common Complete Workflows

## A. Starting a new local project

```bash
mkdir my-project
cd my-project
git init

git add .
git commit -m "Initial commit"
```

---

## B. Connecting a local project to GitHub

```bash
git remote add origin <repository-url>
git branch -M main
git push -u origin main
```

---

## C. Cloning an existing GitHub project

```bash
git clone <repository-url>
cd project-name
```

---

## D. Making normal changes

```bash
git status
git add .
git commit -m "Update project"
git push
```

---

## E. Starting a new feature

```bash
git switch main
git pull

git switch -c feature-login

# Work on the feature

git add .
git commit -m "Add login page"
git push -u origin feature-login
```

---

## F. Updating your branch

```bash
git switch main
git pull

git switch feature-login
git merge main
```

Or, depending on the team's workflow:

```bash
git switch feature-login
git rebase main
```

---

# 35. `git merge` vs `git rebase`

Both can bring changes from one branch into another, but they work differently.

### Merge

```bash
git merge main
```

Combines histories and may create a merge commit.

### Rebase

```bash
git rebase main
```

Moves your commits so they appear on top of the latest `main`.

Simplified:

```text
MERGE

A---B---C main
     \
      D---E feature
           \
            merge


REBASE

A---B---C main
         \
          D'---E' feature
```

> Rebase rewrites commit history. Avoid rebasing commits that other people are already using unless your team has agreed on it.

---

# 36. Essential Command Reference

| Command | Purpose |
|---|---|
| `git --version` | Check Git version |
| `git config` | Configure Git |
| `git init` | Create repository |
| `git clone` | Copy remote repository |
| `git status` | Check repository status |
| `git add` | Stage changes |
| `git commit` | Save changes |
| `git commit --amend` | Modify latest commit |
| `git diff` | View changes |
| `git log` | View commit history |
| `git show` | View commit details |
| `git branch` | Create/list/delete branches |
| `git switch` | Switch branches |
| `git checkout` | Older branch/file command |
| `git merge` | Merge branches |
| `git rebase` | Reapply commits on another base |
| `git remote` | Manage remote repositories |
| `git fetch` | Download remote information |
| `git pull` | Fetch and integrate remote changes |
| `git push` | Upload commits |
| `git restore` | Restore files/unstage changes |
| `git reset` | Move branch/undo commits |
| `git revert` | Undo a commit with a new commit |
| `git rm` | Remove tracked files |
| `git stash` | Temporarily save changes |
| `git tag` | Mark project versions |
| `git blame` | Show who changed each line |
| `git reflog` | View reference history |
| `git bisect` | Find a problematic commit |
| `git clean` | Remove untracked files |
| `git shortlog` | Summarize commits |
| `git ls-files` | List tracked files |
| `git help` | Get Git documentation |

---