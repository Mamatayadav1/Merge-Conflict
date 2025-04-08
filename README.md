# Git Workflow with Merge Conflict Handling and Actual Output
# Step 1: Cloning the forked repository
PS C:\Users\HP> git clone https://github.com/Mamatayadav1/Merge-Conflict.git
Cloning into 'Merge-Conflict'...
warning: You appear to have cloned an empty repository.

# Navigate into the cloned directory
PS C:\Users\HP> cd Merge-Conflict

# Step 2: Adding the upstream remote (original source repo)
PS C:\Users\HP\Merge-Conflict> git remote add upstream https://github.com/devops-intellipaat/merge-conflict.git

# Step 3: Fetching all branches and updates from upstream
PS C:\Users\HP\Merge-Conflict> git fetch upstream
remote: Enumerating objects: 15, done.
remote: Total 15 (delta 0), reused 0 (delta 0), pack-reused 15
Unpacking objects: 100% (15/15), 1.72 KiB | 10.00 KiB/s, done.
From https://github.com/devops-intellipaat/merge-conflict
 * [new branch]      feature1   -> upstream/feature1
 * [new branch]      feature2   -> upstream/feature2
 * [new branch]      master     -> upstream/master

# Step 4: Creating and switching to local master from upstream/master
PS C:\Users\HP\Merge-Conflict> git checkout -b master upstream/master
branch 'master' set up to track 'upstream/master'.
Switched to a new branch 'master'

# Pushing master to origin
PS C:\Users\HP\Merge-Conflict> git push origin master
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (9/9), 1.14 KiB | 53.00 KiB/s, done.
Total 9 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/Mamatayadav1/Merge-Conflict.git
 * [new branch]      master -> master

# Step 5: Creating local feature1 branch tracking upstream/feature1
PS C:\Users\HP\Merge-Conflict> git checkout -b feature1 upstream/feature1
branch 'feature1' set up to track 'upstream/feature1'.
Switched to a new branch 'feature1'

# Step 6: Merging master (security patch) into feature1
PS C:\Users\HP\Merge-Conflict> git merge master
Auto-merging main.c
CONFLICT (content): Merge conflict in main.c
Automatic merge failed; fix conflicts and then commit the result.

# Resolve conflict in main.c manually, then:
PS C:\Users\HP\Merge-Conflict> git add main.c
PS C:\Users\HP\Merge-Conflict> git commit -m "Merged master (security patch) into feature1"
[feature1 ea6fe67] Merged master (security patch) into feature1

# Push to remote
PS C:\Users\HP\Merge-Conflict> git push origin feature1
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 692 bytes | 62.00 KiB/s, done.
Total 6 (delta 0)
remote:
remote: Create a pull request for 'feature1' on GitHub by visiting:
remote:      https://github.com/Mamatayadav1/Merge-Conflict/pull/new/feature1
remote:
To https://github.com/Mamatayadav1/Merge-Conflict.git
 * [new branch]      feature1 -> feature1

# Step 7: Creating local feature2 branch tracking upstream/feature2
PS C:\Users\HP\Merge-Conflict> git checkout -b feature2 upstream/feature2
branch 'feature2' set up to track 'upstream/feature2'.
Switched to a new branch 'feature2'

# Step 8: Merging master (security patch) into feature2
PS C:\Users\HP\Merge-Conflict> git merge master
Auto-merging main.c
CONFLICT (content): Merge conflict in main.c
Automatic merge failed; fix conflicts and then commit the result.

# Resolve conflict in main.c manually, then:
PS C:\Users\HP\Merge-Conflict> git add main.c
PS C:\Users\HP\Merge-Conflict> git commit -m "Merged master (security patch) into feature2"
[feature2 fb8664a] Merged master (security patch) into feature2

# Push to remote
PS C:\Users\HP\Merge-Conflict> git push origin feature2
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 695 bytes | 40.00 KiB/s, done.
Total 6 (delta 0)
remote:
remote: Create a pull request for 'feature2' on GitHub by visiting:
remote:      https://github.com/Mamatayadav1/Merge-Conflict/pull/new/feature2
remote:
To https://github.com/Mamatayadav1/Merge-Conflict.git
 * [new branch]      feature2 -> feature2

# Step 9: Merge features into master
PS C:\Users\HP\Merge-Conflict> git checkout master
Switched to branch 'master'
Your branch is up to date with 'upstream/master'.

# Optional: trying to commit something that has no change
PS C:\Users\HP\Merge-Conflict> git add main.c
PS C:\Users\HP\Merge-Conflict> git commit -m "Merged feature1 into master"
On branch master
Your branch is up to date with 'upstream/master'.

nothing to commit, working tree clean

# Merge feature2 into master
PS C:\Users\HP\Merge-Conflict> git merge feature2
Updating f71ccdc..fb8664a
Fast-forward
 main.c | 7 +++++++
 1 file changed, 7 insertions(+)

# Optional commit (already merged)
PS C:\Users\HP\Merge-Conflict> git add main.c
PS C:\Users\HP\Merge-Conflict> git commit -m "Merged feature2 into master"
On branch master
Your branch is ahead of 'upstream/master' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

# Step 10: Push the final master to GitHub
PS C:\Users\HP\Merge-Conflict> git push origin master
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Mamatayadav1/Merge-Conflict.git
   f71ccdc..fb8664a  master -> master
