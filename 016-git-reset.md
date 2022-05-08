# `git reset`

[Git Cheat Sheet](./README.md) / git reset

---

1. Move the tip of current branch (`HEAD`) back to previous commit, i.e. reset latest commit.

   **_Command_**

   ```none
   git reset --hard HEAD^
   ```

   **_Note_**

   It will also virtually remove/ detach the latest commit from history as if it does not exist from `HEAD` point of view. In fact, commit `fc01234` still exists if we manually `checkout` to it.

   **_Example_**

   Before

   ```none
   fc01324 (HEAD -> main) Remove UI component of feature B
   110fa48 Add feature B
   bec5e72 Feature A: bugfix
   ```

   After

   ```none
   110fa48 (HEAD -> main) Add feature B
   bec5e72 Feature A: bugfix
   ```

2. Rewind/ back to specific commit, preserve the differences and mark them as `modified` and `unstaged`

   **_Command_**

   ```none
   git reset <COMMIT_HASH>
   ```

   **_Example_**

   Assume you made 3 commits to track changes of `doc.txt`.

   Content of `doc.txt`, first commit (`bec5e72`)

   ```none
   This is first commit
   ```

   Content of `doc.txt`, second commit (`110fa48`)

   ```none
   This is first commit
   This is second commit
   ```

   Content of `doc.txt`, third commit (`fc01324`)

   ```none
   This is first commit
   This is second commit
   This is third commit
   ```

   Rewind to commit `bec5e72` (first commit)

   ```none
   git reset bec5e72
   ```

   Before

   ```none
   fc01324 (HEAD -> main) Remove UI component of feature B
   110fa48 Add feature B
   bec5e72 Feature A: bugfix
   ```

   After

   ```none
   bec5e72 (HEAD -> main) Feature A: bugfix
   ```

   Content of `doc.txt` after reset

   ```none
   This is first commit
   This is second commit  <-- this is the preserved change made after commit bec5e72
   This is third commit  <-- this is also the preserved change. Both are modified and unstaged
   ```

   Commit `fc01324` and `110fa48` are _detached_ and are not part of the `main` branch anymore. The commits still exist if you `checkout` to the commit manually.

3. (similar to point 2) Rewind/ back to specific commit, preserve the differences and mark them as `modified` and `staged`

   **_Command_**

   ```none
   git reset --soft <COMMIT_HASH>
   ```

   **_Example_**

   Same example as point 2, but the difference after executing the `git reset --soft` command

   ```none
   git reset --soft bec5e72
   ```

   Content of `doc.txt` after reset

   ```none
   This is first commit
   This is second commit  <-- this is the preserved change made after commit bec5e72
   This is third commit  <-- this is also the preserved change. Both are modified and staged
   ```

4. (similar to point 2) Rewind/ back to specific commit and discard any differences made after this commit

   **_Command_**

   ```none
   git reset --hard <COMMIT_HASH>
   ```

   **_Example_**

   Same example as point 2, but the difference after executing the `git reset --hard` command

   ```none
   git reset --hard bec5e72
   ```

   Content of `doc.txt` after reset

   ```none
   This is first commit
   ```

   Notice the `This is second commit` and `This is third commit` are not preserved.

5. Remove a specific file or directory from staging area

   **_Command_**

   ```none
   git reset <FILE_NAME>
   ```

   It removes the file/ directory from staging area while preserving the latest change you made.
