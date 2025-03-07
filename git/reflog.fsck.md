# Git Reflog – Managing Reference History (HEAD)

- **offical documentation : [git-scm.com](https://git-scm.com/)**

### 🔥 Display reflog history

```sh
git reflog show [HEAD | branch_name | remote/origin/main | --all]
```

### 🔥 Delete reflog history

```sh
git reflog expire --expire=now [--all | branch_name | remote]
```

### 🔥 Reset branch to a previous state (reset ref)

```sh
git reflog reset --hard main@{3}
```

⏳ Note: When reflog is available, you can reset at different levels:

- --hard (lose changes)

- --soft (keep changes)

- --mixed (reset index only)

### Dangling Object – Objects with No References

**🚨 Types of dangling objects:**

- Type Represents When does it occur?

- **Blob** : File content git add file, then git reset

- **Tree** : Directory of blobs/trees git add or git commit, then git reset removes the ref

- **Commit** : Commit history git commit, then git reset --hard or git rebase

### 🔥 Check for dangling objects:

```sh
git fsck --full # Find unlinked objects
```

### 🔥 Identify object type (blob, commit, tree, tag...):

```sh
git cat-file -t object_hash
```

### 🔥 View object content:

Blob (modified file content):

```sh
git cat-file -p blob_hash
```

Commit (restore using checkout, cherry-pick...):

```sh
git checkout commit_hash
```

Tree (list of blobs & subtrees):

```sh
git ls-tree tree_hash
```

### Cleanup Mechanism – When Are Dangling Objects Deleted?

🚀 Git GC (Garbage Collection) cleans up dangling objects as follows:

- Dangling commits can be recovered via reflog (if not yet deleted by GC).
- Dangling blobs/trees will be permanently deleted if git gc --prune=now runs.

### 🔥 Immediately remove dangling objects (use with caution!):

```sh
git gc --prune=now
```
