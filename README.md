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



