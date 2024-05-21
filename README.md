# Git Advanced Exercises

## Part 1
### Initial commits
```bash
touch test{1..4}.md

$ git add test1.md && git commit -m "chore: Create initial file"
[main d43353b] chore: Create initial file       
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md

 $ git add test2.md && git commit -m "chore: Create another file"
[main 8c6f710] chore: Create another file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md

 $ git add test3.md && git commit -m "chore: Create third and fourth files"
[main f8fe744] chore: Create third and fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

```

### Missing File Fix
```bash
$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

no changes added to commit (use "git add" and/or "git commit -a")

$ git log
commit f8fe744b28eec1fc11b618f3017eeb1d7f9f1d18 (HEAD -> main)
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Mon May 20 18:04:25 2024 +0200

    chore: Create third and fourth files

commit 8c6f71040a038c7f677efe45b80837b8f7e1db6e
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Mon May 20 18:04:22 2024 +0200

    chore: Create another file

commit d43353b2f04e6d62a11825c5df3c8658a51158c6
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Mon May 20 18:04:21 2024 +0200

    chore: Create initial file

commit f4b68f980b96895157f2d4aee81b68555c3766d9 (origin/main, origin/HEAD)
Author: Beyla Ruzindana Irakoze <142901020+beylar@users.noreply.github.com>
Date:   Mon May 20 18:02:20 2024 +0200

    Initial commit
```

### Staging/adding test4.md and amending the commit message
```bash
$ git add test4.md & git commit --amend
[1] 1561
[main 5950ba5] chore: Create fourth files        
 Date: Mon May 20 18:04:25 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
[1]+  Done                    git add test4.md

```

```bash
$ git rebase -i
Stopped at 3fe93ab...  chore: Create another file
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue
```
```bash
$ git commit --amend
[detached HEAD d5a60f7] chore: Create second file
 Date: Mon May 20 19:21:47 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
```

```bash
$ git rebase --continue
Successfully rebased and updated refs/heads/main.
```
### How to see the hash for my head
```bash 
$ git reset --hard head~
HEAD is now at 3fe93ab chore: Create another file
```

### Rebase
```bash
$ git rebase -i HEAD~3
[detached HEAD 0fe95f3] chore: Create initial file
 Date: Tue May 21 08:55:11 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

$ git log
commit 5b89fe19b4e4e7706f9500bd94c3680e9d28423e (HEAD -> main)
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 08:55:16 2024 +0200

    chore: Create fourth files

commit 0fe95f35a975d06ef3967004a375d36e4a7954e1
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 08:55:11 2024 +0200

    chore: Create initial file

    chore: Create second file
```
### Splitting commits
```bash
$ git reset HEAD~

$ git add test3.md & git commit -m "Create third files"
[1] 581
[main 0c94a37] Create third files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
[1]+  Done                    git add test3.md

$ git add test4.md & git commit -m "Create fourth files"
[1] 598
[main 437a4e8] Create fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md
[1]+  Done                    git add test4.md

$ git rebase -i HEAD~3
[detached HEAD 8482af7] Create third and fourth files
 Date: Tue May 21 10:41:32 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

$ git log
commit 8482af71de1e0211449029de0646ce1060769711 (HEAD -> main)
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 10:41:32 2024 +0200

    Create third and fourth files

commit 0fe95f35a975d06ef3967004a375d36e4a7954e1
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 08:55:11 2024 +0200

    chore: Create initial file

    chore: Create second file

commit 42aa524481bf3ae39e804e76f16e706cfaf77642 (origin/main, origin/HEAD)
Author: Beyla Ruzindana Irakoze <142901020+beylar@users.noreply.github.com>
Date:   Tue May 21 08:52:02 2024 +0200

    Initial commit

```

### Dropping a commit 
```bash
$ touch unwanted.txt

$ git add unwanted.txt & git commit -m "Unwanted text"
[1] 748
[main a92dfa6] Unwanted text
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 unwanted.txt
[1]+  Done                    git add unwanted.txt

$ git log
commit a92dfa6c1f580829a0dd8b25998864f8cf46d645 (HEAD -> main)
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 11:03:16 2024 +0200

    Unwanted text

commit 8482af71de1e0211449029de0646ce1060769711
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 10:41:32 2024 +0200

    Create third and fourth files

commit 0fe95f35a975d06ef3967004a375d36e4a7954e1
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 08:55:11 2024 +0200

    chore: Create initial file

    chore: Create second file

commit 42aa524481bf3ae39e804e76f16e706cfaf77642 (origin/main, origin/HEAD)
Author: Beyla Ruzindana Irakoze <142901020+beylar@users.noreply.github.com>
Date:   Tue May 21 08:52:02 2024 +0200

    Initial commit

$ git reset --hard HEAD~1
HEAD is now at 8482af7 Create third and fourth files
```

### Reordering Commits
```bash
$ git log
commit 8482af71de1e0211449029de0646ce1060769711 (HEAD -> main)

Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 10:41:32 2024 +0200

    Create third and fourth files

commit 0fe95f35a975d06ef3967004a375d36e4a7954e1
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 08:55:11 2024 +0200

    chore: Create initial file

    chore: Create second file

commit 42aa524481bf3ae39e804e76f16e706cfaf77642 (origin/main, origin/HEAD)
Author: Beyla Ruzindana Irakoze <142901020+beylar@users.noreply.github.com>
Date:   Tue May 21 08:52:02 2024 +0200

    Initial commit

$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

$ git log
commit 99d594c53b0a25899c92702b5114b09a6facbbff (HEAD -> main)
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 08:55:11 2024 +0200

    chore: Create initial file

    chore: Create second file

commit 3ce4fb06c095a2ac5155c333db2f4b391fb3d401
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 10:41:32 2024 +0200

    Create third and fourth files

commit 42aa524481bf3ae39e804e76f16e706cfaf77642 (origin/main, origin/HEAD)
Author: Beyla Ruzindana Irakoze <142901020+beylar@users.noreply.github.com>
Date:   Tue May 21 08:52:02 2024 +0200

    Initial commit
```

### Cherry Picking Events
```bash
$ git checkout -b ft/branch
Switched to a new branch 'ft/branch'
$ touch test5.md
$ git add test5.md
$ git commit -m "Implemented test 5"
[ft/branch 954fc68] Implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

 $ git log
commit 954fc68ffc804678c612817fb2121fc3d045ca1d (HEAD -> ft/branch)
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 11:44:12 2024 +0200

    Implemented test 5

commit 99d594c53b0a25899c92702b5114b09a6facbbff (main)
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 08:55:11 2024 +0200

    chore: Create initial file

    chore: Create second file

commit 3ce4fb06c095a2ac5155c333db2f4b391fb3d401
Author: Beyla Irakoze <beylaruz@gmail.com>
Date:   Tue May 21 10:41:32 2024 +0200

    Create third and fourth files

commit 42aa524481bf3ae39e804e76f16e706cfaf77642 (origin/main, origin/HEAD)
Author: Beyla Ruzindana Irakoze <142901020+beylar@users.noreply.github.com>
Date:   Tue May 21 08:52:02 2024 +0200

$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

$ git cherry-pick 954fc68ffc804678c612817fb2121fc3d045ca1d
[main 49642ba] Implemented test 5
 Date: Tue May 21 11:44:12 2024 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md
```

### Visualizing Commit History
```bash
$ git log --graph
* commit 49642ba9b3682184e901362f191e8845afff30f6 (HEAD -> main)
| Author: Beyla Irakoze <beylaruz@gmail.com>
| Date:   Tue May 21 11:44:12 2024 +0200
|
|     Implemented test 5
|
* commit 99d594c53b0a25899c92702b5114b09a6facbbff
| Author: Beyla Irakoze <beylaruz@gmail.com>
| Date:   Tue May 21 08:55:11 2024 +0200
|
|     chore: Create initial file
|
|     chore: Create second file
|
* commit 3ce4fb06c095a2ac5155c333db2f4b391fb3d401
| Author: Beyla Irakoze <beylaruz@gmail.com>
| Date:   Tue May 21 10:41:32 2024 +0200
|
|     Create third and fourth files
|
* commit 42aa524481bf3ae39e804e76f16e706cfaf77642 (origin/main, origin/HEAD)
  Author: Beyla Ruzindana Irakoze <142901020+beylar@users.noreply.github.com>
  Date:   Tue May 21 08:52:02 2024 +0200

      Initial commit
```

### Reflogs
```bash
49642ba (HEAD -> main) HEAD@{0}: cherry-pick: Implemented test 5
99d594c HEAD@{1}: checkout: moving from ft/branch to main
954fc68 (ft/branch) HEAD@{2}: reset: moving to 954fc68ffc804678c612817fb2121fc3d045ca1d
954fc68 (ft/branch) HEAD@{3}: reset: moving to 954fc68ffc804678c612817fb2121fc3d045ca1d
954fc68 (ft/branch) HEAD@{4}: rebase (finish): returning to refs/heads/ft/branch
954fc68 (ft/branch) HEAD@{5}: rebase (start): checkout HEAD~3
954fc68 (ft/branch) HEAD@{6}: commit: Implemented test 5
99d594c HEAD@{7}: checkout: moving from main to ft/branch
99d594c HEAD@{8}: rebase (finish): returning to refs/heads/main
99d594c HEAD@{9}: rebase (pick): chore: Create initial file
3ce4fb0 HEAD@{10}: rebase (pick): Create third and fourth files
42aa524 (origin/main, origin/HEAD) HEAD@{11}: rebase (start): checkout HEAD~2
8482af7 HEAD@{12}: rebase (abort): returning to refs/heads/main
42aa524 (origin/main, origin/HEAD) HEAD@{13}: rebase (start): checkout HEAD~2
8482af7 HEAD@{14}: rebase (abort): returning to refs/heads/main
42aa524 (origin/main, origin/HEAD) HEAD@{15}: rebase (start): checkout HEAD~2
8482af7 HEAD@{16}: reset: moving to HEAD~1
a92dfa6 HEAD@{17}: rebase (finish): returning to refs/heads/main
a92dfa6 HEAD@{18}: rebase (start): checkout HEAD~3
a92dfa6 HEAD@{19}: commit: Unwanted text
8482af7 HEAD@{20}: rebase (finish): returning to refs/heads/main
8482af7 HEAD@{21}: rebase (start): checkout refs/remotes/origin/main
8482af7 HEAD@{22}: rebase (finish): returning to refs/heads/main
8482af7 HEAD@{23}: rebase (squash): Create third and fourth files
0c94a37 HEAD@{24}: rebase (start): checkout HEAD~3
437a4e8 HEAD@{25}: commit: Create fourth files
0c94a37 HEAD@{26}: commit: Create third files
0fe95f3 HEAD@{27}: reset: moving to HEAD~
5b89fe1 HEAD@{28}: reset: moving to HEAD
5b89fe1 HEAD@{29}: rebase (finish): returning to refs/heads/main
5b89fe1 HEAD@{30}: rebase (pick): chore: Create fourth files
0fe95f3 HEAD@{31}: rebase (squash): chore: Create initial file
defa2cd HEAD@{32}: rebase (start): checkout HEAD~3
36ed635 HEAD@{33}: rebase (finish): returning to refs/heads/main
36ed635 HEAD@{34}: rebase (start): checkout HEAD~2
36ed635 HEAD@{35}: rebase (finish): returning to refs/heads/main
36ed635 HEAD@{36}: rebase (start): checkout HEAD~2
36ed635 HEAD@{37}: rebase (finish): returning to refs/heads/main
36ed635 HEAD@{38}: rebase (pick): chore: Create fourth files
e714441 HEAD@{39}: commit (amend): chore: Create second file
b969cc5 HEAD@{40}: rebase: fast-forward
defa2cd HEAD@{41}: rebase (start): checkout refs/remotes/origin/main
a456e24 HEAD@{42}: commit (amend): chore: Create fourth files
f707c76 HEAD@{43}: commit: chore: Create third and fourth files
b969cc5 HEAD@{44}: commit: chore: Create another file
defa2cd HEAD@{45}: commit: chore: Create initial file
42aa524 (origin/main, origin/HEAD) HEAD@{46}: clone: from https://github.com/beylar/gitLearning.git
```

## Part 2

### Branch creation
```bash
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'
```

### Working on the feature branch
```bash
$ touch feature.txt
$ git add feature.txt 
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature d53c0f0] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
```

### Switching Back and Making More Changes
```bash
 $ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits) 
$ touch readme.txt
$ git add readme.txt   
$ git commit -m "Updated project readme"
[main 89e873f] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

```

### Local vs. Remote Branches
```bash
$ git checkout ft/new-feature 
Switched to branch 'ft/new-feature'

$ git push origin ft/new-feature 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.    
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done. 
Writing objects: 100% (3/3), 319 bytes | 106.00 KiB/s, done. 
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote: 
remote: Create a pull request for 'ft/new-feature' on GitHub by visiting:  
remote:      https://github.com/beylar/Git_learning/pull/new/ft/new-featur 
remote:
To https://github.com/beylar/Git_learning.git
 * [new branch]      ft/new-feature -> ft/new-feature

$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
  ```

### Branch deletion
```bash 
$ git merge ft/new-feature
Merge made by the 'ort' strategy.
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

$ git branch --delete ft/new-feature
Deleted branch ft/new-feature (was fae2d96).
```

### Creating a branch from a commit
```bash
$ git log -1 --pretty=format:%H HEAD~2
ea8e6c730ee48d31a3f50ba78cd0868592d5067e

$ git checkout -b ft/new-branch-from-commit 1d2d98d687d3b02269d6775955c67f098a3ac7f0
Switched to a new branch 'ft/new-branch-from-commit'
```

### Branch merging
```bash
$ touch text.txt
$ git add text.txt
$ git commit -m "changes in new feature branch"
[ft/new-branch-from-commit 7154af7] changes in new feature branch
 1 file changed, 1 insertion(+)
 create mode 100644 text.txt
$ git push origin ft/new-branch-from-commit
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (8/8), 872 bytes | 109.00 KiB/s, done.
Total 8 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), done.
remote:
remote: Create a pull request for 'ft/new-branch-from-commit' on GitHub by 
visiting:
remote:      https://github.com/beylar/Git_learning/pull/new/ft/new-branch-from-commit
remote:
To https://github.com/beylar/Git_learning.git
 * [new branch]      ft/new-branch-from-commit -> ft/new-branch-from-commit
$ git merge ft/new-branch-from-commit
Updating 1d2d98d..7154af7
Fast-forward
 text.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 text.txt
 
 $ git pull origin main
From https://github.com/beylar/Git_learning
 * branch            main       -> FETCH_HEAD
Updating 7154af7..4a4b15a
Fast-forward

```

### Branch Rebasing
```bash
$ git checkout ft/new-branch-from-commit
$ git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
```

### Renaming branches
```bash
 git branch -m ft/new-branch-from-commit ft/improved-branch-name
```

### Checking Out Detached HEAD
```bash
$ git checkout 1d2d98d687d3b02269d6775955c67f098a3ac7f0
Note: switching to '1d2d98d687d3b02269d6775955c67f098a3ac7f0'.

You are in 'detached HEAD' state. You can look around, make experimental   
changes and commit them, and you can discard any commits you make in this  
state without impacting any branches by switching back to a branch.        

If you want to create a new branch to retain commits you create, you may   
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 1d2d98d Merge branch 'ft/new-feature'
```

## Part 3
### Stashing Changes
```bash
$ git stash
Saved working directory and index state WIP on main: 4a4b15a Merge pull request #2 from beylar/ft/new-branch-from-commit
```

### Retrieving Stashed Changes
```bash
$ git stash pop
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (9fe5875fed2c1c44397f005fed33118c560a5145)
```
### Branch Merging Conflicts
```bash

```
### Resolving Merge Conflicts with a Merge Tool
```bash

```

### Understanding Detached HEAD State
```bash
$ git checkout 1d2d98d687d3b02269d6775955c67f098a3ac7f0
M       readme.txt
Note: switching to '1d2d98d687d3b02269d6775955c67f098a3ac7f0'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 1d2d98d Merge branch 'ft/new-feature'
```

### Ignoring Files/Directories
```bash

```

### Working with Tags
```bash

```

### Listing and Deleting Tags
```bash

```

### Pushing Local work to Remote Repositories
```bash

```
### Pulling Changes from Remote Repositories
```bash

```


