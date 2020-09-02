# Git Info

- [Git Clone](#Git-Clone)
- [Git Init](#Git-Init)
- [Git Add](#Git-Add)
- [Git Commit](#Git-Commit)
- [Git Status](#Git-Status)
- [Git Log](#Git-Log)
- [Git Branching](#Git-Branching)
- [Git Checkout](#Git-Checkout)
- [Git Clean](#Git-Clean)
- [Git Pull-a](#Git-Pull)
- [Git Push](#Git-Push)
- [Github SSH](#Github-ssh)
- [Git Diff](#Git-Diff)
- [Git Remote](#Git-Remote)
- [Git Branching](#Git-Branching)
- [Git FF Merge](#Git-FF-Merge)
- [Git 3-way Merge](#Git-3-Way-Merge)
- [Git 3-way Merge Conflicts](#Git-3-Way-Merge-Conflicts)
- [Git Combine commits](#Git-Combine-Commits)
- [Git Rebase](#Git-Rebase)
- [Git Rebase with conflict](#Git-Rebase-with-conflict)
- [Git Fetch](#Git-Fetch)
- [Git Pull-b](#Git-Pull)
- [Git Pull Rebase](#Git-Pull-Rebase)
- [Git Tags](#Git-Tags)
- [Git Stash](#Git-Stash)
- [Git Usage](#Git-Usage)
- [Beyond Compare setup](#Beyond-Compare-Mergetool)

***TODO: Add project to Github

> Creating a new file in the project folder puts the new file into an untracked git status

## Git Clone

`git clone https://github.optum.com/BOS/<ProjectName>`
> Pulls down a project from github to the current folder

- [Top](#Git-Info)

## Git Init

> Creates a local git repository for the current folder structure

- [Top](#Git-Info)

## Git Add

`git add [filename]`

> Adds [filename] to the local git (.git folder) repository. The file is then in a staged git status. You may add the file multiple times to store off incremental states of the file.

- [Top](#Git-Info)

## Git Commit

`git commit -m "message IE reason for the commit"`
> Commits changes into the local repository

`git commit -am "commit Message"`

> Adds the uncommitted file and commits with the commit message

- [Top](#Git-Info)

## Git Status

`git status -s`

> Displays the status of un-committed files in the current folder

- [Top](#Git-Info)

## Git Log

`git log'

> displays the verbose log of all git commits

`git log --oneline`

> displays the simple log of all git commits

`git log <filename>`
> displays the verbose log of all git commits for the specified filename

`git log -n 3 --oneline`

> Displays the 3 most recent commits

- [Top](#Git-Info)

## Git Branching

> Branching is a way to request a new work area / working directory

`git branch`
> Displays the branches of the project

`git branch <branchName>`
> Creates a new branch. The new branch will inherit all of the commits from the master branch.
Create branches when you want to develop a new feature or bug fix. Unstable code is never committed to the main production code base. Each branch gets it's own working directory, staging area, and commit history.

`git branch -a`
> Displays all local and remote branches.

`git branch -m <OriginalBranch> <NewBranchName>`
> -m option means modify. The above command will rename a branch.

`git branch -d <BranchNameToDelete>`

> -d option means delete.

```Git
git branch <branchName> [BranchToCreateNewBranchFrom]
git checkout <branchName>
  Make changes to the branch
git add .
git commit -m "commit message"
git branch -d <branchName>
git branch -D <branchName>

git checkout -b <branchName>
```

1. Creates the branch [branchName] Optionally you can create a new branch from another branch
2. Changes the working folder to the branch folder
3. Adds the change to the git staging area
4. Commits the change to the local branch
5. This throws an error because git doesn't want you to lose the changes
6. This (capital D) forces the deletion of the branch

\* Creates new branch and checks it out

- [Top](#Git-Info)

## Git Checkout

`git checkout <BranchName>`
> Moves to the git [branchName] branch

```Git
git init
  Creates .git folder (git master branch). However, the branch doesn't have any files in it.

git add .
  Adds the files in the current folder structure to the current git staging area.

git commit -m "commit message"
  commits the files in the staging area to the git repository.

git commit -am "commit message"
  adds the changed file(s) to the current branch along with the commit message.
```

`git checkout <branch Id>`
> Brings the version of the files from the branch ID into the current folder
>> this is know as a detached-head status

`git checkout master`
> Returns files to the master branch version(s). However, if you made changes
and committed them while in the earlier branch, they are not in the master
branch. If those changes need to be kept, create a new branch with: `git branch <new-branch-name> <branch ID>`

- [Top](#Git-Info)

## Git Reset

`git reset <filename>`

> Resets the file from an added status in the repository back to a modified status [filename] is still modified in the working directory

`git reset`
> Resets all files from an added status in the repository back to a modified status files are still modified in the working directory

`git reset --hard`
> Resets all files from the repository back to the master state

- [Top](#Git-Info)

## Git Clean

`git clean -n`
> This displays of list of files that would be removed if you re-run the command without the -n option

`git clean -f`
> Force removal of untracked files from your working folder. Files in your .gitIgnore file are not affected by this. **This is not un-doable!**

`git clean -df`
> Force removal of untracked files from your working folder and sub-folders. Files in your .gitIgnore file are not affected by this. **This is not un-doable!**

`git clean -xf`
> Force removal of untracked files from your working folder and sub-folders. Files in your .gitIgnore file **ARE** affected by this. **This is not un-doable!**

- [Top](#Git-Info)

## Git Pull-a

`git pull origin master`
> Allows developer to sync with remote repository to see what others have contributed. You should ALWAYS issue a git pull before doing a push to make sure you will not overwrite something that someone else has done.

- [Top](#Git-Info)

## Git Push

`git push origin master`
> Pushes local changes (master) to the remote (origin) repository. If someone else has made any changes and pushed them, your push will be rejected. If this occurs, you need to do a pull first.

- [Top](#Git-Info)

## Github ssh

> Keys are usually stored in the users home directory (c:\Users\MSID). They could also be in the .ssh sub-folder.
> **Use the GitBash shell for the ssh-keygenand ssh-agent applications**

`ssh-keygen -t rsa -b 4096 -C "Comment-key pair purpose"`

1. -t option is generally the key type. It can be DSA or RSA. RSA is more secure
2. -b option is the key byte length. Longer lengths are more secure, but at a cost of decryption time
3. -C option is the reason for the key pair

> The ssh-keygen application will ask you for the key name. It will default to id_rsa. It will also request a passphrase. You may enter a passphrase to make the key pair more secure, but you must remember the passphrase.

`eval "$(ssh-agent-s)"`

> Starts the ssh agent so you may add the public key to the agent

`ssh-add ~/.ssh/id_rsa.pub`

> adds the id_rsa.pub key to the agent. It will ask for the passphrase you may have entered when creating the key pair. You can edit the id_rsa.pub file to get the public key. Copy the entire file contents to the clipboard and then go into github, user settings and add the SSH key.

`ssh -T git@ssh.github.com`

> Switches the git connections from HTTPS to SSH

`git remote -v`

> Displays the connection type SSL:
```(git@github.com:<userid>/repository) or HTTPS (https://github.com/<userid>/repository)```

`git remote set-url origin https://github.com/<userid>/repository`

> Switches the git connections back to HTTPS

`ssh-keygen -p`

> Changes the passphrase within the key pair. It will ask for the filename and the passphrase twice. When using SSH communication with github and the key has a passphrase, you will be asked to provide the passprase when pushing to the github repository.

*** I see no need to create and use SSL connections.

- [Top](#Git-Info)

## Git Diff

`git diff`

> Displays the file differences between the working folder file(s) and those that have been added to the staging area. Udemy git course reccomends using Perforce Helix Visual Client (available from appstore.uhc.com) for viewing differences between the various states of the file(s).

`git diff HEAD`

> Displays the difference(s) between the local working directory and the last commit.

`git diff --staged HEAD`

> Displays the difference(s) between the the staged area (git add) and the last commit. It will not display differences between the local working  directory and the staged area.

- [Top](#Git-Info)

## Git Remote

`git remote -v`
> view the remote repository

Create remote repository using site GUI and copy the remote repository URL

`git remote add origin <remoteURL>`

> Links the current working folder to the remote repository

`git push origin master`

> Pushes the current working folder to the remote repository

`git diff master origin/master`

> Compares the differences between the local git repository and the
remote repository

`git checkout -b BranchName`

> Creates the feature branch from the master branch

Make changes to the branch and commit the changes

`git checkout master`

> Switch back to the master branch

`git diff FeatureBranch master`

> Compare the feature branch against the master branch

`git log --oneline --decorate --graph --all`

> Displays additional information regarding branches, merges, etc.

`git checkout FeatureBranch`

`git log --oneline --decorate --graph`

> Displays extra information about the current branch

`git log --stat`

> Detailed information about each individual commit of each file including details of lines that were changed.

`git log -p --oneline -n 1`

> -p option displays the most details of a commit -n 1 limits the number of commits to 1

`git log --oneline <folder>`

> Displays changes related ONLY the folder identified.

`git log --oneline --grep="search"`

> Displays commits that contain the search expression.

- [Top](#Git-Info)

## Git FF-Merge

> Before doing a merge you should do a diff to see what will be merged

`git checkout -b <branchName>`

`git merge <SourceBranchToMergeIntoMaster>`

> Merges the branch into Master. However, it won't work if there are other changes to Master since this branch was created. Once the branch has been merged into Master, it can be deleted.

- [Top](#Git-Info)

## Git No-FF-Merge

```Git
git checkout -b <branchName>
Make changes to branch
git checkout master
git merge <branchName> --no-ff
git branch -d <branchName>
git log --oneline --decorate --graph
```

> The -no-ff option will preserve within the master branch the git ID's that were part of the merged branch

- [Top](#Git-Info)

## Git 3-Way-Merge

> 3 way merge is also know as an automatic-merge.

```Git
C1---C2---\---C3---C4 ---C4+B2
           ---B1---B2/

git checkout -b 3wm
Make changes to 3wm
Commit changes to 3wm (git commit -am "B1")
Additional changes to 3wm
Commit changes to 3wm (git commit -am "B2")
git checkout master
Make changes to Master
Commit change to Master (git commit -am "C3")
Make changes to Master
Commit change to Master (git commit -am "C4")
git merge 3wm -m "merging B2+C4"

```

> This works well when C commits are against different files from the B commits in the 3wm branch.

- [Top](#Git-Info)

## Git 3-Way-Merge conflicts

```Git
git checkout -b <featureAbranch>
modify file-A
git commit -am "File A modification in feature A branch"
git checkout master
modify file-A
git commit -am "File A modification in Master"
git log --oneline --decorate --graph --all
git diff master featureAbranch
git merge featureAbranch
-- conflict errors will be displayed
modify file-A (will contain code changes from both master and featureAbranch with <<<< and >>>> indicators to show you where the conflicts are)
-- P4Merge (available from appstore.uhc.com) is a very nice tool for use within git for viewing and resolving merge conflicts

make corrections to resolve conflicts

git commit -am "Message for what was resolved"

```Git
> Resolve merge conflicts

- [Top](#Git-Info)

## Git Combine Commits

```Git
modify file
git commit -am "Commit Message
modify file
git add <filename>
git commit --amend
```

> This will replace an entire previous commit with recent changes or to amend the commit message

### NEVER AMEND COMMITS TO THE REPOSITORY

- [Top](#Git-Info)

## Git Rebase

`git rebase <BASE>`

> BASE can be an ID, BranchName, Tag or a relative reference to HEAD

```Git
C1-->C2-->\-->C3-->C4
            -->B1-->B2

Rebase basically takes the C4 commit of Master and applies B1 and B2 commits to it creating new commits K1 and K2

C1-->C2-->C3-->C4-\
                   -->K1-->K2
```

```Git
git init
modify file1
git commit -am "master: file1 change"
git checkout -b <branchName> -- creates new branch and moves to that branch
modify file2
git commit -am "<branchName>: file2 change"
git checkout master -- moves back to master branch
modify file3
git commit -am "master: file3 change"
git log --online --decorate --graph --all
------------------------------------
*4444444 file3 change
| *3333333 file2 change
|/
*2222222 master: file1 change
*1111111 repository setup
```

![Image](./GitRebasePrep.jpg)

```Git
git checkout <branchName>  -- move to the feature branch
git rebase master -- applies feature updates to master branch
*3333333 (master) master: file3 change
*4444444 master: file2 change
*2222222 master: file1 change
*1111111 repository setup
```

![Image](./GitAfterRebase.jpg)

```Git
git checkout master  -- switch to master branch
git merge <branchName> -- merges <branchName> commits to master
git branch -d <branchName> -- now that <branchName> is in master you delete the branch
```

- [Top](#Git-Info)

## Git Rebase with conflict

```Git
git checkout master
modify file1
git commit -am "master: change to file1"
git checkout -b Conflict -- New branch and moves to it
modify file1 -- change line in file1 that was also modified before the checkout
git commit -am "conflicting change to file1"
git rebase master
-----Error will be displayed
git mergetool  // screen shot using P4Merge app
```

![Image](./GitMergeConflict.jpg)

Once merge conflicts have been resolved:

```Git
git rebase --continue
git checkout master
git merge <Conflict>
git branch -d <Conflict>  // remove the Conflict branch
```

Or to abort the conflicts:
`git rebase --abort`

## Simulate merge conflict

```Git
git checkout -b featureBranch
modify test.txt lines 1-3 changes
git commit -am "modified test.txt lines 1-3 for featureBranch"
git checkout master
modify test.txt lines 1-3 changes with different text
git commit -am "modified test.txt lines 1-3 for master Branch"
git log --oneline origin/master --decorate --graph --all
git difftool master featureBranch // view differnces
git merge featureBranch
// conflict message!
git mergetool
```

- [Top](#Git-Info)

## Git Fetch

> Git Fetch is used to sync the origin/master (local) branch with the remote repository

`git log --oneline origin/master`
> displays the local master branch
>> In demo the github project has 2 newer commits than the local project
![Image](./GitHubWithNewerCommits.jpg)

`git fetch`
> retrieves the commits from the remote repository
>> `git fetch origin master`
>> use this if you have multiple repositories

`git log --oneline origin/master --decorate --graph --all`
> will display all of the local master branch items including the newly retrieved items from the repository
![Image](./LocalMasterWithNewerCommitsNotMerged.jpg)
> This shows that the HEAD is behind origin/master

`git branch -r`
> Displays the remote repository branch

`git branch -a`
> Displays the remote and local branches

`git merge origin/master`
> Does a fast forward merge
![Image](./AfterFFMerge.jpg)

1) Do a fetch before you start your day's work
2) Do a fetch before you push to remote repository
3) Fetch often to stay in sync as much as possible

- [Top](#Git-Info)

## Git Pull-b

> Remember that Git keeps a copy of your local master branch and the repository master branch.

`git fetch`
> Brings the local copy of the remote repository up to date.

`git pull`
> git pull fetches the latest changes of the current branch from a remote and applies those changes to your local copy of the branch. Generally this is done by merging, i.e. the local changes are merged into the remote changes. So git pull is similar to git fetch & git merge.

Create a github repository
`git remote add origin <remoteRepositoryURL>`
> Links the current directory with the github remote repository

`git remote -v`
> Displays the repositories

`git push -u origin master`
> Pushes the contents of the local directory to the remote repository.

```Git
make change to file1
commit change
make change to file1
commit change
Co-worker makes a change to file2, commits change and uploads to github
Co-worker makes another change to file2, commits change and uploads to github
```

`git pull origin master`
> Enter a merge message describing why the pull was done.

`git log --oneline --decorate --graph --all`
> Displays the commits after the pull
![Image](./BeforeAndAfterPull.jpg)

- [Top](#Git-Info)

## Git Pull Rebase

Create a github repository

`git remote add origin <remoteRepositoryURL>`
> Links the current directory with the github remote repository

`git remote -v`
> Displays the repositories

`git push -u origin master`
> Pushes the contents of the local directory to the remote repository.

```Git
make change to file1
commit change
make change to file1
commit change
Co-worker makes a change to file2, commits change and uploads to github
Co-worker makes another change to file2, commits change and uploads to github
```

`git pull --rebase origin master`
> Enter a merge message describing why the pull was done.

`git log --oneline --decorate --graph --all`
> Displays the commits after the pull
![Image](./BeforeAndAfterPullWithRebase.jpg)

```Git
git pull and git pull --rebase are not interchangeable, but they are closely connected.

git pull fetches the latest changes of the current branch from a remote and applies those changes to your local copy of the branch. Generally this is done by merging, i.e. the local changes are merged into the remote changes. So git pull is similar to git fetch & git merge.

Rebasing is an alternative to merging. Instead of creating a new commit that combines the two branches, it moves the commits of one of the branches on top of the other.

You can pull using rebase instead of merge (git pull --rebase). The local changes you made will be rebased on top of the remote changes, instead of being merged with the remote changes.

https://www.atlassian.com/git/tutorials/merging-vs-rebasing
```

- [Top](#Git-Info)

## Git tags

## Tags are a way of noting specific points of your project beyond a commit message. There are lightweight, annotated and signed tags. Lightweight tags are generally used for local commits. Annotated tags are generally used for tagging the remote repository with information like specific milestones like alpha, beta, etc. Annotated tags also add meta data of who created the tag and when. Signed tags have a higher level of security and probably isn't needed

`git tag <tagName>`
> Creates a tag at the current commit. This is useful for noting when something significant occurs such as release builds.

`git tag -a <tagName> -m "tag message"`
> Creates an annotated tag which includes more information in the git database

- [Top](#Git-Info)

## Git Stash

## Git Stash is used to stash away uncommitted work so you can work on something like a criticle defect and return back to what you were originally working on

```Git
git stash
git stash list
git stash save "message to help identify the stash state / reason"
git stash -u
```

> Stashes the current working status of the project and returns you to the original master branch. Now you can create a new "hotfix" branch 'git checkout -b hotfix' to work on the hotfix. Use the save with message option! Stashes work on a last in first out (LIFO) model

## git stash only works on tracked (added) files. Use 'git stash -u' to stash new files that haven't been added to git

```Git
work on current project in progress
git stash save "work before hotfix w/current project state1"
git checkout -b hotfix
fix issue 1
git commit -am "issue 1 fix"
git checkout master
more current project work
git stash save "work before hotfix w/current project state2"
git checkout -b hotfix
fix issue 2
git commit -am "issue 2 fix"
git checkout master
more current project work
git stash save "work before hotfix w/current project state3"
git checkout -b hotfix
fix issue 3
git commit -am "issue 3 fix"
git checkout master
git stash apply  //Brings stash@{0} back into project
git commit -am "commit work saved from Stash state3"
git stash drop // drops the work in stash@{0}
git stash list // shows the list of remaining stashes
git stash pop // Brings stash@{0} back into project and removes from the stash list
git commit -am "commit work saved from Stash state2"
git stash clear // removes all stashes

git stash -u // creates a stash for tracked and untracked files
git stash branch <branchName> // creates a branch from all items in the stash and drops the stash. Any untracked files in the stash need to be committed to the branch.
git checkout master // switch to master for merging
git merge <branchName>
```

- [Top](#Git-Info)

## Git Usage

```Git
git status -s
Create file blah.txt
git status -s
  Status:  ?? blah.txt
git add blah.txt
  Status:  A blah.txt
git commit -m "commit message"
  Status:  (blah.txt not displayed as it is committed)
edit blah.txt and save
git status -s
  Status:   M blah.txt (Red M right aligned means modified, but not updated to local branch)
git add blah.txt
  Status:  M  blah.txt (Green M left aligned means modified and added to local branch)
git commit -m "commit message"
  Status:  (blah.txt not displayed as it is committed to the master branch)
rename blah.txt blah2.txt
git status -s
  Status:   D blah.txt (Red D right aligned means deleted, but not in the local branch)
  Status:  ?? blah.txt (?? means not in local or master branch)

edit, commit1, edit commit2, edit commit3, edit commit4, need to revert back to commit2

git log --oneline

To get list of commits with identifiers
git checkout <identifier of commit2>
```

- [Top](#Git-Info)

## Git bash Configuration

> Edit the .bashrc file located at: c:\\users\\MSID\\ and paste the following into the file. This will configure git bash to have customized colors and git status in the prompt.

```Git
parse_git_branch() {
git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u \W\[\033[32m\]$(parse_git_branch)\[\033[00m\] $ "
cd "C:\Users\jtrusty\Documents\Projects"
```

- [Top](#Git-Info)

## Beyond Compare Mergetool

Per article at: `https://gist.github.com/RohanBhanderi/2b20592048f6b67368a7`

```Git
//Git Mergetool and difftool with Beyond Compare 4
//For Windows
//IF running this command in git bash then escape $ with \
git config --global diff.tool bc4
git config --global difftool.bc4.cmd "\"C:/Program Files (x86)/Beyond Compare 4/BCompare.exe\" \"\$LOCAL\" \"\$REMOTE\""
git config --global difftool.prompt false

git config --global merge.tool bc4
git config --global mergetool.bc4.cmd "\"C:/Program Files (x86)/Beyond Compare 4/BCompare.exe\" \"\$LOCAL\" \"\$REMOTE\" \"\$BASE\" \"\$MERGED\""
git config --global mergetool.bc4.trustExitCode true

```

- [Top](#Git-Info)

## VS Code usage

## There are 2 ways to begin a project for use in VS Code and Git. Both require you to create a project in GitHub

1) Start a project in GitHub
  \* `https://www.youtube.com/watch?v=9cMWR-EGFuY`
2) Use an existing project folder
  \* `https://youtu.be/I7WfxhF2wEg`

```Git
1)
Create GitHub repository
Go into the repository and copy the repository URL
Open VS Code in the folder for your project
In command pallet type: git clone
  You will be asked for the repository URL, paste it in.
  You will be asked for the local project folder

2)
Create GitHub repository (copy the git remote command into clipboard)
Open project folder in VS Code
Open terminal
enter the following commands:
  git init
  git remote add origin <URL> (or paste git remote from clipboard)
  git push -u origin master
```

- [Top](#Git-Info)
