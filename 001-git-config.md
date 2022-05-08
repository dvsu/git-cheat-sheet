# `git config`

[Git Cheat Sheet](./README.md) / git config

---

1. Show global configuration

   **_Command_**

   ```none
   git config --list
   ```

   **_Output_**

   ```none
   user.name=Adam Smith
   user.email=adam.smith@example.com
   core.repositoryformatversion=0
   core.filemode=true
   core.bare=false
   core.logallrefupdates=true
   ```

   Alternatively

   ```none
   git config --list --show-origin
   ```

   **_Output_**

   ```none
   file:/home/ubuntu/.gitconfig    user.name=Adam Smith
   file:/home/ubuntu/.gitconfig    user.email=adam.smith@example.com
   file:.git/config        core.repositoryformatversion=0
   file:.git/config        core.filemode=true
   file:.git/config        core.bare=false
   file:.git/config        core.logallrefupdates=true
   ```

2. Add user name

   **_Command_**

   ```none
   git config --global user.name <NAME>
   ```

   **_Example_**

   ```none
   git config --global user.name "Adam Smith"
   ```

3. Add user email

   **_Command_**

   ```none
   git config --global user.email <EMAIL>
   ```

   **_Example_**

   ```none
   git config --global user.email "adam.smith@example.com"
   ```

4. Detect capitalization change

   **_Command_**

   ```none
   git config core.ignorecase false
   ```

   **_Example_**

   If `ignorecase` is `true` (default value), when you change directory name from

   ```none
   Product/readme.md
   ```

   to

   ```none
   product/readme.md --> (no change)
   ```

   Git will ignore the change because `Product` and `product` are essentially the same, i.e. `product` (ignorecase) is equal to `product`. However, if `ignorecase` is `false`, `Product` is not equal to `product`. Therefore, it will be detected as a change.

   ```none
   product/readme.md --> (a change)
   ```

5. Create an alias for a lengthy command

   **_Command_**

   ```none
   git config --global alias.<ALIAS_NAME> "<COMMAND_NAME>"
   ```

   **_Example_**

   Assume you use customized `git log` command to print beautiful log to terminal.

   ```none
   git log --pretty=format:'%h %aD %d %f' --graph
   ```

   It is really cumbersome to remember and type a very long command for generating the customized log. The command can be assigned to an alias and applied globally with `--global` option, so the _shortcut_ command exists in the whole system.

   ```none
   git config --global alias.logoneliner "log --pretty=format:'%h %aD %d %f' --graph"
   ```

   To test the new shortcut

   ```none
   git logoneliner
   ```
