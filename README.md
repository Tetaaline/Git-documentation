# Git & GitHub Commands Documentation

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

| Git                                 | GitHub                               |
| ----------------------------------- | ------------------------------------ |
| Software installed on your computer | Online platform                      |
| Tracks project history              | Hosts Git repositories               |
| Works locally                       | Used for sharing/collaboration       |
| Uses Git commands                   | Provides pull requests, issues, etc. |

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

After the upstream is established:

```bash
git push
```

is normally enough.

---

## Delete a remote branch

```bash
git push origin --delete feature-login
```

This deletes the branch from the remote repository.

---

# 14. Getting Changes From GitHub

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
```

---

## List all branches

```bash
git branch -a
```

This shows local and remote-tracking branches.

Example:

```text
* main
  feature-login
  remotes/origin/main
  remotes/origin/feature-login
```

---

## Create a local branch from a remote branch

```bash
git switch -c feature-login --track origin/feature-login
```

A shorter form often works:

```bash
git switch feature-login
```

if Git can automatically identify the matching remote branch.

---

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

---

# 18. Restoring Files

## `git restore`

Discards unstaged changes in a file.

```bash
git restore index.html
```

The uncommitted changes in that file will be lost.

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

`--hard` can permanently discard work. Use it carefully.

---

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

| Command      | What it does                                       |
| ------------ | -------------------------------------------------- |
| `git reset`  | Moves the branch backward                          |
| `git revert` | Creates a new commit that undoes an earlier commit |

For commits that have already been pushed and shared, `git revert` is generally safer because it preserves the existing history.

---

# 21. Stashing Work

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
```

Example:

```text
stash@{0}: WIP on feature-login
stash@{1}: WIP on main
```

---

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

Use carefully.

---

# 22. Comparing Changes

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

# 23. Removing Files

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

> `.gitignore` only affects files that Git is not already tracking. If a file is already tracked, you may need `git rm --cached` first.

---

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
```

---

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

# 37. The Commands You Should Know First

Although Git has many commands, these are the core commands to become comfortable with:

```bash
git status
git add .
git commit -m "message"
git push
git pull
git clone <url>

git branch
git switch -c <branch>
git switch <branch>
git merge <branch>

git remote -v
git fetch

git log --oneline
git diff

git restore <file>
git restore --staged <file>

git stash
git revert <commit>
```

### The basic mental model

Remember Git as:

```text
                    GIT WORKFLOW

     Edit/Create Files
            │
            ▼
       git status
            │
            ▼
         git add
            │
            ▼
      Staging Area
            │
            ▼
       git commit
            │
            ▼
     Local Repository
            │
            ▼
         git push
            │
            ▼
          GitHub
```

And when someone else changes the GitHub repository:

```text
GitHub
   │
   ▼
git fetch       → See/download remote changes
   │
   ▼
git pull        → Get and integrate remote changes
```

---

# 38. Common Troubleshooting

### "I don't know what is happening."

```bash
git status
```

### "I want to see what I changed."

```bash
git diff
```

### "I accidentally staged a file."

```bash
git restore --staged filename
```

### "I want to discard my changes."

```bash
git restore filename
```

### "I need to temporarily put my work aside."

```bash
git stash
```

### "I want my work back."

```bash
git stash pop
```

### "I need to see previous commits."

```bash
git log --oneline
```

### "I want to know which remote I'm connected to."

```bash
git remote -v
```

### "I need the latest version from GitHub."

```bash
git pull
```

### "I want to upload my committed work."

```bash
git push
```

### "I accidentally made a bad commit."

If it has not been shared:

```bash
git reset --soft HEAD~1
```

If it has already been shared:

```bash
git revert <commit-id>
```

---