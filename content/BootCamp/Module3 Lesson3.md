---
title: "Module3 Lesson3"
---
##### Previous Lesson
[Module2 Lesson3](Module3%20Lesson1.md)


# Using Git with Unity

**What are the problems?**

-   **Noise**: Unity editor has lots of temporary files that we don’t want git to track
-   **Broken object references**: Unity keeps track of objects created by using random GUIDs, and if they aren’t tracked using .meta files then there can be conflicts that really break your project
-   **Unresolvable merge conflicts**: files like scene files that are written in confusing languages (like YAML) that are supposed to be translations of Unity editor actions into code. Most likely, you cannot resolve using Git, and the only way to resolve merge conflicts is to open it in a text editor and resolve them manually while hoping you don't mess anything up because these files are confusing and not meant to be manipulated directly.
-   **Large files**: Sometimes assets are large and take up a lot of storage space



# Setting up a project

- Create Unity Project 

- Create blank Github repository

- Add a .gitignore file 
	- [gitignore/Unity.gitignore at main · github/gitignore](https://github.com/github/gitignore/blob/main/Unity.gitignore)

Navigate to  Project path
```bash
cd Documents/CircuitStream/GitProject
```


Initialize  git local repository
```bash

git init
```


Stage necessary  Unity files 
```bash

git add Assets

git add Project Settings

git add ProjectSettings

git add Packages 
 
git add -f .gitignore
```

Connect to blank remote repository on Github 
``` bash 
git remote add origin <https link>

git push -u origin main

git commit -m 'initial commit'
   
git push -u origin main
   

```

# Branches

create a new branch and checkout into it 
```bash
git checkout -b ＜new-branch-name＞
```

push new branch to remote
```bash
 git push -u origin Newranch
```


# Branches and Collaboration


# Collaboration

# Merging Pull Requests


```bash
git merge <branch_name>

git log --graph”
```

