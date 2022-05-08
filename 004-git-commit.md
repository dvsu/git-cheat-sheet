# `git commit`

[Git Cheat Sheet](./README.md) / git commit

---

1. Move content from staging area to local repository

   **_Command_**

   ```none
   git commit
   ```

   This command will open a file where you can type your commit message.

   **_Example_**

   ```none
   Fix UI bug found on feature 2S
   ```

   Save and close the file to complete the commit.

   To do the same process in line

   **_Command_**

   ```none
   git commit -m <COMMIT_MESSAGE>
   ```

   **_Example_**

   ```none
   git commit -m "Fix UI bug found on feature 2S"
   ```

   **_Output_**

   ```none
   [mybranch 1a2b3c4] Fix UI bug found on feature 2S
   1 file changed, 50 insertions(+), 18 deletions(-)
   ```

2. Stage and commit changes to local repository

   **_Command_**

   ```none
   git commit -a -m <COMMIT_MESSAGE>
   ```

   The `git commit -a -m` command is a shortcut for

   ```none
   git add <FILE_NAME>
   ```

   and

   ```none
   git commit -m <COMMIT_MESSAGE>
   ```

3. Revise latest commit

   **_Command_**

   ```none
   git commit --amend
   ```

   This command will also open a file where you can edit the latest commit message.

   Similarly, you can do it in line.

   **_Command_**

   ```none
   git commit --amend -m <NEW_COMMIT_MESSAGE>
   ```

   **_Example_**

   Assume you spot a typo in `readme.md` of the latest commit. You fix the typo and stage the change.

   ```none
   git add readme.md
   ```

   To include the fix and amend it to the latest commit with new commit message

   ```none
   git commit --amend -m "Fix UI bug found on feature 2T"
   ```

   To keep the same commit message

   ```none
   git commit --amend --no-edit
   ```
