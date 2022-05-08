# `git tag`

[Git Cheat Sheet](./README.md) / git tag

---

1. Create tag for the latest commit

   **_Command_**

   ```none
   git tag <TAG_NAME>
   ```

   **_Example_**

   Create tag for the latest commit with name `v0.0.1`

   ```none
   git tag v0.0.1
   ```

2. Create tag with tag message for the latest commit

   **_Command_**

   ```none
   git tag -a <TAG_NAME> -m <TAG_MESSAGE>
   ```

   **_Example_**

   Create tag for the latest commit with name `v0.0.1` and tag message `Version 0.0.1`

   ```none
   git tag -a v0.0.1 -m "Version 0.0.1"
   ```

3. Display/ show all tags

   **_Command_**

   ```none
   git tag
   git tag -l
   git tag --list
   ```

4. Delete a tag

   **_Command_**

   ```none
   git tag -d <TAG_NAME>
   ```

   **_Example_**

   Delete a tag with name `v1.0.1`

   ```none
   git tag -d v1.0.1
   ```

5. Create tag for specific commit

   **_Command_**

   ```none
   git tag -a <TAG_NAME> <COMMIT_HASH>
   ```

   **_Example_**

   Create a tag `v2.0.0` for commit `a1b2c3d4e5f6...`

   ```none
   git tag -a v2.0.0 a1b2c3d
   ```

6. Create tag for specific commit with specific tag name and message

   **_Command_**

   ```none
   git tag -a <TAG_NAME> <COMMIT_HASH> -m <TAG_MESSAGE>
   ```

   **_Example_**

   Create tag `v2.0.0` for commit `a1b2c3d4e5f6...` with tag message `Version 2.0.0`

   ```none
   git tag -a v2.0.0 a1b2c3d -m "Version 2.0.0"
   ```
