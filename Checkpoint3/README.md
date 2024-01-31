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


### Part B - Manage Conflicts - Reset Local Commit Head

part2-conflict-error.log
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

part2-pull-error.log
```log
POST git-upload-pack (196 bytes)
POST git-upload-pack (483 bytes)
From https://github.com/129325239-mysenecaa/CAA-900-AzureProject
   950a4b7..4ef9845  main        -> origin/main
 = [up to date]      dummy       -> origin/dummy
 = [up to date]      feat-emojis -> origin/feat-emojis
Updating 950a4b7..4ef9845
Fast-forward
 Checkpoint3/conflict-resolution/index.html | 4 ++--
 1 file changed, 2 insertions(+), 2 deletions(-)
```

part2-reset-head.log
```log
HEAD is now at 950a4b7 cp3-part1 update
```

