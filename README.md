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
