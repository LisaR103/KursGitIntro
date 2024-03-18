# How to use git

![Logic](https://github.com/LisaR103/KursGitIntro/blob/main/LogicOfGit.png)

1. create Repository online and clone into a folder where you want it

Open a terminal in the folder where you want the Repository to be and type:

	`git clone https://reponame.git`

per default the repository is created in a directory with the repository name. This can be modified by adding a name after the link, e.g. oldstate if I want to safe the current state of the remote depository again

	`git clone https://reponame.git oldstate`

2. check the status of the Staging Area:

	`git status`

This shows which files in the working directory of the repository are
- not tracked/tracked
- modified but not staged
- staged with/without further modifications
- whether the working directory is up to date with the remote directory
- where the head is (i.e. where in the repository I am, at the most current or at an earlier or branched version)

3. to add a file

	`git add file1 file2`

wildcards apply, e.g. *.txt etc to add several files at once
if the file is changed it needs to be added again

4. commit file = add it to LOCAL Repository

	`git commit -m "Describe the changes"`

5. look at all the changes that have happened in the LOCAL repository

	`git log`

leave `git log` by pressing q
the commit showing origin/main Head/main is where the remote repository is

6. push file = add it to the REMOTE Repository

	`git push`

username is my username
password is my token that I generated for this repository

If this doesn't work try deleting the safed token from the Schlüsselbundverwaltung:

- Open Keychain Access app.
- Search for github.com
- Delete the information of other users/repositories

![Keychain](https://github.com/LisaR103/KursGitIntro/blob/main/KeychainAccess.png)

I only have to put in the password 1x per session

7. pull file = update *from* remote repository

	`git pull`

8. getting back an old version after a mistake = going back to that commit

	`git checkout [commitnumber]`

everything I do now happens with the state of the files at this snapshot, but I can't commit these files
what I can do is copy it into the parent directory and later back in
to work on an "alternate version" create a branch, that you can then commit
to go back to the most current:

	`git checkout main`

9. gitignore

files that I don't want versioned because it is a waste of space and clusters the repository
e.g. pdf files/result files/temporary files/history files

I can add all of those file to a file called `.gitignore`

This is a text file without a file extension

content e.g.:
.*
!.gitignore

= ignore everything that starts with a `.` except `.gitignore` itself

10. turning a markdown file into a pdf file

	`pandoc -o file.pdf file.md`

## Branching

This is to have a "work in progress" save so you don't have to change the main

Create branch: `git checkout -b branchname` (if it doesn't exist)
Commit the branch: `git commit -m "descriptive message"`
Push the branch: `git push -u origin branchname`

It's important to do the push correctly so that the main (remote) and local have the head at the same place

Merge two branches (here branchname with master ):
`git checkout master`
`git merge branchname` (In case of conflict: Edit, commit)

## Tags
Adding a license in important!!! Even if it's just to have a liability statement
