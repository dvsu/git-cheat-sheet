# `git checkout`

[Git Cheat Sheet](./README.md) / git checkout

---

1. Restore staged or unstaged changes to latest commit (undo changes)

   **_Command_**

   ```none
   git checkout HEAD <FILE_NAME>
   ```

   Alternative

   ```none
   git checkout -- <FILE_NAME>
   ```

   **_Example_**

   `app.js` content of latest commit

   ```javascript
   const express = require("express");
   const app = express();

   app.get("/", (req, res, next) => {
     return res.send("<h1>Hi there!</h1>");
   });

   app.listen(3000);
   ```

   Then you made a change

   ```javascript
   const express = require("express");
   const app = express();

   app.get("/", (req, res, next) => {
     return res.send("<h1>Rise and shine!</h1>");
   });

   // port 3000 in use by React app. Change to 5000
   app.listen(5000);
   ```

   and stage it.

   ```none
   git add app.js
   ```

   Soon you realize the change is not necessary and plan to restore the `app.js` to its original state (latest commit).

   ```none
   git checkout HEAD app.js
   ```

   At this point, the file content will be back to its original state

2. Rewind to specific commit and detach from branches

   **_Command_**

   ```none
   git checkout <COMMIT_HASH>
   ```

   **_Example_**

   Assume you made 3 commits

   ```none
   fc01324 (HEAD -> main) Remove UI component of feature B
   110fa48 Add feature B
   bec5e72 Feature A: bugfix
   ```

   You want to rewind to commit `bec5e72`

   ```none
   git checkout bec5e72
   ```

   After executing the command, you will be detached from `main` branch.

   ```none
   bec5e72 (HEAD) Feature A: bugfix
   ```

   Any changes made from this commit afterwards will not affect the original branch (`main`)

3. Create and switch to new branch

   **_Command_**

   ```none
   git checkout -b <NEW_BRANCH_NAME>
   ```

   **_Example_**

   Creating new branch after rewinding to old commit (as of example in point 2)

   ```none
   git checkout -b security-fix
   ```

   It will create and switch to a new branch named `security-fix`. This branch will also be connected back to _trunk_ (previously detached)
