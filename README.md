
## Short manual

### Working with Branch

#### Show current branch and local branches
```
$ git branch
```

### Create local branch
```
$ git branch branchname
```

### Create local branch and checkout to new branch
```
$ git checkout -b branchname
```

### Delete local branch
```
$ git branch -d branchname
```

#### Merge current branch with another branch
```
$ git merge another-branch
```

### Working with Commit

#### Stage all changes
```
$ git add --all
# or
$ git add .
```

#### Add exact file to staging
```
$ git add LICENSE.txt
```

#### Commit change to current branch
```
$ git commit -m "comment with clear definition what is done"
```

#### Revert change to some commit
```
$ git reset --hard c1255e111673f80d244587b41784da1b5557a8fd // commit id
$ git push -f // don't try force push if you do not understand the logic
```

### Working with remote repository

#### Push commit remote repo
```
$ git push origin branch
```

#### Pull update from remote repo
```
$ git pull origin branch
```

#### Delete remote branch
```
$ git push origin --delete branchname
```

## GitFlow

### Branch Tree example

![Git Flow Example](https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%20(2).svg?cdnVersion=jo)

### Live circle for the Git Flow
```
1) Initialize repo with new branch "master". This branch hold the stable version of software. 
2) Create branch "dev" from the "master" branch for active development
3) Create another branch for some task [bug, feature, release, hotfix] from the "develop" 
4) If task on another branch [bug, feature, release, hotfix] completed merge task branch to the develop
5) If realease completed create new branch "release 1" from the develop
6) If realease code from "release 1" published than you need to merge "release 1" to "master"
7) If your need create hotfix to release branch you should merge thіs hotfix to the develop branch
8) Repeat step 2-7 if you have a new release
9) If your published branch "release n" and the release fail your need publish stable code from the master branch
```

### Branch Rule
```
# [folder] - bug, feature, release, hotfix
# [task-id] - task from jira (for e.g. DUED-64)
# [task-alias] - short alias of the task from jira for quick navigation through branches
$ git branch [folder]/[task-id]__[task-alias]

Example:
hotfix/questionnaire_user_assign
feature/dued-123__implement_crud_for_questionnaire
```

### Create Pull Request Rule
```
# [folder] - Bug, Feature, Release, Hotfix
# [task-id] - task from jira (for e.g. DUED-64)
# [task-name] - full task name copied from jira

Title following the next snippet:
[folder]. [task-id] [task-name]

Example Title:
"Feature. DUED-994 Notification user assign."
"Hotfix. Questionnaire user assign."

Comment following the next snippet:
Short description should be provided as well
Insert link to the task in Jira if it possible

Create a pull request.
```

### Merge Pull Request Rule
```
# [folder] - Bug, Feature, Release, Hotfix
# [task-id] - task from jira (for e.g. DUED-64)
# [task-name] - full task name copied from jira
# [hash-tag] - hash tag\link for pull request (for e.g. (#135))

Title following the next snippet:
[folder]. [task-id] [task-name] [hash-tag]

Example Title:
"Feature. DUED-994 Notification user assign. (#135)"
"Hotfix. Questionnaire user assign. (#136)"

Comment following the next snippet:
* Some update
* Some fix
* Short feature or task detail 

Insert link to the task in Jira if it possible

Example:
"* Bound notifications and questionnaire user assign id.

https://duediliger.atlassian.net/browse/DUED-994"

Merge pull request to develop selecting method "Squash and merge".
```

### Full working process with branch and pull request:
```
1. Create new branch from developer branch
2. Swich branch to him
3. Work with this branch. 
4. If you finish some features pull changes from develop branch 
5. Merge your branch with develop branch and fix all conflicts
5. Create Pull Request to the develop branch
6. Read fedback for you code quality. And tell about why you develop some way.  
7. If neded fix problem create new commit and repeat step 5)
8. After push to the develop branch system automatically will create a build on the CI Server
```

### Gitflow Workflow With Pull Requests

![](https://wac-cdn.atlassian.com/dam/jcr:a5c54fd9-09d7-4f59-90c1-8b228fec80a5/06.svg?cdnVersion=jo)

## How we worked with git repository
1. Admin/Tech lead creates repository
2. Tech lead creates base branch infrastructure master, develop, testing
3. Tech lead setup security protection to the branch master, develop
4. Tech lead invited team and should provide two-factor authorization with all the team
5. Tech lead should provide access to the repository via ssh key
6. Tech lead give access to the develop branch to responsible people for code review
7. Team working with GitFlow and pull requests

## Articles. Be sure to get acquainted

[Base Configuration](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

[Software. Git GUI Clients](https://git-scm.com/download/gui/windows)

[Learn Git. Atlassian manual](https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud)

[Short PDF manual](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)

[Connecting to GitHub with SSH](https://help.github.com/articles/connecting-to-github-with-ssh/)
