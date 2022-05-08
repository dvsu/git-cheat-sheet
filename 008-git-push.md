# `git push`

[Git Cheat Sheet](./README.md) / git push

---

1. Upload/ push local commits to a remote repository with the same branch name.

   **_Command_**

   ```none
   git push <ALIAS> <BRANCH_NAME>
   ```

   To upload local commits to a remote repository with alias `origin` branch `main`

   **_Example_**

   ```none
   git push origin main
   ```

2. Rename remote branch

   **_Command_**

   ```none
   git push <ALIAS> <LOCAL_BRANCH>:<REMOTE_BRANCH>
   ```

   **_Example_**

   Upload commits from local branch `ft1` to a remote repository and rename remote branch name to `feature1`

   ```none
   git push origin ft1:feature1
   ```

3. Delete remote branch

   **_Command_**

   ```none
   git push <ALIAS> :<REMOTE_BRANCH>
   ```

   **_Example_**

   Delete remote branch `feature1` from remote repository with alias `origin`.

   ```none
   git push origin :feature1
   ```

   It basically tells `git` to upload/ push nothing into remote branch `feature1`, which essentially deletes the remote branch.

4. Delete remote branch (alternative)

   **_Command_**

   ```none
   git push <ALIAS> --delete <REMOTE_BRANCH>
   ```

   **_Example_**

   Delete remote branch `feature1` from remote repository with alias `origin`.

   ```none
   git push origin --delete feature1
   ```

5. Upload/ push all local tags to remote repository

   **_Command_**

   ```none
   git push --tags <ALIAS>
   ```

   **_Example_**

   Upload/ push all local tags to a remote repository with alias `origin`

   ```none
   git push --tags origin
   ```

6. Delete remote tag

   **_Command_**

   ```none
   git push <ALIAS> :refs/tags/<REMOTE_TAG_NAME>
   ```

   **_Example_**

   Delete remote tag `1.2.3` from remote repository with alias `origin`.

   ```none
   git push origin :refs/tags/1.2.3
   ```

7. Upload/ push amended commit

   **_Command_**

   ```none
   git push --force-with-lease
   ```

   **_Note_**

   Push will be rejected if remote repository has newer updates/ commits.
