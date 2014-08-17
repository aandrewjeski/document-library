Development Workflow using Git for Pavlok Software Team
=======================================================

At Pavlok, we're building world-class behavior modification software at a ridiculously low cost. We must maintain a meticulously high standard of code quality if we are to outlast the competition. Technical debt, is the very real problem that you face when you push code into production without fully understanding how it works. Pavlok is a company about building good habits. Let's use good habits to build great software.

# Good habits are going to beat out experience

*It doesn't matter if you're a rockstar developer if other developers come into your code base feeling like a monkey at mensa conference.*

Git
===
*"Git is a distributed revision control and source code management (SCM) system with an emphasis on speed, data integrity, and support for distributed, non-linear workflows."*
*- Wikipedia*

## New Projects
1. You'll need to initialize a new local repository in your project's root directory using `git init`
2. Now you can begin tracking your changes!
3. *But first,* you need to create a `.gitignore` file. In a Rails app this should be available by default.
4. Your `.gitignore` file should include `.DS_Store` if you're using a mac
5. Then, move all your changes into a temporary staging area by running `git add -A`
6. You can make those changes permanent by running `git commit -m"Initial commit"`

## Sharing Code
Pavlok uses Github to host and share code. If you're dropping into one of our codebases, just run `git clone git@github.com:justuseapen/REPO_NAME.git`. That will copy the master branch of the repository into your current directory.

### Follow along with this tutorial:
1. Fork one of the Pavlok repositories to your profile.
2. Clone the repo to your machine.
3. Make the root of the project your working directory.
4. Run `git checkout -b NEW_BRANCH_NAME_HERE` to create a new branch off of master
5. Fix a bug, refactor a model, build a feature, write a test, enhance the README, it doesn't matter, just make a single, small change.
6. Save your changes.
7. Stage your changes `git add -A`
8. Commit your changes `git commit -m"COMMIT MESSAGE GOES HERE"
9. Push your branch to GitHub `git push origin BRANCH NAME`
10. Make a pull request

Congratulations! That is going to be the workflow you use on any new project you join at Pavlok! If you're currently working on a project, you can simply start that workflow at step 4.

# Branches
The default branch in a project is known as a master branch. This is the branch that we will push to production and is therefore sacred.

A GitHub repo is a tree, where the tip of each branch is the snapshot of the most recent commit.

Use tig `brew install tig` to view repo trees and examine diffs.

Let’s run through an example:

## Branching off of Pavlokcom
1. Firstly, decide which branch you want to break off of. Are you starting a new feature? If so, start from master:
2. Clone master using git clone git@github.com:maneeshsethi/Pavlokcom.git .
3. Or, do you want the latest code for an in-progress feature? You’ll still want to clone master. But then you have…
4. …Pull the branch you are looking for: git pull origin branch_im_looking_for
5. Then, break off a new branch with git checkout -b branch_name_explaining_what_youre_doing
6. Make changes to that document and COMMIT EARLY AND OFTEN. This means git add ./files/with/changes and git commit -m”detailed message about changes made”
7. A good github repository allows us to track feature creation all the way through the product lifecycle. We’ll never lose code this way.
8. When the feature you’re building is completed, and hopefully well-tested, you can git push origin branch_name_explaining_what_youre_doing
9. If you look at the branch in GitHub, you there will be an option to create a pull request. Doing so will update the collaborators and someone can code review your branch and choose to merge with master. This ensures at least two people look at all the code. This is extremely important to maintaining good code quality and is an essential habit to propagate.

## Merging Feature Branches
Never merge feature branches directly to master. Feature branches should go through QA,then be merged into integration. New features only go into master
1. `git checkout integration`
2. `git merge no-ff feature_branch`
3. The no-ff is important because it retains the historical commits associated with the feature branch.


## Ten git commandments
1. Thou shalt not pollute the master branch with buggy code.
2. Thou shalt refactor thy code before pushing to master.
3. Thou shalt commit early and commit often.
4. Thou shalt submit pull requests.
5. Thou shalt share thy codebase.
6. Thou shalt not push directly to master.
7. Thou shalt name your branches in lowercase snake string

## Pavlok and Git Branching: Keeping Things Organized
Branching is essential to the work flow of a project. Allowing each contributer to have their own branch for features keeps things clean and prevents from polluting the master with bugs and missing out on team approval.

The more organized the branching system, the more closely the code can be tracked and patched. At Pavlok, using this system will help to make sure that mishaps do not make it into the product which is vital to our success.

### Master and Integration Branches
The master branch is the core of a branching scheme. The master branch should never be directly committed to. It is only for stable version releases that contain no bugs or failing tests.

The development branch is work in progress. When new features are ready to go, a pull request is made. After all contributers validate it, it is merged into master and the new commit on master is called a version release.

### Features and Hotfixes
A feature is any new major addition to the functionality or support of the software. Features are branched off of the integration branch and are merged when the feature is polished.This generally will be the type of branch most frequently worked on.

A hotfix branch is an extraordinary case of branching that happens when a bug or technicality is discovered in a working version. To patch the problem, hotfix is branched directly off of master to quickly solve the problem.

### Release Branches
Release branches are not always necessary, but provide additional support before a feature is integrated to a new version in master. This branch allows for a last lookover for bugs and small mishaps before the merge. Once a bug is patched, the release branch can be merged into master.

# Existing projects


