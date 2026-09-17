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

