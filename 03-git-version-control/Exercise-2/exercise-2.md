## EXERCISE 2: .gitignore

You see that build folders and editor specific folders are in the repository and decide to ignore it as a
best practice.

Ignore .idea folder, .DS_Store, out and build folders

Hint: remove from git cache first

## Solution

In the Project root folder, I created a file named ``.gitignore``

In thi file i added the following lines

```
.idea/*
.DS_Store*
build/*

```
To remove the already cached .idea folder, i used the command

```
git rm -r --cached .idea 

```

I pushed the modified contents to my github repo

