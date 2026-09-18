 Getting Changes From GitHub

## `git fetch`

Downloads information about changes from the remote repository without automatically merging them into your current branch.

```bash
git fetch
```

Think:

> "Check what changed on GitHub."

---

## `git fetch --all`

Fetches information from all configured remotes.

```bash
git fetch --all
```

---

<<<<<<< HEAD
## `git pull`

Downloads remote changes and integrates them into your current branch.

```bash
git pull
```

Or:

```bash
git pull origin main
```

Think:

> "Get the latest changes from GitHub and integrate them into my branch."

---

## `git pull --rebase`

Fetches remote changes and replays your local commits on top of them.

```bash
git pull --rebase
```

This can keep the project history more linear.

---

# 15. Remote Branches

## List remote branches

```bash
git branch -r
=======
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
>>>>>>> main
```

---

<<<<<<< HEAD
## List all branches

```bash
git branch -a
```

This shows local and remote-tracking branches.
=======
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
>>>>>>> main

Example:

```text
* main
  feature-login
<<<<<<< HEAD
  remotes/origin/main
  remotes/origin/feature-login
```

---

## Create a local branch from a remote branch

```bash
git switch -c feature-login --track origin/feature-login
```

A shorter form often works:
=======
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
>>>>>>> main

```bash
git switch feature-login
```

<<<<<<< HEAD
if Git can automatically identify the matching remote branch.

 git push --set-upstream origin flavia
 # 16. Merging Branches

## `git merge`

Combines another branch into the current branch.

Example:

```bash
git switch main
git merge feature-login
```

This means:

> Merge `feature-login` into `main`.

The order matters: you switch to the branch that should receive the changes.

---

# 17. Merge Conflicts

A merge conflict occurs when Git cannot automatically combine changes.

For example:

```text
<<<<<<< HEAD
Your version
=======
Other version
>>>>>>> feature-login
```

You must manually edit the file and decide what the final version should contain.

Then:

```bash
git add .
git commit
```

If you want to cancel the merge:

```bash
git merge --abort
```

18. Restoring Files

## `git restore`

Discards unstaged changes in a file.

```bash
git restore index.html
```


---

## `git restore --staged`

Removes a file from the staging area without deleting your changes.

```bash
git restore --staged index.html
```

Example:

```bash
git add index.html
git restore --staged index.html
```

The file remains modified, but it is no longer staged.

---
# 19. Undoing Commits

## `git reset`

Moves the current branch to another commit.

### Soft reset

```bash
git reset --soft HEAD~1
```

Removes the last commit but keeps the changes staged.

### Mixed reset

```bash
git reset HEAD~1
```

Removes the last commit and unstages the changes, but keeps the files' changes.

### Hard reset

```bash
git reset --hard HEAD~1
```

Removes the last commit and its changes.
# 20. `git revert`

Creates a new commit that reverses the changes introduced by an earlier commit.

```bash
git revert <commit-id>
```

Example:

```bash
git revert a82f31c
```

### Reset vs Revert

| Command | What it does |
|---|---|
| `git reset` | Moves the branch backward |
| `git revert` | Creates a new commit that undoes an earlier commit |

For commits that have already been pushed and shared, `git revert` is generally safer because it preserves the existing history.

---# 21. Stashing Work

Sometimes you have unfinished changes but need to switch branches.

## `git stash`

Temporarily saves uncommitted changes.

```bash
git stash
```

Your working directory becomes clean.

---

## `git stash list`

Shows saved stashes.

```bash
git stash list
=======
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
>>>>>>> main
```

Example:

```text
<<<<<<< HEAD
stash@{0}: WIP on feature-login
stash@{1}: WIP on main
=======
origin  https://github.com/user/project.git (fetch)
origin  https://github.com/user/project.git (push)
>>>>>>> main
```

---

<<<<<<< HEAD
## `git stash pop`

Restores the most recent stash and removes it from the stash list.

```bash
git stash pop
```

---

## `git stash apply`

Restores a stash but keeps it in the stash list.

```bash
git stash apply
```

---

## Apply a specific stash

```bash
git stash apply stash@{1}
```

---

## `git stash drop`

Deletes a stash.

```bash
git stash drop
```

---

## `git stash clear`

Deletes all stashes.

```bash
git stash clear
```
 22. Comparing Changes

## Compare working changes

```bash
git diff
```

---

## Compare staged changes

```bash
git diff --staged
```

---

## Compare two branches

```bash
git diff main feature-login
```

---

## Compare two commits

```bash
git diff <commit1> <commit2>
```

---

## Find commits that exist in one branch but not another

```bash
git log main..feature-login
```

This shows commits in `feature-login` that are not in `main`.

---


23. Removing Files

## `git rm`

Removes a file from your project and stages the deletion.

```bash
git rm file.txt
```

Then:

```bash
git commit -m "Remove unnecessary file"
```

---

## `git rm --cached`

Stops tracking a file but keeps it on your computer.

```bash
git rm --cached file.txt
```

This is useful when you accidentally tracked a file that should not be committed.

For example:

```bash
git rm --cached .env
```

Then add `.env` to `.gitignore`.

---
# 24. `.gitignore`

`.gitignore` tells Git which files should not be tracked.

Example:

```text
node_modules/
.env
*.log
dist/
```

Common things to ignore:

- Passwords and secrets
- Environment files
- Dependencies
- Temporary files
- Build files

Then:

```bash
git add .
git commit -m "Add gitignore"
```
# 25. Tags

Tags are used to mark specific versions of a project.

For example:

```text
v1.0
v2.0
v2.1
```

## Create a tag

```bash
git tag v1.0
=======
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
>>>>>>> main
```

---

<<<<<<< HEAD
## Create an annotated tag

```bash
git tag -a v1.0 -m "Version 1.0"
```

Annotated tags store additional information and are commonly used for releases.

---

## List tags

```bash
git tag
```

---

## Show tag information

```bash
git show v1.0
```

---

## Push a tag

```bash
git push origin v1.0
```

Push all tags:

```bash
git push origin --tags
```

---

## Delete a local tag

```bash
git tag -d v1.0
```

---

## Delete a remote tag

```bash
git push origin --delete v1.0
```

---

# 26. Finding Who Changed Something

## `git blame`

Shows who last modified each line of a file.

```bash
git blame index.html
```

Useful when working on a team and trying to understand the history of a particular line.

---
=======
## Push a new branch

```bash
git push -u origin feature-login
```
>>>>>>> main
