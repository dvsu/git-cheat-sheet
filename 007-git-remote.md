# `git remote`

[Git Cheat Sheet](./README.md) / git remote

---

1. Check existing remote configuration

   Show alias only

   **_Command_**

   ```none
   git remote
   ```

   **_Output_**

   ```none
   origin
   ```

   Show alias + URL

   **_Command_**

   ```none
   git remote -v
   ```

   **_Output_**

   ```none
   origin  git@github.com:mysuperaccount/shinyrepo.git (fetch)
   origin  git@github.com:mysuperaccount/shinyrepo.git (push)
   ```

2. Create a new connection to remote repository

   **_Command_**

   ```none
   git remote add <ALIAS> <URL>
   ```

   **_Example_**

   ```none
   git remote add origin git@github.com:mysuperaccount/shinyrepo.git
   ```

   This command will add a new connection to remote repo `shinyrepo` and create a local alias `origin`. The alias is essentially a shortcut for the full URL. Instead of typing the whole URL for every interaction with remote repo, you can simply type the alias name, in this case `origin` to replace the URL.

3. Check remote URL of specific alias

   **_Command_**

   ```none
   git remote get-url <ALIAS>
   ```

   **_Example_**

   ```none
   git remote get-url origin
   ```

   **_Output_**

   ```none
   git@github.com:mysuperaccount/shinyrepo.git
   ```

   This command is very straightforward, which is to get the URL of an alias. In most cases, `git remote -v` is a more convenient command to use, as it shows all information of remote configuration.

4. Change alias of remote repository

   **_Command_**

   ```none
   git remote rename <OLD_ALIAS> <NEW_ALIAS>
   ```

   **_Example_**

   ```none
   git remote rename origin somethingcool
   ```

   This command will rename the existing alias `origin` to `somethingcool`. To confirm the command is successfully executed,
   use command `git remote -v`

   **_Output_**

   ```none
   somethingcool  git@github.com:mysuperaccount/shinyrepo.git (fetch)
   somethingcool  git@github.com:mysuperaccount/shinyrepo.git (push)
   ```

5. Change/ rename URL of remote repository

   **_Command_**

   ```none
   git remote set-url <ALIAS> <NEW_URL>
   ```

   **_Example_**

   ```none
   git remote set-url origin git@github.com:mysuperaccount/shinierrepo.git
   ```

   This command will change the URL of alias `origin` from `git@github.com:mysuperaccount/shinyrepo.git` to `git@github.com:mysuperaccount/shinierrepo.git`. Again, to confirm whether the command is successfully executed, use command `git remote -v`
