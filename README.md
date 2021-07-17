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

![image](https://github.com/gnasses/GitHubLab/blob/571c13e538e456c61e369e5208a63438fa84a333/pull%20request%20screenshot.png?raw=true)


---
## Typical Developer Workflow
This section describes the profcess of a typical development workflow to collaborate on a common code repository with basic code control and features of GitHub

### Issues/Assigments
An issue is simple an identification of a problem in the code, or a desired enhancement that someone wants developers to work on. Just becasue an issue is identified, does not mean that it will be worked on. It is up to the product/repo owner(s) or the development team to determine the priority of work and even if an issue will be addressed at all. Sometimes just an explanation and comment are all that are required for an issue to be close.  

For this example, an issue is created for the intentional misspelling on teh first line of the README.md in this repo. An issue is created by clicking the Issues menu near the top of the repo page. A title is required, and a description is optional, but is best practice. 

![image](https://github.com/gnasses/GitHubLab/blob/main/issue%20screenshot.png?raw=true)

If there is a development team collaborating on issues, the issue may be assigned to an individual so that the team knows who is responsible to fix the problem, or to make the enhancement. 

![image](https://github.com/gnasses/GitHubLab/blob/54f46a57baeec461cde7ad991577e98e214ba8b9/Assignment%20screenshot.png?raw=true)

### Pull Request
Above, the branch creation and pull request processes is described to incorporate the branch. The typical developer workflow is similar, however a best practice for shared development is to have each pull request related to an issue logged in the repo. In the description for the pull request, you would add the text `fixes #10` to link the request to issue #10. If the pull request is approved and the branch merged into `main` then GitHub will automatically close the issue and link to which pull request fixed the issue. Best practive is also to delete the branch for a particular feature once it is merged into `main`. 

![image](https://github.com/gnasses/GitHubLab/blob/b7df8d6ca889e3644d89634b7be181d43c9a18fa/issuefix%20screenshot.png?raw=true)

### Repo Owner Code Review/Approval and Merge into `main`
Proper code control makes sure that only the product owner or those responsible for the product development are able to approve the merge of any new branches into the `main` branch, even though any team member (or anyone at all, for open source software) can submit a pull request. Dilligent product owners will review any code before it is merged in, and may even require more than one approver before code is merged. This is configurable in teh GitHub repo. 

![image](https://github.com/gnasses/GitHubLab/blob/fa86a61c311e1803e92c36e44d2dbc9c1eb1dbbb/code%20review%20screenshot.png?raw=true)

### Code Review Options
If a repo requires approval before code is merged, there are two basic options for a reviewer (other than ignoring/deleting the pull request)
These steps are taken by the Repo owner and show the most basic code review and approval process, for a repo with a single owner/reviewer.  	

#### Request Changes
If the reviewer finds problems or has questions about the code they can request that the author of the pull request modify their code before it is approved and merged in. The reviewer should add comments to describe what changes they would like to see before code is merged in. The submitted of the pull request does not need to create another pull request, they simply need to update the code in their branch and re-request a review. 

![image](https://github.com/gnasses/GitHubLab/blob/ac4d282d644b791c9c0f789c79c7d4edc77c82f9/request%20changes%20screenshot.png?raw=true)

Here the pull request has been modified to include additional spelling fixes, and the requester has added notes and re-requested review. 

![image](https://github.com/gnasses/GitHubLab/blob/374abbe44e68f2feafe4d23c447d12a905ccd7e5/changes%20made%20screenshot.png?raw=true)

#### Approve, Merge, Delete Branch

`![image]()`

