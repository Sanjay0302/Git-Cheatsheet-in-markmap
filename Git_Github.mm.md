---
markmap:
  colorFreezeLevel: 2
  maxWidth: 300
  initialExpandLevel: 1
---

# Git Github and MarkDown

## Installing Git

## Basic CLI Commands

- `git --version`
  - Check git version
- `whoami`
  - Get the current device name
- `pwd`
  - Print current DIR
- `ls`
  - list the element of current directory
- `cd`
  - Change Directory
- `mkdir`
  - New Folder
- `cd ..`
  - Previous directory
- `touch`
  - Create a new File with extension
  - touch filename.txt
- `echo`
  - To create a file with some text inside
  - echo This is example Text > filename.txt

## Git Configuration

- `git config --global user.name`
  - Configure User_Name
  - `git config --global user.name "USERNAME"`
- `git config --global user.email`
  - Configure User_Email
  - `git config --global user.email "EMAILADDRESS"`
- `git config --list`
  - To check all configuration in the device

## Initialise and Use of Git Folder

- check the current DIR using `pwd`
  then create folder using `mkdir`
  navigate to new folder using `cd` command
- `git init`
  - Initialise folder as Git folder
- then go on adding files

## tracked and Untracked Files

- Tracked Files are the files that are in stagging
- To check number of Untracked files use `git status`
- The files displayed in red are untracked files

## stagging a single file

- Use `git add`

  - To add file to stagging environment
  - To add single file use `git add FILENAME`
  - To add all Files use `git add .` or `git add --all` or `git add -A`
  - for Multiple files we can also do this `git add FileName1 FileName2` and so on

- Use `git restore FileName`
  - Use this after any changes in the file
  - And that file should not be tracked
    that means the file should not be stagged
  - after that if we want to restore to
    previous stagged file we use this command
    `git restore FileName`
  - To remove a file from Stagging environment
    `git rm --cached FileName`

## Git commit

- converting a file from staging environment to commit is called as `tracking process`
- And commits are the `save points` with `HASH`
- we do this so that we can go back to the versions during errors using codes (hashes)
- Each commit should contain a message to describe about the message
- `git commit -m "MESSAGE"`
- Then verify the commit is done or not using `git status`
- to see the status messages in short we use `git status --short`
  - We get `File Name` with `Flags`
  - if it is in red color then it is untracked file
  - `M` then the file is modified
  - `D` for deleted files
  - `A` for Added Files

## stage and commit in a single command

- `git comnmit -a -m "MESSAGE"`
- this method is not recommended
- since direct stage and commit might led to add
  unwanted error files without cross checking

## git help

- no need to remmember all the commands
  we have git help command for that
- `git <command_method> -help`
  - to get the command related to specific command method
  - for example to get commands related to commit
    we use `git commit -help` or `git add -help`
- `git help --all`
  - this is to get all the command_methods of git
  - select a command method to get command related to that
  - later to exit use `q`

## git branch

- Creating a copy of main branch without affecting it
- we can edit in that new branch and later we can merge the changes to main branch
- Command : `git branch Branch_Name`
  - The Branch is Created that's all
  - Later get list of all branch use `git branch`
  - To navigate to new branch use `git checkout Branch_Name`

## Changes in New Branch

- Navigate to Branch using `git checkout Branch_Name`
- Then Create files Inn that folder
- Then use `git status` and check for non tracked files]
- Use `git add --all` to add all files to stagging area
- Then use `git commit -m "MESSAGE"`
- if we try to go to master branch till changes will not be shown

## git Merge

- Navigate to destination branch and then use `git merge SOURCE_BRANCH`
- VERIFY THE MERGED DATA USING `ls` command

## git conflict

- for example if we have master and subbranch as to branch
- once we merge subbranch with master using `git merge subbranch` in master branch
- Then we use subbranch again and added something to subbranch again
- So then stagged and commited
- then if we use `git merge subbranch` again we get error
- to solve this conflict we use editor to edit and fix
- stage and commit changes

## delete branch

- use `git branch -d BRANCH_NAME`

## Link Github Repo With Local Repo

- create new repo in Github Website
- Copy the HTTP link for setting remote repo
- then go to local folder and open git bash then type this commands
  - `echo "# hello everyone" >> README.md`
  - `git init`
  - `git add README.md`
  - `git commit -m "first commit"`
  - `git branch -M master`
  - `git remote add origin <HTTPLINK>`
  - `git push -u origin master`
  - Or just use `git remote add origin <HTTPLINK>`
  - After linking to push all files using `git push --set-upstream origin BRANCH_NAME`

## Up to date with changes (Web to local)

- i.e what ever changes made in website should be pulled to local repo
- There are 2 ways to do that
  - First method is to use `Fetch + Merge` Method
  - Second method is to use `pull` method
- `Fetch + Merge` Method
  - `git fetch origin`
  - then `git status` we will get the message if we have anything to be changed in the github web
  - use `git log origin/master` to fetch the latest commit
  - use `git merge origin/master`
  - verify using `git status`
- `Pull` Method
  - After making changes in Github Web
  - come to git bash and use command `git pull origin`
  - then the local repo is up-to-date

## Up to date with changes (local to web)

- We use `Push` Coommand
- Make changes in local repo
- stage and commit
  - `git add --all`
  - `git commit -m "MESSAGE"`
  - `git status`
- then use `git push origin`

## To pull new branch to local folder

- after adding a new branch in github web
- come to git bash and do the pull using `git pull origin`
- Now the local folder is upto date
- then if we check `git branch` we wont see the new branch pulled
- For that we use `git branch -a`
- then to use that branch we use `git checkout BRANCH_NAME`

## Create branch locally and push

- `git checkout -b BRANCH_NAME`
  - create and navigate to the branch in single command
- then make changes -> stage -> check status -> commit
  - this changes are only in new branch
- to push the new changes `git push origin BRANCH_NAME`
- then we can also move the changes from one branch to another

## Go back to previous version

- First check the available commit `git log --oneline`
  - `--oneline` willl display the minimal info about the commits
- Then use `git reset HASH`
  - RESET command will help to go back to previous version using the hashes
  - where every commit has diffrent hashes
- Then commits after the specified point will be removed

## Parts ignored by git

- `.gitignore`
  - `ls`
  - `touch .gitignore`
  - if we try using `ls` the gitignore file will not be seen because it is a hidden file
  - this file helps in avoiding the files in local folder from being pushed to github
- In this file
  - We can add comment using `#`
  - to ignore file `*.extension`
    - for Example `*.txt` and `*.log`
  - to ignore folder we use `DIR_NAME/`

## two ways to collaborate with other `Dev`

- we have `fork` and `clone` methods
- `fork` is copy of repo
  - we can customise name and visibilty
- Then we can do clone
  - copy the http link
  - open local folder
  - use `git clone HTTPLINK`
  - we can get history of the project we can use `git log`
