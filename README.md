# Git Cheat Sheet

The most common Git commands

## Contents

1. `git config`
2. `git init`
3. `git add`
4. `git commit`
5. `git status`
6. `git log`
7. `git remote`
8. `git push`
9. `git pull`
10. `git fetch`
11. `git clone`
12. `git branch`
13. `git checkout`
14. more to add

### `git config`

1. Show global configuration

   **_Command_**

   ```none
   git config --list
   ```

   **_Example output_**

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

   **_Example output_**

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
   git config --global user.name "myname"
   ```

   **_Example_**

   ```none
   git config --global user.name "Adam Smith"
   ```

3. Add user email

   **_Command_**

   ```none
   git config --global user.name "myemail@mydomain.com"
   ```

   **_Example_**

   ```none
   git config --global user.name "adam.smith@example.com"
   ```

### `git init`

Initialize empty Git repository

**_Command_**

```none
git init
```

**_Example_**

Let say we want to create a new repository with name `web_project`.

1. Create a folder `web_project`
2. Change directory to `web_project`
3. Run `git init` command

**_Example_**

```shell
~$ mkdir web_project
~$ cd web_project
~/web_project$ git init
```

**_Example output_**

```none
Initialized empty Git repository in /home/ubuntu/web_project/.git/
```
