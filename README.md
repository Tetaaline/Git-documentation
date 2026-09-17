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
