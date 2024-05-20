# gitAdvanced

## Initial commits
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

## Missing File Fix
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

### staging/adding test4.md and amending the commit message
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
#### how to see the hash for my head
```bash 
$ git reset --hard head~
HEAD is now at 3fe93ab chore: Create another file
```
