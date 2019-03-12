# Basic repo to play and experiment with git commands as I learn them.

Git Submodules
```
Richins-MBP:git-helloworld richinjain$ git submodule add git@github.com:fastai/fastai.git lib/fastai
Cloning into '/Users/richinjain/git-helloworld/lib/fastai'...
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 27069 (delta 1), reused 2 (delta 0), pack-reused 27056
Receiving objects: 100% (27069/27069), 391.67 MiB | 9.14 MiB/s, done.
Resolving deltas: 100% (19407/19407), done.
```
```
Richins-MBP:git-helloworld richinjain$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   .gitmodules
	new file:   lib/fastai
```

```
Richins-MBP:git-helloworld richinjain$ cat .gitmodules 
[submodule "lib/fastai"]
	path = lib/fastai
	url = git@github.com:fastai/fastai.git
Richins-MBP:git-helloworld richinjain$ 
```

```
Richins-MBP:fastai richinjain$ pwd
/Users/richinjain/git-helloworld/lib/fastai
Richins-MBP:fastai richinjain$ 
Richins-MBP:fastai richinjain$ 
Richins-MBP:fastai richinjain$ git log
commit 9a123c36f9a8df82445f2843ec87c917b8a901bf (HEAD -> master, origin/master, origin/HEAD)
Author: Stas Bekman <stas@stason.org>
Date:   Mon Mar 11 18:39:42 2019 -0700

    let's try to always save test registry (unconditionally)

commit 8b12be9d19cd778c1afef5ebc20a344865efa6b8
Author: Stas Bekman <stas@stason.org>
Date:   Mon Mar 11 18:39:28 2019 -0700

```

```
Richins-MBP:fastai richinjain$ 
Richins-MBP:fastai richinjain$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/ImageCleaner
  remotes/origin/ci
  remotes/origin/fp16
  remotes/origin/master
  remotes/origin/release-1.0.10
  remotes/origin/release-1.0.11
  remotes/origin/release-1.0.12
  remotes/origin/release-1.0.13
  remotes/origin/release-1.0.14
  remotes/origin/release-1.0.15
```

```
Richins-MBP:git-helloworld richinjain$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   .gitmodules
	new file:   lib/fastai

Richins-MBP:git-helloworld richinjain$ git commit -m "Adding submodules"
[master 615a0fa] Adding submodules
 2 files changed, 4 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 lib/fastai
Richins-MBP:git-helloworld richinjain$ git push
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 421 bytes | 421.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0)
To github.com:jainr/git-helloworld.git
   44d881a..615a0fa  master -> master
Richins-MBP:git-helloworld richinjain$ 
```

## Create GitHub PR with only a specific commit
Create a new branch based off the branch you want to merge to, cherry pick your change in this branch and commit this branch

Made two commits to testbranch but only want the commit with file1 to be part of PR
```
Richins-MBP:git-helloworld richinjain$ git log
commit 7064bb7935ed158b5ef42f8459eefde56a843e4b (HEAD -> testbranch, origin/testbranch)
Author: Richin Jain <rijai@microsoft.com>
Date:   Mon Mar 11 22:05:36 2019 -0400

    Adding file2

commit 55516c17c79e254727aa478738baddd71847d0a7
Author: Richin Jain <rijai@microsoft.com>
Date:   Mon Mar 11 22:05:02 2019 -0400

    Adding file 1
```

```
Richins-MBP:git-helloworld richinjain$ git checkout -b file1branch origin/master
Branch 'file1branch' set up to track remote branch 'master' from 'origin'.
Switched to a new branch 'file1branch'
Richins-MBP:git-helloworld richinjain$ 
Richins-MBP:git-helloworld richinjain$ git cherry-pick 55516c17c79e254727aa478738baddd71847d0a7
[file1branch 88b02cf] Adding file 1
 Date: Mon Mar 11 22:05:02 2019 -0400
 2 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 file1.txt
Richins-MBP:git-helloworld richinjain$ git push -u origin file1branch
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 388 bytes | 388.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'file1branch' on GitHub by visiting:
remote:      https://github.com/jainr/git-helloworld/pull/new/file1branch
remote: 
To github.com:jainr/git-helloworld.git
 * [new branch]      file1branch -> file1branch
Branch 'file1branch' set up to track remote branch 'file1branch' from 'origin'.
```

## How to keep Github email private
Go to settings on GitHub, then click email, select the option here to keep email address private
```
Keep my email address private
We’ll remove your public profile email and use jainr@users.noreply.github.com when performing web-based Git operations and sending email on your behalf. If you want command line Git operations to use your private email you must set your email in Git.
```

# Checkout a branch that's not visible on your local
Do git pull origin to first pull all the remotes.
```
Richins-MBP:richinjain$ git pull origin
remote: Enumerating objects: 79, done.
remote: Counting objects: 100% (79/79), done.
remote: Compressing objects: 100% (35/35), done.
remote: Total 79 (delta 46), reused 75 (delta 42), pack-reused 0
Unpacking objects: 100% (79/79), done.
 * [new branch]      jiata-benchmark     -> origin/jiata-benchmark
 * [new branch]      loomlike-products -> origin/loomlike-msproducts
   490ff8e..994abad  service_deploy      -> origin/service_deploy
 * [new branch]      workspace_setup     -> origin/workspace_setup
 ```