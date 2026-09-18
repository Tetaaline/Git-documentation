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


