# CAA-900-AzureProject


# Checkpoint3 Submission

- **COURSE INFORMATION: CAA900ZAA**
- **STUDENT’S NAME: Isaiah Cyrus Majam**
- **STUDENT'S NUMBER: 129325239**
- **GITHUB USER_ID: 129325239-mysenecaa**
- **TEACHER’S NAME: Atoosa Nasiri**


## Table of Contents
1. [Part A - Manage Conflicts - Overwrite Remote Changes](#header)
2. [Part B - Inspecting Local Repo with `git status` and `git log`](#header)
3. [Part C - Creating & Merging Branches](#header)
4. [Part D - Git Branching Strategy Review Question](#header)


### Part A - Manage Conflicts - Overwrite Remote Changes

part1-conflict-error.log
```log
Pushing to https://github.com/129325239-mysenecaa/CAA-900-AzureProject.git
To https://github.com/129325239-mysenecaa/CAA-900-AzureProject.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/129325239-mysenecaa/CAA-900-AzureProject.git'
hint: Updates were rejected because the remote contains work that you do not
hint: have locally. This is usually caused by another repository pushing to
hint: the same ref. If you want to integrate the remote changes, use
hint: 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

part1-conflict-overwrite.log
```log
POST git-receive-pack (6931 bytes)
Pushing to https://github.com/129325239-mysenecaa/CAA-900-AzureProject.git
To https://github.com/129325239-mysenecaa/CAA-900-AzureProject.git
 + e3f6734...62cc2ba main -> main (forced update)
updating local tracking ref 'refs/remotes/origin/main'
```