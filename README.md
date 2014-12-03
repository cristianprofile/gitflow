GITFLOW TESTING PROJECT
=======

Testing git flow commands to order branches flow, with several branches using labels to
mark several release version on master's branch.

See:  https://github.com/nvie/gitflow/wiki/Command-Line-Arguments
      http://blogs.endjin.com/2013/04/a-step-by-step-guide-to-using-gitflow-with-teamcity-part-3-gitflow-commands/


GITFLOW COMMANDS AND EQUIVALENT GIT COMMAND
=======

Gitflow commands to use this workflow in a Git Repository and equivalent git command launched. 


## Initialize

gitflow | git
--------|-----
`git flow init` | `git init`
 | `git commit --allow-empty -m "Initial commit"`
 | `git checkout -b develop master`


## Connect to the remote repository

gitflow | git
--------|-----
_N/A_ | `git remote add origin git@github.com:MYACCOUNT/MYREPO`


## Features

### Create a feature branch

gitflow | git
--------|-----
`git flow feature start MYFEATURE` | `git checkout -b feature/MYFEATURE develop`


### Share a feature branch

gitflow | git
--------|-----
`git flow feature publish MYFEATURE` | `git checkout feature/MYFEATURE`
 | `git push origin feature/MYFEATURE`
 
Once you’ve published the feature your team mates will be able to work on the feature branch with you by cloning the Repository from the centralized Repository and then doing a “git flow init”.  This will set them up to have a Gitflow enabled local Repository with a master and a develop branch.  Once they have a Gitflow enabled Repository they should be in the develop branch on which they should now do a pull to ensure their local Repository is in sync with the one on the remote.  Once this is complete they should be able to follow it.


### get a branch created  shared remote repository

git flow feature track <name>


### Get latest for a feature branch remote repository

gitflow | git
--------|-----
`git flow feature pull origin MYFEATURE` | `git checkout feature/MYFEATURE`
 | `git pull --rebase origin feature/MYFEATURE`
 
 
 ### Push for a feature branch remote repository
(Note: without gitflow command, )

 git checkout feature/myfeature (only if you are out of feature branch)
 git push


### Finalize a feature branch

gitflow | git
--------|-----
`git flow feature finish MYFEATURE` | `git checkout develop`
 | `git merge --no-ff feature/MYFEATURE`
 | `git branch -d feature/MYFEATURE`


### Push the merged feature branch

gitflow | git
--------|-----
_N/A_ | `git push origin develop`
 | `git push origin :feature/MYFEATURE` _(if pushed)_


## Releases

### Create a release branch

gitflow | git
--------|-----
`git flow release start 1.2.0` | `git checkout -b release/1.2.0 develop`


### Share a release branch

gitflow | git
--------|-----
`git flow release publish 1.2.0` | `git checkout release/1.2.0`
 | `git push origin release/1.2.0`


###Start tracking release

Start tracking release <name> that is shared on $ORIGIN

git flow release track <name>


### Get latest for a release branch

gitflow | git
--------|-----
_N/A_ | `git checkout release/1.2.0`
 | `git pull --rebase origin release/1.2.0`

 ### Push for a feature branch remote repository
(Note: without gitflow command, )

 git checkout release/myrelease (only if you are out of relase branch)
 git push


### Finalize a release branch

gitflow | git
--------|-----
`git flow release finish 1.2.0` | `git checkout master`
 | `git merge --no-ff release/1.2.0`
 | `git tag -a 1.2.0`
 | `git checkout develop`
 | `git merge --no-ff release/1.2.0`
 | `git branch -d release/1.2.0`


### Push the merged feature branch

gitflow | git
--------|-----
_N/A_ | `git push origin master`
 | `git push origin develop`
 | `git push origin --tags`
 | `git push origin :release/1.2.0` _(if pushed)_


## Hotfixes

### Create a hotfix branch

gitflow | git
--------|-----
`git flow hotfix start 1.2.1 [commit]` | `git checkout -b hotfix/1.2.1 [commit]`


### Finalize a hotfix branch

gitflow | git
--------|-----
`git flow hotfix finish 1.2.1` | `git checkout master`
 | `git merge --no-ff hotfix/1.2.1`
 | `git tag -a 1.2.1`
 | `git checkout develop`
 | `git merge --no-ff hotfix/1.2.1`
 | `git branch -d hotfix/1.2.1`


### Push the merged hotfix branch

gitflow | git
--------|-----
_N/A_ | `git push origin master`
 | `git push origin develop`
 | `git push origin --tags`
 | `git push origin :hotfix/1.2.1` _(if pushed)_



## References

 - http://nvie.com/posts/a-successful-git-branching-model/
 - https://help.github.com/articles/using-pull-requests#shared-repository-model
 - Personal experience

