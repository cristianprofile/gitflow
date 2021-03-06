Important!!!!!
Format of any commit message in a git project
https://github.com/erlang/otp/wiki/Writing-good-commit-messages





Example commit template message

Short (50 chars or less) summary of changes

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded by a
   single space, with blank lines in between, but conventions vary here

Close #4 (only if we want this commit close an issue when you merge this commit to your master branch)


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


### Get a branch created  shared remote repository

git flow feature track MYFEATURE


### Get latest for a feature branch remote repository

gitflow | git
--------|-----
`git flow feature pull origin MYFEATURE` | `git checkout feature/MYFEATURE`
 | `git pull --rebase origin feature/MYFEATURE (try only git pull --rebase) (remember when a pull is fired commands: fetch + merge)`
 
 
### Push for a feature branch remote repository
 
gitflow | git
--------|-----
N/A | `git checkout feature/myfeature (only if you are out of feature branch)`
 | `git push`


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

git flow release track 1.2.0


### Get latest for a release branch

gitflow | git
--------|-----
_N/A_ | `git checkout release/1.2.0`
 | `git pull --rebase origin release/1.2.0`
 
 (note that there is not any command to pull like on feature's branch)

### Push for a release branch (remote repository)
 
gitflow | git
--------|-----
N/A | `git checkout release/myrelease (only if you are out of feature branch)`
 | `git push`


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


### Change initial configuration of Gitflow

If you want to remap branch names in gitflow you have to do it via Git’s configuration file.

The config file is located in the .git folder of your repository:

/.git/config

Information about submodules and branches is saved to this file. And gitflow also creates a few entries.





## References

 - http://nvie.com/posts/a-successful-git-branching-model/
 - https://help.github.com/articles/using-pull-requests#shared-repository-model
 - Personal experience
