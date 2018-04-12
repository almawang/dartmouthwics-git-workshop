# Dartmouth WiCS Git/GitHub Workshop

## What is git? How's it different different than GitHub?
[Git](https://git-scm.com/) is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

In layman's terms: it helps you manage changes and versions of a project, especially when working with other people.

Now [GitHub](https://github.com/) is a web-based hosting service for version control using git.

## High Level git Concepts
Projects within git are referred to as repositories or repos for short.

### Local vs. Remote
![git graphic](https://www.intertech.com/PostingIMages/f05c4ce327e8_E7D5/IntroToGitConcepts.png)

Git has two repository types: local and remote.  The local repo is on your computer for your direct use (what you work on).  The remote repo is typically elsewhere and for your indirect use, kind of like a back up that you keep updating.  Git supports multiple remote repositories.

## Getting Started
First download git if do not already have it installed. You can check by running `git` on your preferred terminal:
https://git-scm.com/

Run the following command on terminal:
```
git
```
You should get a long list of git commands and what they do. We'll go over the key ones later.

Also set up a GitHub account. Use your personal email (not your school one) because you will be using your GitHub account beyond Dartmouth. Other users will search for and find you by your username (such as for class projects) so choose one that is easy to remember and type out.
https://github.com/

Now you have git on your computer and a GitHub account on the internet. But how do we connect the GitHub account to the local git? We have to configure git!

Run the following commands (fill in your name and email you registered in GitHub with):
```
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL"
```
Now git will automatically attempt to sign into GitHub using the above email when you push your changes and prompt for your password.

## Git Basics
Now for actually using git and GitHub.

Lets create your first project in GitHub. On https://github.com ,find the new repo button in the top right corner.
![new repo](/images/newrepo.png)

Name your repo test-repo or anything else you'd like (no spaces, lowercases preferred) and click "Create repository" on the bottom.

Now you need the git specific link to the repository. On a new empty repository this is in the middle of the page. Click on the clickboard to copy the link, or just right click copy.

![empty repo](/images/emptyrepo.png)

In a non-empty repo, the link is the top right of the page

![nonempty repo](/images/nonemptyrepo.png)

Now open up Terminal. Navigate to where you want the repo stored (`ls` to list documents and folders, `cd FOLDERNAME` to go to a specific folder). Then do:
```
git clone REPO-URL
ls
```
Look for the name of your repo. Then do
```
cd REPO-NAME
```
You're now in a local version of the repo. If you open up your file explorer you can find a folder with this name. Let's add a file (don't worry about this. You could alternatively just drag any files into the folder):

```
echo "# Sample README" >> README.md
```

Now we need to add the file to the list of files git tracks:
```
git add .
```
(this adds all files)

Save all the changes so far. The message in the parentheses describes what changes you've made:
```
git commit -am "added readme"
```

Since git is a collaborative tool, someone else could be making changes to a repo. We need to make sure we're up to date with any changes they've pushed to the remote repo. Git will combine most changes so they interfere, calling *merging*:

```
git pull
```

Then save all your changes to the remote git repo (or GitHub in this case)
```
git push
```

Congrats! You're officially using git!

## Branches

Wait there's more! If you're working on a large project with everyone working on separate features, you don't constantly want other people's changes overlapping with yours. That's why you use *branches*, essentially copies of the repo that you can work on separately before combining with the master repo.

Do the command
```
git branch
```
This lists all the branches in your local git repo and indicates which one you're currently one. You should only have master and be on master at this point in the tutorial.

```
git branch new-branch
git checkout new-branch
```
The above code creates a new branch called `new-branch` and then switches into that branch.

Let's makes some changes into the branch.
```
echo "test" >> temp.txt
```

Now add, commit and push the changes
```
git add .
git commit -am "made a new file"
git push -u origin new-branch
```
See anything different? When you push a new branch to the remote repo, you need to "create" the whole branch in the remote repo, not just a file change. Therefore you have to tell git to push changes to a branch of the original repo. (-u is short for --set-upstream which essentially means push my changes to this location

![branches](/images/branches.png)

Look at your repo on GitHub. Click on the dropdown that says "branch" and you'll see your new branch! Now you can work on this branch without stressing about other people's work causing issues with your work.

### Pull Request

Say you're done with your branch, you're ready to combine it with the full project. To do so you do a **pull request**.

Click on "branches" in the top bar:
![topbar](/images/topbar.png)

Next to your branch you'll see a button that says "New pull request". Describe your changes and click "Create pull request"

![create pull request](/images/createpullrequest.png)

Normally on a large project or at a company someone more in charge would look to make sure the changes are okay and then merge the pull request, but for the same of this tutorial, follow the instructions to merge the branch.

Congrats! You're using branches like a pro!.

When you're done with a branch and no longer working with it, and to keep the number of branches from going too crazy, make sure to delete it from the GitHub (on the branches tab) and locally (with `git branch -d new-branch`, where `new-branch` is the name of your branch). 

## Merge Conflicts
Sometimes when you pull someone else's changes it may conflict with your changes. This is called a **merge conflict** and it'll in your file look something like this:

```
<<<<< master
// some code that was in master
=====
// some code that was in gh-pages
>>>>> gh-pages
```

Stay calm. Fix the conflict, add, commit and pull again. Then push the fixed conflict.

# Other aspects of git

## .gitignore file
TODO

# Extra GitHub features

## USERNAME.github.io Site
If you make a repo in GitHub named **YOURUSERNAME.github.io** with an index.html file, GitHub will automatically deploy that html to the url **YOURUSERNAME.github.io**!

# Credits
Tutorial Instructions from [Nick Charlton](https://github.com/nickcharlton/git-workshop/blob/master/Guide%20to%20Git.pdf)

Graphics and git concepts from [Intertech](https://www.intertech.com/Blog/introduction-to-git-concepts/)
