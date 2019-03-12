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

