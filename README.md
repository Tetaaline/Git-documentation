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