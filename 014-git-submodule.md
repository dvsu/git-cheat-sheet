# `git submodule`

[Git Cheat Sheet](./README.md) / git submodule

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
