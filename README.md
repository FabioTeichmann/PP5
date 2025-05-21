# PP5

## Goal

In this exercise you will:

* Use Git **locally** on your own machine: create branches, make commits, and merge them back.
* Set up and interact with a **bare** Git repository on an SSH‐accessible server (e.g. **vorlesungsserver**, or any machine you have SSH access to).
* Push and pull to/from **GitHub** and the **THGA GitLab** server.
* Practice **forking** an existing repo, making changes, and submitting a **Pull Request** (on GitHub) or **Merge Request** (on GitLab).

**Important:** Start a stopwatch when you begin and work uninterruptedly for **90 minutes**. Once time is up, stop immediately and document exactly where you had to pause.

---

## Workflow

1. **Fork** this repository
2. **Modify & commit** your solution
3. **Submit your link for Review**

---

## Prerequisites

* Several starter repos are available here:
  [https://github.com/orgs/STEMgraph/repositories?q=Git%3A](https://github.com/orgs/STEMgraph/repositories?q=Git%3A)
* Ensure you have **SSH access** to a remote server (e.g., “vorlesungsserver”).
* Throughout, consult Git’s built-in man-pages (`git help <command>`) for explanations and options.

---

## Tasks

### Task 1: Local Git – Branching & Merging

1. Create a new directory in your home directory and initialize a repository in it. 
2. In one of your cloned repos, initialize a new branch called `feature-1`.
3. On `feature-1`, create a file `feature.txt` containing a short description of what you’re doing.
4. Commit your changes, then switch back to `master` (or `main`), and merge `feature-1` into your `master`.
5. Resolve any merge conflicts (if they arise) by hand, then commit the merge. 

**Your Commands & Output**

```bash
# Paste here the sequence of git commands you ran
# and the relevant terminal output (e.g., branch listing, merge messages)
```
Aufgabe 1:

fabioteichmann@Flipbook:/mnt/c/WINDOWS/system32$ mkdir ~/git-uebung
mkdir: cannot create directory ‘/home/fabioteichmann/git-uebung’: File exists
fabioteichmann@Flipbook:/mnt/c/WINDOWS/system32$ mkdir ~/git-uebung-neu
mkdir: cannot create directory ‘/home/fabioteichmann/git-uebung-neu’: File exists
fabioteichmann@Flipbook:/mnt/c/WINDOWS/system32$ mkdir ~/neue-git-uebung
fabioteichmann@Flipbook:/mnt/c/WINDOWS/system32$ cd ~/neue-git-uebung
fabioteichmann@Flipbook:~/neue-git-uebung$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /home/fabioteichmann/neue-git-uebung/.git/
fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout -b feature-1
Switched to a new branch 'feature-1'
fabioteichmann@Flipbook:~/neue-git-uebung$ echo "Das ist eine neue Funktion." > feature.txt
fabioteichmann@Flipbook:~/neue-git-uebung$ git add feature.txt
fabioteichmann@Flipbook:~/neue-git-uebung$ git comit -m "add feature.txt with description"
git: 'comit' is not a git command. See 'git --help'.

The most similar command is
        commit
fabioteichmann@Flipbook:~/neue-git-uebung$ git commit -m "add feature.txt with description"
[feature-1 (root-commit) 1539ba1] add feature.txt with description
 Committer: fabioteichmann <ö.>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly:

    git config --global user.name "Your Name"
    git config --global user.email you@example.com

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout master
error: pathspec 'master' did not match any file(s) known to git
fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout -b master
Switched to a new branch 'master'
fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout feature-1
Switched to branch 'feature-1'
fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout master
Switched to branch 'master'
fabioteichmann@Flipbook:~/neue-git-uebung$ git merge feature-1
Already up to date.
fabioteichmann@Flipbook:~/neue-git-uebung$ git config --global user.name "Teichmann"
fabioteichmann@Flipbook:~/neue-git-uebung$ git config --global user.email "fabio.teichmann@stud.thga.de"
fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout master
Already on 'master'
fabioteichmann@Flipbook:~/neue-git-uebung$ git merge feature-1
Already up to date.
fabioteichmann@Flipbook:~/neue-git-uebung$
---

### Task 2: Bare Repository on an SSH Server

1. On your SSH server (e.g., “vorlesungsserver”), create a **bare** repo at `~/repos/myproject.git`:

   ```bash
   ssh youruser@vorlesungsserver \.
     "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"
   ```
2. On your local machine, add it as a remote named `origin-ssh`:

   ```bash
   git remote add origin-ssh youruser@vorlesungsserver:~/repos/myproject.git
   ```
3. Push your `master` branch to `origin-ssh`, then clone it into a fresh directory to verify.

**Your Commands & Output**

```bash
# Paste here the push & clone commands and outputs
```
Aufgabe 2:

fabioteichmann@Flipbook:~/neue-git-uebung$ ssh user94@128.140.85.215 \
>
user94@128.140.85.215's password:
You are required to change your password immediately (administrator enforced).
You are required to change your password immediately (administrator enforced).
Linux vorlesung 6.1.0-21-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.90-1 (2024-05-03) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Mon May 19 17:17:48 2025 from 87.123.196.55
WARNING: Your password has expired.
You must change your password now and login again!
Changing password for user94.
Current password:
New password:
Retype new password:
passwd: password updated successfully
Connection to 128.140.85.215 closed.

fabioteichmann@Flipbook:~/neue-git-uebung$ ls ~
file.txt  git-Test  git-uebung  git-uebung-neu  meinprojekt-test  neue-git-uebung  repos  snap
fabioteichmann@Flipbook:~/neue-git-uebung$ git remote add origin-ssh user94@vorlesung:~/repos/meinprojekt.git
fabioteichmann@Flipbook:~/neue-git-uebung$ git remote -v
origin-ssh      user94@vorlesung:~/repos/meinprojekt.git (fetch)
origin-ssh      user94@vorlesung:~/repos/meinprojekt.git (push) 
fabioteichmann@Flipbook:~/neue-git-uebung$ git remote set-url origin-ssh user94@128.140.85.215:~/repos/meinprojekt.git
fabioteichmann@Flipbook:~/neue-git-uebung$ git push origin-ssh master
user94@128.140.85.215's password:
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 253 bytes | 253.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To 128.140.85.215:~/repos/meinprojekt.git
 * [new branch]      master -> master
fabioteichmann@Flipbook:~/neue-git-uebung$
---

### Task 3: GitHub & THGA GitLab

1. On [GitHub](github.com), create a new empty repo under your account named `myproject-gh`.
2. On [THGA GitLab](gitlab.thga.de), create a new project named `myproject-gl`.
3. In your local repository, add these as remotes:

   ```bash
   git remote add github  git@github.com:YOUR_USERNAME/myproject-gh.git
   git remote add gitlab  git@gitlab.thga.de:YOUR_USERNAME/myproject-gl.git
   ```
4. Push your `master` branch to both `github` and `gitlab` remotes.

> Hint: You are just adding two more bare-remotes to your already existing repository!

**Your Commands & Output**

```bash
# Paste here the remote‐adding & push outputs
```
Aufgabe 3:

fabioteichmann@Flipbook:~/neue-git-uebung$ git remote add github git@github.com:Flipbook/myproject-gl.git
fabioteichmann@Flipbook:~/neue-git-uebung$ git remote add gitlab git@gitlab.thga.de:fabio.teichmann/myproject-gl.git
fabioteichmann@Flipbook:~/neue-git-uebung$ git remote -v
github  git@github.com:Flipbook/myproject-gl.git (fetch)
github  git@github.com:Flipbook/myproject-gl.git (push)
gitlab  git@gitlab.thga.de:fabio.teichmann/myproject-gl.git (fetch)
gitlab  git@gitlab.thga.de:fabio.teichmann/myproject-gl.git (push)
origin-ssh      user94@128.140.85.215:~/repos/meinprojekt.git (fetch)
origin-ssh      user94@128.140.85.215:~/repos/meinprojekt.git (push)
fabioteichmann@Flipbook:~/neue-git-uebung$ git push github master
Enter passphrase for key '/home/fabioteichmann/.ssh/id_ed25519':
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 253 bytes | 84.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:Flipbook/myproject-gh.git
 * [new branch]      master -> master
 * 
fabioteichmann@Flipbook:~/neue-git-uebung$ git push gitlab master
Enter passphrase for key '/home/fabioteichmann/.ssh/id_ed25519':
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 253 bytes | 63.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: To create a merge request for master, visit:
remote:   https://gitlab.thga.de/fabio.teichmann/meinprojekt-gl/-/merge_requests/new?merge_request%5Bsource_branch%5D=master
remote:
To gitlab.thga.de:fabio.teichmann/meinprojekt-gl.git
 * [new branch]      master -> master
---

### Task 4: Fork, Modify, and Pull/Merge Request

1. On GitHub, **fork** one of the repos from the STEMgraph org.
2. Clone your fork locally, create a branch `pp5-changes`, and make a small change (e.g., update the README).
3. Commit and push `pp5-changes` to **your** fork, then open a **Pull Request** against the original repo.
4. Repeat on THGA GitLab: fork another students repository, clone, branch, change, push, and open a **Merge Request**. If your peers opened a merge request to your repository, review and merge or decline it!

**Your PR/MR Links & Descriptions**

* GitHub PR: *paste URL and a one-sentence summary*
* GitLab MR: *paste URL and a one-sentence summary*

---
Aufgabe 4:

fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout -b feature-2
Switched to a new branch 'feature-2'
fabioteichmann@Flipbook:~/neue-git-uebung$ echo "Die zweite Funktion." >feature2.txt
fabioteichmann@Flipbook:~/neue-git-uebung$ git add feature2.txt
fabioteichmann@Flipbook:~/neue-git-uebung$ git commit -m "Add feature2.txt with second feature description"
[feature-2 9651f0a] Add feature2.txt with second feature description
 1 file changed, 1 insertion(+)
 create mode 100644 feature2.txt
fabioteichmann@Flipbook:~/neue-git-uebung$ git checkout master
Switched to branch 'master'
fabioteichmann@Flipbook:~/neue-git-uebung$ git merge feature-2
Updating 1539ba1..9651f0a
Fast-forward
 feature2.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature2.txt
fabioteichmann@Flipbook:~/neue-git-uebung$ git push origin-ssh master
user94l@128.140.85.215's password:
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 318 bytes | 63.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To 128.140.85.215:~/repos/meinprojekt.git
   1539ba1..9651f0a  master -> master
fabioteichmann@Flipbook:~/neue-git-uebung$ git push github master
Enter passphrase for key '/home/fabioteichmann/.ssh/id_ed25519':
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 318 bytes | 318.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:Flipbook/myproject-gh.git
   1539ba1..9651f0a  master -> master
fabioteichmann@Flipbook:~/neue-git-uebung$ git push gitlab master
Enter passphrase for key '/home/fabioteichmann/.ssh/id_ed25519':
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 318 bytes | 106.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: To create a merge request for master, visit:
remote:   https://gitlab.thga.de/fabioteichmann/meinprojekt-gl/-/merge_requests/new?merge_request%5Bsource_branch%5D=master
remote:
To gitlab.thga.de:fabio.teichmann-/meinprojekt-gl.git
   1539ba1..9651f0a  master -> master

**Remember:** Stop working after **90 minutes** and record where you stopped!
