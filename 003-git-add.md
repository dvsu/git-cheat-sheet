# `git add`

[Git Cheat Sheet](./README.md) / git add

---

1. Add a file to staging area

   **_Command_**

   ```none
   git add <FILE_NAME>
   ```

2. Add multiple files to staging area

   **_Command_**

   ```none
   git add <FILE_1> <FILE_2>
   ```

3. Add all files and directories, relative to current working directory, to staging area

   **_Command_**

   ```none
   git add .
   ```

   **_Example_**

   Assume a git repo contains the following files and directories and all of them are untracked.

   ```none
   my-repo
      │
      ├─ alpha
      │    ├─ alpha-1.txt
      │    ├─ alpha-2.txt
      │    └─ alpha-3.txt
      ├─ bravo
      │    ├─ bravo-1.txt
      │    ├─ bravo-1.txt
      │    └─ bravo-3.txt
      ├─ charlie
      └─ zulu.txt

   ```

   If you change directory to `alpha`

   ```none
   cd alpha
   ```

   and add all files and directories to staging area

   ```none
   git add .
   ```

   The only files that are in staging area are `alpha-1.txt`, `alpha-2.txt`, and `alpha-3.txt` because `.` is relative to the current working directory, `/my-repo/alpha`
