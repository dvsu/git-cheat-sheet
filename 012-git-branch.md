# `git branch`

[Git Cheat Sheet](./README.md) / git branch

---

1. Check existing local branches

   **_Command_**

   ```none
   git branch
   ```

   **_Output_**

   ```none
   * master
     branch1
     branchn
   ```

2. Rename branch

   **_Command_**

   ```none
   git branch -m <BRANCH_NAME> <NEW_NAME>
   ```

   **_Example_**

   Change branch name `master` to `main`

   ```none
   git branch -m master main
   ```

3. Delete local branch

   **_Command_**

   ```none
   git branch -d <BRANCH_NAME>
   ```

   **_Example_**

   Delete `branch1` from local branches

   ```none
   git branch -d branch1
   ```
