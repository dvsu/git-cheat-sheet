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
14. `git submodule`

### 1. `git config`

---

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
   git config --global user.name {NAME}
   ```

   **_Example_**

   ```none
   git config --global user.name "Adam Smith"
   ```

3. Add user email

   **_Command_**

   ```none
   git config --global user.email {EMAIL}
   ```

   **_Example_**

   ```none
   git config --global user.email "adam.smith@example.com"
   ```

### 2. `git init`

---

1. Initialize empty Git repository

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

   ```none
   ~$ mkdir web_project
   ~$ cd web_project
   ~/web_project$ git init
   ```

   **_Example output_**

   ```none
   Initialized empty Git repository in /home/ubuntu/web_project/.git/
   ```

### 4. `git commit`

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
   git commit -m {COMMIT_MESSAGE}
   ```

   **_Example_**

   ```none
   git commit -m "Fix UI bug found on feature 2S"
   ```

   **_Example output_**

   ```none
   [mybranch 1a2b3c4] Fix UI bug found on feature 2S
   1 file changed, 50 insertions(+), 18 deletions(-)
   ```

2. Revise commit message of latest commit

   **_Command_**

   ```none
   git commit --amend
   ```

   This command will also open a file where you can edit the latest commit message.

   Similarly, you can do it in line.

   **_Command_**

   ```none
   git commit --amend -m {NEW_COMMIT_MESSAGE}
   ```

   **_Example_**

   ```none
   git commit --amend -m "Fix UI bug found on feature 2T"
   ```

### 7. `git remote`

---

1. Check existing remote configuration

   Show alias only

   **_Command_**

   ```none
   git remote
   ```

   **_Example output_**

   ```none
   origin
   ```

   Show alias + URL

   **_Command_**

   ```none
   git remote -v
   ```

   **_Example output_**

   ```none
   origin  git@github.com:mysuperaccount/shinyrepo.git (fetch)
   origin  git@github.com:mysuperaccount/shinyrepo.git (push)
   ```

2. Create a new connection to remote repository

   **_Command_**

   ```none
   git remote add {ALIAS} {URL}
   ```

   **_Example_**

   ```none
   git remote add origin git@github.com:mysuperaccount/shinyrepo.git
   ```

   This command will add a new connection to remote repo `shinyrepo` and create a local alias `origin`. The alias is essentially a shortcut for the full URL. Instead of typing the whole URL for every interaction with remote repo, we can simply type the alias name, in this case `origin` to replace the URL.

3. Check remote URL of specific alias

   **_Command_**

   ```none
   git remote get-url {ALIAS}
   ```

   **_Example_**

   ```none
   git remote get-url origin
   ```

   **_Example output_**

   ```none
   git@github.com:mysuperaccount/shinyrepo.git
   ```

   This command is very straightforward, which is to get the URL of an alias. In most cases, `git remote -v` is a more convenient command to use, as it shows all information of remote configuration.

4. Change alias of remote repository

   **_Command_**

   ```none
   git remote rename {OLD_ALIAS} {NEW_ALIAS}
   ```

   **_Example_**

   ```none
   git remote rename origin somethingcool
   ```

   This command will rename the existing alias `origin` to `somethingcool`. To confirm the command is successfully executed,
   use command `git remote -v`

   **_Example output_**

   ```none
   somethingcool  git@github.com:mysuperaccount/shinyrepo.git (fetch)
   somethingcool  git@github.com:mysuperaccount/shinyrepo.git (push)
   ```

5. Change/ rename URL of remote repository

   **_Command_**

   ```none
   git remote set-url {ALIAS} {NEW_URL}
   ```

   **_Example_**

   ```none
   git remote set-url origin git@github.com:mysuperaccount/shinierrepo.git
   ```

   This command will change the URL of alias `origin` from `git@github.com:mysuperaccount/shinyrepo.git` to `git@github.com:mysuperaccount/shinierrepo.git`. Again, to confirm whether the command is successfully executed, use command `git remote -v`

### 14. `git submodule`

---

Add a submodule to current repository

**_Command_**

```none
git submodule add git@github.com:{myaccount}/{myrepo}.git {path_name}
```

**_Example_**

Let say we want to add a submodule and name the path, `dashboard`, from our Github account, `mysuperaccount`, to current repository, `car`. If it is successful, Git will create a new file, `.gitmodule`, in current repository. If `.gitmodule` has already existed, Git will instead append the details of submodule.

```none
git submodule add git@github.com:mysuperaccount/dashboard.git dashboard
```

```none
car
├── ...
├── .gitignore
├── .gitmodule
├── ...
├── dashboard
│   ├── ...
│   ├── ...
│   └── ...
└── ...
```

Example of content inside `.gitmodule`

```none
[submodule "dashboard"]
	path = dashboard
	url = git@github.com:mysuperaccount/dashboard.git
```

In some cases, the path name may have already existed in `car` repository. Git will complain

```none
'dashboard' already exists in the index
```

If the path exists because we cloned the `dashboard` repository before, the workaround is to add `--force` flag to the Git command

**_Command_**

```none
git submodule add --force git@github.com:{myaccount}/{myrepo}.git {path_name}
```

**_Example_**

```none
git submodule add --force git@github.com:mysuperaccount/dashboard.git dashboard
```
