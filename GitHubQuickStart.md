GitHub HowTo from dmchdev:

This file's purpose is to simplify dealing with git and github for beginners, especially regarding pushing their local repository into the remote. The available instructions do a pretty good job of explaining how to set up git and gitHub and how to pull from it. Before you can 'pull' money out of your pocket, you need to 'push' it in there, right? You need to create your repository, fill it with files  and so on. These are simplified instructions on how to do that. If you get these, it'll be much easier to understand more complex things you can do with git and github. Definitely refer to official tutorials for more info.
I found that many beginners are confused about what git and github are:
'Git' is a version control system, it is a program on your computer that keeps track of changes you make to your work (to any files—text, images, code etc.) Git creates a local repository (a special folder) where the tracking is done. Each directory can have its own repository, it's up to you how you want it.
'GitHub' is a place on the internet where you can upload a remote copy of your local repository. GitHub is actually the name of the company that provides the hosting and management service for your remote repository. Yes, there is a program called “GitHub for Windows”, but it is not the GitHub itself, just a helper program for GitHub. I personally prefer the command line to the “GitHub for Windows”. 
To 'commit' means to 'save' changes to your repository. Before you commit, you 'stage' your changed files. 'Staging' is adding files that you just finished changing, to the list of files you want to commit after you finish your work. Essentially, you make changes to files and keep 'staging' them one by one and, once you are done changing, commit them all at once.

Without further ado:

Say you have a project named 'SuperProject' you want to keep track of using git and github.
 1.	Install/configure git and sign up for an account at github.
 2.	Using your command line, go to your project directory
 3.	Once in your project directory type **git init** (this creates an empty repository for your project in your project folder. You'll have //SuperProject/.git as a result. This is done only once for each particular directory you want to keep track of. Once the .git is there you don't run git init again.
 4.	Now indicate which files you want to commit (this is called 'staging') by typing:  **git add** _yourfilename_. The file indicated is now ready to commit.
 5.	Commit your file by typing: **git commit" _-m “Your Comment”_.  “git commit” is the general command, “-m” is an extra argument allowing you to add “Your Comment”(whatever you want to say about this particular commit). Congratulations, your file is now committed to your LOCAL repository
 6.	Now let's add it to github. Log into your github account and add/create a new repository (use the “+” sign at the top right corner of the page) and name it “SuperProject”. Don't initialize it with Readme option, just create it for now.
 7.	Go back to your command line. Stay in your project directory. In command line type this: **git remote add** _SuperProject yourprojectURL_ 
 8.	Example: **git remote add** _SuperProject https://github.com/YourGitHubID/SuperProject_   This creates a 'connection' between your local repository and the remote one on github.
 9.	Now type: **git push** _SuperProject master_ You'll be asked your password and githubID. When you type your password cursor doesnt move. Don't worry, it's recording your input. This whole operation pushed your local repository contents into the master(main) branch of the remote repository.
 10.	Now go back to your github and refresh the page you got after creating your repository. 'yourfilename' should be displayed.

###CLONING:
 If you wish to collaborate, or to view a repository that someone else has created, you need to clone it from a remote location, such as GitHub. Type this:

 **git clone** _URL-path-to-repository_

 This may ask for credentials if you are supposed to have them. For publicly accessible repos, it will just clone it onto your hard drive as a child directory to wherever you happend to issue the git clone command from. So if you were in /ProgrammingProjects/OtherPeoplesRepos, then it would create a subdirectory named after the repo you are cloning.

###PULLING
 As part of your development workflow, in order to get the latest from the remote, before branching and making any changes, type:  
 **git pull**  
 This should synchronize the content of the remote repo with you local copy. Now you can branch.

###BRANCHING:
 Most workflows involve branching. A branch is essentially a sandboxed copy of the original repository. It is sandboxed
 because when you make changes on it, they are not going to affect the original repository, unless you merge the branch into the original repository, at which point the changes you made will become part of the original repo. This also allows for easy code review process using Pull Requests (a request for other developers to pull your branch and see how your changes work).

 Every developer should create a branch before doing new work. This is actually enforced at most companies. Nobody commits directly to the "master" branch.  
 To create a branch, cd into the desired directory and type this:

 **git branch** _desired-branch-name_

 Example: in your /SuperProject directory, type **git branch** _new-cool-feature-for-superproject_

 This will create a branch named _new-cool-feature-for-superproject_ and allow you to add code and test changes, without affecting SuperProject.

 Type **git branch** to see which branch you are currently on (marked with *)
 
 To actually move into the sandbox (your new branch) to work, type:
 **git checkout** _new-cool-feature-for-superproject_  
 Now you are in and ready to play around.
 
 To RENAME a branch, type:

 **git branch** _-m new-name_

###STASHING
 To stash away changes to be applied later, use the **git stash** command on your current branch  
 Stash contains your new work, as determined by Git in relation to where you will be applying that stash.  
 You stash when you need to go do work on some other branch on the same repo, or if you don't wish to commit changes yet.  
 To apply stash to your repo, type:  
 **git stash pop** OR **git stash apply**  
 The former deletes the stash after applying, the latter does not. 
 If you accidentally started making changes without branching first, type this:
 **git stash branch** _new-cool-feature-for-superproject_  
 This will create a branch off your master named _new-cool-feature-for-superproject_ and changes made will be applied to it. At the same time, these changes will disappear from master, as if you properly branched in the first place.  

###PUSHING
 Pushing is a moving changes into a remote repository. Normally, you want the remote repo to also have a branch just like yours so that others could review that branch, and merge it into remote master if they like it. Type this:  
 **git push origin** _new-cool-feature-for-superproject_  
 This creates a branch _new-cool-feature-for-superproject_ on the remote. Now you can go to GitHub and issue a Pull Request on that branch. Should it get approved, your changes could be merged into the remote repo.  
 "origin" is the name of your remote usually given when you clone someone's work. It is the same thing as the would be created by **git remote add** from step 7 above in "without further ado".

###OTHER USEFUL COMMANDS
**git status** to get current state of affairs. USE THIS OFTEN, PLEASE  
**git add** _-all_ to stage all changed files at once (no name typing)  
**git stash** -help to access Git user manual for "git stash". Use any command with -help flag to get help right from Git.

