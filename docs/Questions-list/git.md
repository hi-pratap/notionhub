
### Q1. **What is Git and how does it differ from other version control systems?**

Git is a distributed version control system that allows multiple developers to collaborate on a project. Unlike centralized VCS, Git stores the entire history of the project locally.

### Q2. **Explain the difference between Git clone, pull, and fetch.**

**git clone** creates a local copy of a remote repository. 

**git pull** fetches changes from the remote repository and merges them into the current branch. 

**git fetch** fetches changes from the remote repository but does not merge them.

### Q3. **What is a Git repository?**

A Git repository is a data structure that stores metadata for a project, including files, directories, commit history, branches, and tags. It allows developers to track changes, collaborate, and manage versions of their code.

### Q4. **What is a Git commit?**

A Git commit is a snapshot of changes made to the repository at a specific point in time. It includes a unique identifier, author, timestamp, and a message describing the changes.

### Q5. **What is a Git branch?**

A Git branch is a lightweight movable pointer to a commit. It allows developers to work on new features or bug fixes without affecting the main codebase. Branches can be merged or deleted once their purpose is served.

### Q6. **What is a Git merge?**

Git merge combines changes from one branch into another. It creates a new commit that incorporates the changes from the specified branch into the current branch.

### Q7. **What is a Git conflict?**

A Git conflict occurs when two or more branches have made changes to the same part of a file, and Git is unable to automatically merge the changes. Resolving conflicts involves manually editing the affected files to reconcile the differences.

### Q8. **What is a Git remote?**

A Git remote is a reference to a repository hosted on a server. It allows developers to interact with the repository, fetch changes, and push commits.

### Q9. **Explain Git branching strategies like Gitflow and GitHub Flow.**

Gitflow is a branching model that defines a strict branching strategy with long-lived branches for development, release, and hotfixes. GitHub Flow is a simpler approach with short-lived branches focused on continuous delivery.

### Q10. **How do you revert a commit in Git?**

You can revert a commit in Git using the git revert command followed by the commit hash you want to revert. This creates a new commit that undoes the changes introduced by the specified commit.

**You are working on a new feature in a separate branch called feature-x. Your team decides to change its priority. How would you put your current changes on hold and switch to another task on a new branch?**

To put our changes on hold in feature-x and switch to another task, I would first save our changes using git stash. Then, I would create a new branch for the new task from the appropriate base branch using git checkout -b new-branch-name. After completing the urgent task, I can return to feature-x and apply the stashed changes with git stash pop.

**You are trying to merge your branch feature-y into the main branch, but you encounter a merge conflict in the file abc.java. How would you resolve this conflict?**

When encountering a merge conflict in abc.java while merging feature-y into the main branch, I open the file and manually resolve the conflicts by choosing the correct changes. After resolving the conflicts, I add the resolved file to the staging area using git add abc.java, and then complete the merge by committing the changes.

**Your feature branch is several commits behind the main branch. Explain how you would use git rebase to bring your branch up to date with main.**

To update our feature branch with the latest changes from the main branch, I use git rebase main while on the feature branch. This moves our branch’s changes on top of the most recent commit on the main branch, keeping the project history cleaner.

**You’re in the middle of developing a feature when an urgent bug fix needs to be addressed, but you’re not ready to commit your changes. How would you temporarily store your uncommitted changes and retrieve them later?**

To handle an urgent bug, fix while in the middle of development, I use git stash to temporarily store our uncommitted changes. After fixing the bug, I retrieve the stashed changes using git stash pop, allowing us to continue where we left off.

**After deploying a recent change, you realize it has caused a significant issue. How would you revert the last commit in your repository while ensuring the change is also removed from the history?**

To revert the last commit and remove it from the history after a problematic deployment, I use git reset –hard HEAD~1. This command undoes the last commit, resetting the HEAD to the previous commit, and the changes are discarded, ensuring the history reflects this correction.
