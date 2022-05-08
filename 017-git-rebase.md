# `git rebase`

[Git Cheat Sheet](./README.md) / git rebase

---

Merge the last `x` commits into a single commit.

**_Command_**

```none
git rebase --interactive HEAD~x
```

or

```none
git rebase -i HEAD~x
```

`x` is the number of commits. `HEAD~3` means the last three commits, started from `HEAD`.

**_Example_**

```none
git rebase --interactive HEAD~5
```

Before

```none
cccccc latest   -----.
bbbbbb commit B      |
aaaaaa commit A      |-- merge into a single commit
999999 commit 9      |
888888 commit 8 -----'
777777 good commit
```

After

```none
dddddd revised
777777 good commit
```

**_Note_**

`git rebase` will create a new hash
