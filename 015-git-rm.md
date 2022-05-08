# `git rm`

[Git Cheat Sheet](./README.md) / git rm

---

Stop Git from tracking file/ folder.

**_Command_**

```none
git rm --cached <file_name>
```

`-r` flag is required to stop tracking a folder because the `rm` has to be applied to all files inside the folder recursively.

```none
git rm -r --cached <folder_name>
```

**_Note_**

The change will become effective on the next commit.
