# GitHubLab
This is a demo repository with supplemental lab exercises to learn about using Git and GitHub as part of a DevNet study group

---

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

---

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

Create a new Branch of this local repo to work with. This will not change any of the files, but identifies this in git as distinct work from 'main' which is the master copy. Choose a name for your branch that is easily related to the original repo to avoid confusion. 

`git branch GitHubLab-[yourname]`

The checkout command switches to the new branch so you are working there

`git checkout GitHubLab-[yourname]`

Verify your current working branch

`git status`

Your output should look similar to this:

```
On branch GitHubLab-gnasses
nothing to commit, working tree clean
```
---

## Making, Tracking, and Saving Changes

Working in the new branch, create a new directory with your name or initials and create a new file in that directory (syntax will depend on your local OS)

```
mkdir [yourname]
cd [yourname]
echo "Starting on the Git lab" > [yourname].txt
```

Check the status, to show that there are new untracked files

`git status`

Your output should look like this: 

```
On branch GitHubLab-gnasses
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	./

nothing added to commit but untracked files present (use "git add" to track)
```

Start tracking the new file. Specify the individual filename, or use '.' to select all filenames.   

`git add . `

'git status' output should now look like this: 

```
On branch GitHubLab-gnasses
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   gnasses.txt
```

Commit the file to save your changes. Best Practice is to leave a descriptive message to identify the work or change being saved. If you do not use the -m switch, git will ask for the commit messsage. 

`git commit -m "new directory and text file" `

Your returned output should be similar to this: 

```
[GitHubLab-gnasses 46d19fd] new directory and text file
 1 file changed, 1 insertion(+)
 create mode 100644 gnasses/gnasses.txt
```

Make a file change, add the file to tracking, and make another commit (edit syntax for your OS)

`echo "Working on the Git lab" >> [yourname].txt`

`git add . `

`git commit -m "first edit to new file"`

Output from this commit should look similar to below. Note that the commit id number (immediately after the branch name) is different. Each commit is uniquely tracked. 

```
[GitHubLab-gnasses eaeffec] first edit to new file
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Compare Differences to the original 'main' branch

`git diff main GitHubLab-[yourname]`

Your output should show a linux-style diff of the changessimilar to this: 

```
diff --git a/gnasses/gnasses.txt b/gnasses/gnasses.txt
new file mode 100644
index 0000000..cd24a02
--- /dev/null
+++ a/gnasses/gnasses.txt
@@ -0,0 +1,2 @@
+Starting on the Git lab
+Working on the Git lab
```
---

## Sync your changes to GitHub

To upload your individual branch as a branch on the GitHub repo and link the two together, first set the upstream origin and push the changes to GitHub, which can all be done in one command. 

`git push --set-upstream origin GitHubLab-[yourname]`

Detailed output returned should be similar to this: 

```
Enumerating objects: 18, done.
Counting objects: 100% (18/18), done.
Delta compression using up to 12 threads
Compressing objects: 100% (10/10), done.
Writing objects: 100% (18/18), 2.70 KiB | 1.35 MiB/s, done.
Total 18 (delta 0), reused 6 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'GitHubLab-gnasses' on GitHub by visiting:
remote:      https://github.com/gnasses/GitHubLab/pull/new/GitHubLab-gnasses
remote: 
To https://github.com/gnasses/GitHubLab.git
 * [new branch]      GitHubLab-gnasses -> GitHubLab-gnasses
Branch 'GitHubLab-gnasses' set up to track remote branch 'GitHubLab-gnasses' from 'origin'.
```

Note these lines in the above output:

```
remote: Create a pull request for 'GitHubLab-gnasses' on GitHub by visiting:
remote:      https://github.com/gnasses/GitHubLab/pull/new/GitHubLab-gnasses
```

These show the link in GitHub to create a 'Pull Request' which is a request to the owner of the original main repo to merge the changes from your branch into the master branch. 

Go to that link, enter some text in the comment box to describe the code being merged in (Required) and click the green 'Create Pull Request' button to make the pull request. The owner will receive an email to let them know a merge request has been made and approval is required. The pull request will show if there are any conflicts between branches.

![image](https://github.com/gnasses/GitHubLab/blob/master/pull_request_screenshot.jpg?raw=true)




