# `git show`

[Git Cheat Sheet](./README.md) / git show

---

1. Get file from specific commit and overwrite the current file. The `FILE_PATH` is relative to the repository root.

   **_Command_**

   ```none
   git show <OLD_COMMIT_HASH>:<FILE_PATH> > <FILE_PATH>
   ```

   **_Example_**

   Get file `src/routes/product.js` from old commit hash `a1b2c3d4e` and overwrite the latest one.

   ```none
   git show a1b2c3d4e:src/routes/product.js > src/routes/product.js
   ```

2. Show details of the most recent commit (`HEAD`)

   **_Command_**

   ```none
   git show HEAD
   ```
