# `git pull`

[Git Cheat Sheet](./README.md) / git pull

---

A shortcut command to `fetch` and `merge` to the local checked-out branch.

**_Command_**

```none
git pull <ALIAS> <REMOTE_BRANCH>
```

**_Example_**

If you want to sync and merge your remote repo with alias `origin` and branch name `main`, to current checked-out branch, the command is

```none
git pull origin main
```

There is also a case when you created and did the first commit on a new remote repo. Later on, you also initialized a new Git repo locally and wanted to sync both repos.

When you try to `git pull`, e.g.

```none
git pull origin main
```

this error message may pop up

```none
fatal: refusing to merge unrelated histories
```

It is because both repos have two completely different histories, e.g. different commit hashes

```none
remote repo
   commit (a1b2c3d)
     x-----------------------

local repo
   commit (e5f6a1b)
     x-----------------------
```

The simple solution is to merge them locally using `--allow-unrelated-histories` option.

**_Command_**

```none
git pull <ALIAS> <REMOTE_BRANCH> --allow-unrelated-histories
```

**_Example_**

```none
git pull origin main --allow-unrelated-histories
```

```none
remote repo
   commit a1b2c3d
     x----------------------.
                             \
local repo                    \
   commit e5f6f8c              \
     x--------------------------x--------------- (your next commit may
                           commit ad982cf           start from here)
                         merge e5f6f8c a1b2c3d
```
