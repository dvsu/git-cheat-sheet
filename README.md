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
15. `git rm`
16. `git reset`
17. `git rebase`
18. `git tag`
19. `git show`
20. `git diff`

### 1. `git config`

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

### 2. `git init`

---

1. Initialize empty Git repository

   **_Command_**

   ```none
   git init
   ```

   **_Example_**

   Let say you want to create a new repository with name `web_project`.

   1. Create a folder `web_project`
   2. Change directory to `web_project`
   3. Run `git init` command

   **_Example_**

   ```none
   ~$ mkdir web_project
   ~$ cd web_project
   ~/web_project$ git init
   ```

   **_Output_**

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

2. Revise commit message of latest commit

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

### 8. `git push`

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

### 9. `git pull`

---

A shortcut command to `fetch` and `merge` to the local checked-out branch.

**_Command_**

```none
git pull <ALIAS> <REMOTE_BRANCH>
```

**_Example_**

If you want to sync and merge your remote repo with alias `origin` and branch name `main`, to current checked-out branch, the command is

```none
git pull origin main
```

There is also a case when you created and did the first commit on a new remote repo. Later on, you also initialized a new Git repo locally and wanted to sync both repos.

When you try to `git pull`, e.g.

```none
git pull origin main
```

this error message may pop up

```none
fatal: refusing to merge unrelated histories
```

It is because both repos have two completely different histories, e.g. different commit hashes

```none
remote repo
   commit (a1b2c3d)
     x-----------------------

local repo
   commit (e5f6g8h)
     x-----------------------
```

The simple solution is to merge them locally using `--allow-unrelated-histories` option.

**_Command_**

```none
git pull <ALIAS> <REMOTE_BRANCH> --allow-unrelated-histories
```

**_Example_**

```none
git pull origin main --allow-unrelated-histories
```

```none
remote repo
   commit a1b2c3d
     x----------------------.
                             \
local repo                    \
   commit e5f6f8c              \
     x--------------------------x--------------- (your next commit may
                           commit ad982cf           start from here)
                         merge e5f6f8c a1b2c3d
```

### 11. `git clone`

---

1. Clone remote repo

   **_Command_**

   ```none
   git clone <REMOTE_REPO_URL>
   ```

2. Clone remote repo which contains submodule

   **_Command_**

   ```none
   git clone <REMOTE_REPO_URL> --recurse-submodules
   ```

### 12. `git branch`

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

### 14. `git submodule`

---

Add a submodule to current repository

**_Command_**

```none
git submodule add git@github.com:<myaccount>/<myrepo>.git <path_name>
```

**_Example_**

Let say you want to add a submodule and name the path, `dashboard`, from our Github account, `mysuperaccount`, to current repository, `car`. If it is successful, Git will create a new file, `.gitmodule`, in current repository. If `.gitmodule` has already existed, Git will instead append the details of submodule.

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

If the path exists because you cloned the `dashboard` repository before, the workaround is to add `--force` flag to the Git command

**_Command_**

```none
git submodule add --force git@github.com:<myaccount>/<myrepo>.git <path_name>
```

**_Example_**

```none
git submodule add --force git@github.com:mysuperaccount/dashboard.git dashboard
```

### 15. `git rm`

---

Stop Git from tracking file/ folder.

**_Command_**

```none
git rm --cached <file_name>
```

`-r` flag is required to stop tracking a folder because the `rm` has to be applied to all files inside the folder recursively.

```none
git rm -r --cached <folder_name>
```

**_Note_**

The change will become effective on the next commit.

### 16. `git reset`

---

Move the tip of current branch (`HEAD`) back to previous commit, i.e. reset latest commit.

**_Command_**

```none
git reset --hard HEAD^
```

**_Note_**

It will also remove the latest commit from history as if it does not exist.

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

### 17. `git rebase`

---

Merge the last `x` commits into a single commit.

**_Command_**

```none
git rebase --interactive HEAD~x
```

or

```none
git rebase -i HEAD~x
```

`x` is the number of commits. `HEAD~3` means the last three commits, started from `HEAD`.

**_Example_**

```none
git rebase --interactive HEAD~5
```

Before

```none
cccccc latest   -----.
bbbbbb commit B      |
aaaaaa commit A      |-- merge into a single commit
999999 commit 9      |
888888 commit 8 -----'
777777 good commit
```

After

```none
dddddd revised
777777 good commit
```

**_Note_**

> `git rebase` will create a new hash

### 18. `git tag`

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

### 19. `git show`

---

1. Get file from specific commit and overwrite the current file. The `FILE_PATH` is relative to the repository root.

   **_Command_**

   ```none
   git show <OLD_COMMIT_HASH>:<FILE_PATH> > <FILE_PATH>
   ```

   **_Example_**

   Get file `src/routes/product.js` from old commit hash `a1b2c3d4e` and overwrite the latest one.

   ```none
   git show a1b2c3d4e:src/routes/product.js > src/routes/product.js
   ```

2. Show details of the most recent commit (`HEAD`)

   **_Command_**

   ```none
   git show HEAD
   ```

### 20. `git diff`

---

1. Check the difference between working directory and last commit

   ```none
   git diff
   ```
