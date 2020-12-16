# GIT FLOW SIMPLIFIED

The purpose of this lab is to teach a simplified version of git-flow to help beginner developers work effectively as a team.


## Create a git repository locally

```none
mkdir /Users/$(whoami)/git-flow-practic
cd /Users/$(whoami)/git-flow-practice
git init
```


## Create your first commit

```none
touch README.md
git add README.md
git commit -m "Add README.md file."
```


## Create remote repository on github 

1. On github.com create a new repository named git-flow-practice.


2. Add reference to origin on local git repo.  
**Be sure to replace [githubuserid] with your actual id.**

  ```
  git remote add origin https://github.com/[githubuserid]/git-flow-practice.git
  ```

4. Validate remote repository is setup.

```
git remote -v
```

3. Push local changes to remote repository.

```
git push -u origin main
```


## Create an integration branch

This branch will be where all developers sync their code to.

```
git checkout -b develop
git push origin develop
```


## Create Feature Branches

```
git branch feature_one
git branch feature_two
```


## Implement Feature One

1. Create feature_one branch
```
git checkout feature_one
```

2. Modify some code
```
vim feature_one_file.txt
```

3. Commit and push modifications
```
git status
git add feature_one_file.txt
git commit -m "Implement feature one."
git pull origin feature_one
git push origin feature_one
```

The git pull command will likely generate an error stating the following:   
"fatal: Couldn't find remote ref feature_one"

This is ok and expected. In this case, feature_one did not yet exist remotely. The idea here is to get you used to first pulling in changes from remote branches prior to pushing new code to it.


## Update local development branch

While you were busy working away on feature one, other team members may have merged their changes into the remote develop branch. Let's check before proceeding.

```
git checkout develop
git pull origin develop
```

In our case, no changes were made yet. So we may now proceed to creating a pull request.


## Open Pull Request For Feature One

1. Go to your repository on github.
2. Click on the pull requests tab.
3. Click on the green button that says "New pull request".
4. On the base drop down box, select the "develop" branch.
5. For the compare drop down box, select the "feature_one branch.
6. Review the details of  the pull request.
7. Click on the green button that says "Create pull request".
8. Optionally add in additional comments in the comment box.
9. Click on the green button that says "Create pull request".


## Review & Approve Pull Request For Feature One

1. Go to your repository on github.
2. Click on the pull requests tab.
3. Select the pull request we just created.
4. Review the details of the pull request.
5. Select the green button that says "Merge pull request."
6. Select the green button that says "Confirm merge."
7. Optionally delete feature_one branch from remote and local repos.


## Implement Feature Two

1. Check out feature two

```
git checkout feature_two
```

2. Modify some code
```
vim feature_two_file.txt
```

3. Commit and push modifications
```
git status
git add feature_two_file.txt
git commit -m "Implement feature two."
git pull origin feature_two
git push origin feature_two
```


## Update local development branch

While you were busy working away on feature two, other team members may have merged their changes into the remote develop branch. Let's check before proceeding.

```
git checkout develop
git pull origin develop
```

We now see the some changes have been applied to the develop branch while we were working on feature two. 
We should apply these changes to our feature_two branch prior to considering our work complete.

```
git checkout feature_two
git merge develop
git push origin feature_two
```


## Open Pull Request For Feature Two

1. Go to your repository on github.
2. Click on the pull requests tab.
3. Click on the green button that says "New pull request".
4. On the base drop down box, select the "develop" branch.
5. For the compare drop down box, select the "feature_two branch.
6. Review the details of  the pull request.
7. Click on the green button that says "Create pull request".
8. Optionally add in additional comments in the comment box.
9. Click on the green button that says "Create pull request".


## Review & Approve Pull Request For Feature Two

1. Go to your repository on github.
2. Click on the pull requests tab.
3. Select the pull request we just created.
4. Review the details of the pull request.
5. Select the green button that says "Merge pull request."
6. Select the green button that says "Confirm merge."
7. Optionally delete feature_two branch from remote and local repos.


## Open Pull Request For Develop To Main

All of the work from feature one and feature two are now integrated in the develop branch. 

Open a pull request to get the work from the develop branch to the main branch.

Review the pull request and merge it.


## Key take aways:

1. No one ever pushes directly to main or develop branches. Changes to these two branches are introduced only through pull requests.
2. Feature branches open pull requests against develop.
3. Develop branch opens pull requests against main.
