# GitHubLab
This is a demo repository with supplemental lab exercises to learn about using Git and GitHub as part of a DevNet study group

## Git setup

### Install Software
If you have not already done so, you will need to install and configure Git. Installation is not covered in these labs but both Git and GitHub desktop software can be found for your platform at: 

https://windows.github.com

https://mac.github.com

### Create an Account on GitHub

https://github.com/signup

### Configure local settings
This will configure your local user info for all local repos on your personal system. This is required for code collboration and use of GitHub. 

Set the name you want attached to your commits

`git config --global user.name "[Name]"`

Set your email address for use with your commits and GitHub transactions (should match your GitHub account)

`git config --global user.email "[Email Address]"`

(Optionally) Enable helpful colorization of CLI Output. 

`git config --global color.ui auto`

## Working with an existing Repo
This example will show how to work with an existing GitHub repo, either yours or someone else's as long as it is public or you have permissions

Clone this repo (make an exact copy) to your local system. This will create a new subdirectory with the same name as the Repo. 

`git clone https://github.com/gnasses/GitHubLab.git`

Change directory into the newly created directory

`cd GitHubLab`

Show the repo status to confirm it cloned correctly, and that you are seeing the 'Main' branch

`git status`

You should see similar output to this: 

```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```


Now create a new branch to work with. This will not change any of the files, but identifies this in git as distinct work from 'main' which is the master copy. Choose a name for your branch that is easily related to the original repo to avoid confusion. 

`git branch GitHubLab-[yourname]`

