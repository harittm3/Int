# Int
# lab
LAB-3
Q3. Creating and Managing Branches
Write the commands to stash your changes, switch branches, and then apply the stashed changes.

1. Stash your changes:

#git stash save "Your stash message"
This command will save your local changes in a temporary area, allowing you to switch branches without committing the changes.

2. Switch to another branch:

#git checkout your-desired-branch
3. Apply the stashed changes:

#git stash apply
If you have multiple stashes and want to apply a specific stash, you can use:

#git stash apply stash@{1}
After applying the stash, your changes are reapplied to the working directory.

4. Remove the applied stash (optional):

If you no longer need the stash after applying it, you can remove it:

#git stash drop
To remove a specific stash:

#git stash drop stash@{1}
If you want to apply and drop in one step, you can use git stash pop:

#git stash pop



LAB-5
first, add a line to remote (GitHub) repo
git@ise:~/your-usn-here/proj-5$ gedit README.md // (or) echo "line-2" > README.md
git@ise:~/your-usn-here/proj-5$ git add README.md
git@ise:~/your-usn-here/proj-5$ git commit -m "Local changes"
[master e308769] Local changes
1 file changed, 1 insertion(+)
git@ise:~/your-usn-here/proj-5$ git fetch
Username for 'https://github.com': your-user-name
Password for 'https://your-user-name@github.com':
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 920 bytes | 920.00 KiB/s, done.
From https://github.com/write-your-username-here/aiml-prog-5
eef175d..318215a master -> origin/master
git@ise:~/your-usn-here/proj-5$ git rebase origin/master
First, rewinding head to replay your work on top of it...
Applying: Local changes
Using index info to reconstruct a base tree...
M README.md
Falling back to patching base and 3-way merge...
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
error: Failed to merge in the changes.
Patch failed at 0001 Local changes
hint: Use 'git am --show-current-patch' to see the failed patch
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
git@ise:~/your-usn-here/proj-5$ gedit README.md (resolve the rebase conflict here!)
git@ise:~/your-usn-here/proj-5$ git status
rebase in progress; onto 318215a
You are currently rebasing branch 'master' on '318215a'.
(fix conflicts and then run "git rebase --continue")
(use "git rebase --skip" to skip this patch)
(use "git rebase --abort" to check out the original branch)
Unmerged paths:
(use "git restore --staged <file>..." to unstage)
(use "git add <file>..." to mark resolution)
both modified: README.md
no changes added to commit (use "git add" and/or "git commit -a")
git@ise:~/your-usn-here/proj-5$ git add .
git@ise:~/your-usn-here/proj-5$ git rebase --continue
Applying: Local changes
git@ise:~/your-usn-here/proj-5$ git push -u origin master
Username for 'https://github.com': your-user-name
Password for 'https://your-user-name@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 288 bytes | 288.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/your-user-name-here/aiml-prog-5.git
318215a..839c37a master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.



LAB-6
git@ise:~/your-usn-here/proj-6$ git branch feature-branch
git@ise:~/your-usn-here/proj-6$ gedit README.md // (or) echo "line-1" > README.md
git@ise:~/your-usn-here/proj-6$ git status
On branch master
Your branch is up to date with 'origin/master'.
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: README.md
no changes added to commit (use "git add" and/or "git commit -a")
git@ise:~/your-usn-here/proj-6$ git add README.md
git@ise:~/your-usn-here/proj-6$ git commit -m "edit in master"
[master 703a630] edit in master
1 file changed, 1 insertion(+)
git@ise:~/your-usn-here/proj-6$ git checkout feature-branch
Switched to branch 'feature-branch'
git@ise:~/your-usn-here/proj-6$ gedit README.md // (or) echo "line-1\nline-2" > README.md
git@ise:~/your-usn-here/proj-6$ git status
On branch feature-branch
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: README.md
no changes added to commit (use "git add" and/or "git commit -a")
git@ise:~/your-usn-here/proj-6$ git add .
git@ise:~/your-usn-here/proj-6$ git commit -m "edit2 in feature-branch"
[feature-branch 1a419c8] edit2 in feature-branch
1 file changed, 2 insertions(+)
git@ise:~/your-usn-here/proj-6$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
(use "git push" to publish your local commits)
git@ise:~/your-usn-here/proj-6$ git merge feature-branch -m "merge fb"
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
git@ise:~/your-usn-here/proj-6$ gedit README.md
git@ise:~/your-usn-here/proj-6$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
(use "git push" to publish your local commits)
You have unmerged paths.
(fix conflicts and run "git commit")
(use "git merge --abort" to abort the merge)
Unmerged paths:
(use "git add <file>..." to mark resolution)
both modified: README.md
no changes added to commit (use "git add" and/or "git commit -a")
git@ise:~/your-usn-here/proj-6$ git add .
git@ise:~/your-usn-here/proj-6$ git commit -m "resolve merge conflict"
[master c818a0a] resolve merge conflict
git@ise:~/your-usn-here/proj-6$ git log --graph
* commit c818a0ad65b9033343cd51e54a5d3a019187c70c (HEAD -> master)
|\ Merge: 703a630 1a419c8
| | Author: username <user.name@example.com>
| | Date: Sat Oct 26 15:05:25 2024 +0530
| |
| | resolve merge conflict
| |
| * commit 1a419c84cf1cd921434468e7f060273ce89b3ec0 (feature-branch)
| | Author: username <user.name@example.com>
| | Date: Sat Oct 26 15:02:40 2024 +0530
| |
| | edit2 in feature-branch
| |
* | commit 703a6303111ca50963f8f4f5aeef2a247c99c8a6
|/ Author: username <user.name@example.com>
| Date: Sat Oct 26 14:56:37 2024 +0530
|
| edit in master
|
* commit 0cf8bb88b178773b48d50f3151387bb3b37f3535 (origin/master)
Author: username <user.name@example.com>
Date: Sat Oct 26 14:52:07 2024 +0530
first commit


LAB-7
Q7. Git Tags and Releases

Write the command to create a lightweight Git tag named “v1.0” for a commit in your local repository.

NOTE:  Do everything in local repository
Login with github account and create new repository and copy paste the readme.md content
Then, open local repository and type the below content
git@ise:~/p7$ gedit README.md
git@ise:~/p7$ git add README.md
git@ise:~/p7$ git commit -m "edit 1"
[master 7c453fd] edit 1
1 file changed, 1 insertion(+)
git@ise:~/p7$ git log
commit 7c453fdc9ad5498e51e1a439da1b45d59b947272 (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Sat Nov 23 15:48:10 2024 +0530
   edit 1
commit f20bacafa8d23cfaf368e475d64addbe64e82615 (origin/master)
Author: imama <imambasaha2021@gmail.com>
Date:   Sat Nov 23 15:45:53 2024 +0530
   first commit
git@ise:~/p7$ git tag v1.0 HEAD
or
git@ise:~/p7$ git tag v1.0 7c453fdc9ad5498e51e1a439da1b45d59b947272
git@ise:~/p7$ git tag –l
v1.0
git@ise:~/p7$ git push origin v1.0
Username for 'https://github.com': lala
Password for 'https://lala@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 260 bytes | 260.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/ambareeshgitlab/p7.git
* [new tag]         v1.0 -> v1.0
git@ise:~/p7$ git push -u origin master
Username for 'https://github.com': lala
Password for 'https://lala@github.com':
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/ambareeshgitlab/p7.git
  7c453fd..18c3b1f  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.


 LAB-8
 Q8. Advanced Git Operations

Write the command to cherry-pick a range of commits from “source-branch” to the current branch.

NOTE:  Do everything in local repository
git@ise:~/p8-2$ git init
Initialized empty Git repository in /home/git/p8-2/.git/
git@ise:~/p8-2$ git status
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
git@ise:~/p8-2$ gedit file1.txt // line-1 (master)
git@ise:~/p8-2$ git add file1.txt
git@ise:~/p8-2$ git commit -m "line-1 (master)"
[master (root-commit) 3a91448] line-1 (master)
1 file changed, 1 insertion(+)
create mode 100644 file1.txt 
git@ise:~/p8-2$ git log
commit 3a9144818de92a5689a823d113f9faf2b8dc4271 (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:49:09 2024 +0530
     line-1 (master)
git@ise:~/p8-2$ git checkout -b source-branch
Switched to a new branch 'source-branch'
git@ise:~/p8-2$ ls
file1.txt
git@ise:~/p8-2$ gedit file2.txt // line-1 (source)
git@ise:~/p8-2$ git add file2.txt
git@ise:~/p8-2$ git commit -m "add file2.txt"
[source-branch f4599dd] add file2.txt
1 file changed, 2 insertions(+)
create mode 100644 file2.txt 
git@ise:~/p8-2$ git log
commit f4599ddbf365796a26588c2b264fadf07afcb79d (HEAD -> source-branch)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:50:17 2024 +0530
   add file2.txt
commit 3a9144818de92a5689a823d113f9faf2b8dc4271 (master)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:49:09 2024 +0530
   line-1 (master)
git@ise:~/p8-2$ gedit file1.txt // append line-2 (source)
git@ise:~/p8-2$ git add file1.txt
git@ise:~/p8-2$ git commit -m "add line-2 to file1.txt"
[source-branch e0b298d] add line-2 to file1.txt
1 file changed, 1 insertion(+)
git@ise:~/p8-2$ git log
commit e0b298dd2e1034ff89815746e9fafe987b84c418 (HEAD -> source-branch)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:51:05 2024 +0530
   add line-2 to file1.txt
commit f4599ddbf365796a26588c2b264fadf07afcb79d
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:50:17 2024 +0530
   add file2.txt
commit 3a9144818de92a5689a823d113f9faf2b8dc4271 (master)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:49:09 2024 +0530
   line-1 (master)
git@ise:~/p8-2$ gedit file3.txt // line-1 (source)
git@ise:~/p8-2$ git add file3.txt
git@ise:~/p8-2$ git commit -m "add file3.txt"
[source-branch 96fed04] add file3.txt
1 file changed, 2 insertions(+)
create mode 100644 file3.txt 
git@ise:~/p8-2$ git log
commit 96fed046a708463e90317814b2160f762f5cd936 (HEAD -> source-branch)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:51:57 2024 +0530
   add file3.txt
commit e0b298dd2e1034ff89815746e9fafe987b84c418
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:51:05 2024 +0530
   add line-2 to file1.txt
commit f4599ddbf365796a26588c2b264fadf07afcb79d
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:50:17 2024 +0530
   add file2.txt
commit 3a9144818de92a5689a823d113f9faf2b8dc4271 (master)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:49:09 2024 +0530
   line-1 (master)
git@ise:~/p8-2$ git checkout master
Switched to branch 'master'
 
git@ise:~/p8-2$ git log
commit 3a9144818de92a5689a823d113f9faf2b8dc4271 (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:49:09 2024 +0530
   line-1 (master)
git@ise:~/p8-2$ git   cherry-pick  f4599ddbf365796a26588c2b264fadf07afcb79d^ ..e0b298dd2e1034ff89815746e9fafe987b84c418
On branch master
Cherry-pick currently in progress.
 (run "git cherry-pick --continue" to continue)
 (use "git cherry-pick --skip" to skip this patch)
 (use "git cherry-pick --abort" to cancel the cherry-pick operation)
nothing to commit, working tree clean
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:
   git commit --allow-empty
and then use:
   git cherry-pick --continue
to resume cherry-picking the remaining commits.
If you wish to skip this commit, use:
   git cherry-pick --skip
git@ise:~/p8-2$ git cherry-pick --skip
[master 6cf762e] add line-2 to file1.txt
Date: Mon Nov 25 10:51:05 2024 +0530
1 file changed, 1 insertion(+)
git@ise:~/p8-2$ git log
commit 6cf762e3a2cb6fcb73d2c79d43c9e9ad16fe44fb (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:51:05 2024 +0530
 
   add line-2 to file1.txt
commit 3a9144818de92a5689a823d113f9faf2b8dc4271
Author: imama <imambasaha2021@gmail.com>
Date:   Mon Nov 25 10:49:09 2024 +0530
   line-1 (master)
git@ise:~/p8-2$ ls
file1.txt


 LAB-9
 git@ise:~/p9$ git init 
Initialized empty Git repository in /home/git/p9/.git/

git@ise:~/p9$ gedit file1.txt

git@ise:~/p9$ git add file1.txt 

git@ise:~/p9$ git commit -m "Add file1.txt"
[master (root-commit) e73fa9d] Add file1.txt
 1 file changed, 2 insertions(+)
 create mode 100644 file1.txt

git@ise:~/p9$ gedit file2.txt

git@ise:~/p9$ git add file2.txt 

git@ise:~/p9$ git commit -m "Add file2.txt"
[master 2daa571] Add file2.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file2.txt

git@ise:~/p9$ git log
commit 2daa571cfabdb3148c9f10585c0dadf229ca0e86 (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 15:16:44 2024 +0530

    Add file2.txt

commit e73fa9d3431b010f5a3206bbe46b4ad8d27362d2
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 15:16:05 2024 +0530

    Add file1.txt

git@ise:~/p9$ git log --author="imama" --since="2024-11-20" --until="2024-11-28"
commit 2daa571cfabdb3148c9f10585c0dadf229ca0e86 (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 15:16:44 2024 +0530

    Add file2.txt

commit e73fa9d3431b010f5a3206bbe46b4ad8d27362d2
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 15:16:05 2024 +0530

    Add file1.txt

git@ise:~/p9$ git log -n 1 --pretty=format:"%h - %an, %ar : %s" e73fa9d3431b010f5a3206bbe46b4ad8d27362d2
e73fa9d - imama, 10 minutes ago : Add file1.txt

=========================================================



Program-10

git@ise:~/p9$ git log --author="imama" --since="2024-11-26" --until="2024-11-28"
commit 2daa571cfabdb3148c9f10585c0dadf229ca0e86 (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 15:16:44 2024 +0530

    Add file2.txt

commit e73fa9d3431b010f5a3206bbe46b4ad8d27362d2
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 15:16:05 2024 +0530

    Add file1.txt
===============================

Program - 11

git@ise:~/p11$ git init
Initialized empty Git repository in /home/git/p11/.git/
git@ise:~/p11$ gedit file.txt
git@ise:~/p11$ git add file.txt 
git@ise:~/p11$ git commit -m "Add file.txt"
[master (root-commit) b5a0816] Add file.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file.txt
git@ise:~/p11$ git commit --allow-empty -m "Empty-commit"
[master 1b3227a] Empty-commit
git@ise:~/p11$ git commit --allow-empty -m "Empty-commit"
[master 24f383c] Empty-commit
git@ise:~/p11$ git commit --allow-empty -m "Empty-commit"
[master 35e1907] Empty-commit
git@ise:~/p11$ git commit --allow-empty -m "Empty-commit"
[master ff8c3cc] Empty-commit
git@ise:~/p11$ git commit --allow-empty -m "Empty-commit"
[master 237e655] Empty-commit
git@ise:~/p11$ git commit --allow-empty -m "Empty-commit"
[master fff71d1] Empty-commit
git@ise:~/p11$ git commit --allow-empty -m "Empty-commit"
[master bd530f6] Empty-commit
git@ise:~/p11$ git log 
commit bd530f68bc8aca8c62c9f4e51cefcdc6755bb49d (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:02 2024 +0530

    Empty-commit

commit fff71d1af58a89715a09668c54178bf9e149e24f
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:01 2024 +0530

    Empty-commit

commit 237e655a7f0f717838c6bfff82d0f5b2bda07bdd
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:01 2024 +0530

    Empty-commit

commit ff8c3ccb439207f56875ec6f29477850cbb6687a
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:00 2024 +0530

    Empty-commit

commit 35e1907a75fd3e2fe69407b8149c28ddd57f4dad
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:00 2024 +0530

    Empty-commit

commit 24f383c690b614c434f1830e9566322fa91b7298
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:03:59 2024 +0530

    Empty-commit

commit 1b3227a1b067b32dad0728ad33bd1607c155abea
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:03:58 2024 +0530

    Empty-commit

commit b5a0816224baa2f3957e0bcc4e22e864e7c6c9c2
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:03:08 2024 +0530

    Add file.txt
git@ise:~/p11$ git log -n 4
commit bd530f68bc8aca8c62c9f4e51cefcdc6755bb49d (HEAD -> master)
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:02 2024 +0530

    Empty-commit

commit fff71d1af58a89715a09668c54178bf9e149e24f
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:01 2024 +0530

    Empty-commit

commit 237e655a7f0f717838c6bfff82d0f5b2bda07bdd
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:01 2024 +0530

    Empty-commit

commit ff8c3ccb439207f56875ec6f29477850cbb6687a
Author: imama <imambasaha2021@gmail.com>
Date:   Wed Nov 27 16:04:00 2024 +0530

    Empty-commit
git@ise:~/p11$ git log -n 4 --oneline
bd530f6 (HEAD -> master) Empty-commit
fff71d1 Empty-commit
237e655 Empty-commit
ff8c3cc Empty-commit

===================================================

Program-12

ise@ise:~/1MV23AI024/exp09$ git log
commit 8c3b3e6cd07afd25734f1cc1c186eba27bc312de (HEAD -> master)
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:05:05 2024 +0530

    Add file3.txt

commit 98aaf6f40b86049561fa17f9b033ae74e9732514
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:03:17 2024 +0530

    Add file2.txt

commit dda49fd3978f738546316174471087311a95b5b9
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:02:28 2024 +0530

    add file1.txt
ise@ise:~/1MV23AI024/exp09$ git revert 8c3b3e6cd07afd25734f1cc1c186eba27bc312de
Removing file3.txt
[master aaa8838] Revert "Add file3.txt" file3 reverted This reverts commit 8c3b3e6cd07afd25734f1cc1c186eba27bc312de.
 1 file changed, 1 deletion(-)
 delete mode 100644 file3.txt
ise@ise:~/1MV23AI024/exp09$ git log
commit aaa8838d114625770713395335b8ed19bc99f509 (HEAD -> master)
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:36:48 2024 +0530

    Revert "Add file3.txt"
    file3 reverted
    This reverts commit 8c3b3e6cd07afd25734f1cc1c186eba27bc312de.

commit 8c3b3e6cd07afd25734f1cc1c186eba27bc312de
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:05:05 2024 +0530

    Add file3.txt

commit 98aaf6f40b86049561fa17f9b033ae74e9732514
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:03:17 2024 +0530

    Add file2.txt

commit dda49fd3978f738546316174471087311a95b5b9
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:02:28 2024 +0530

    add file1.txt
ise@ise:~/1MV23AI024/exp09$ git reset --hard 8c3b3e6cd07afd25734f1cc1c186eba27bc312de
HEAD is now at 8c3b3e6 Add file3.txt
ise@ise:~/1MV23AI024/exp09$ git log
commit 8c3b3e6cd07afd25734f1cc1c186eba27bc312de (HEAD -> master)
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:05:05 2024 +0530

    Add file3.txt

commit 98aaf6f40b86049561fa17f9b033ae74e9732514
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:03:17 2024 +0530

    Add file2.txt

commit dda49fd3978f738546316174471087311a95b5b9
Author: sanshetty15 <sannidhishetty1510@gmail.com>
Date:   Mon Dec 2 14:02:28 2024 +0530

    add file1.txt


