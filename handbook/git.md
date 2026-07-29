# Git and GitHub

## Git Notes From Day 2

### git add .
Stages all changes inside the current repository.

Example: git add .

### git add ..
Tries to stage the parent directory.

This failed because the parent directory was outside my Git repository.

### git commit -am
Stages and commits changes only for files that Git is already tracking.

Important:

git commit -am does not add brand-new files.

For new files, I need to use git add first.

## Git Fundamentals

### git status
Shows the current state of the repository.

It tells me:
- What files changed
- What files are staged
- What files are untracked
- Whether the working tree is clean

### git diff
Shows the exact changes made before the staging.

### git diff --staged
Shows the exact changes that are staged and ready to be committed.

### git add
Stages files for the next commit.

Example: git add README.md

### git add .
Stages all changes inside the current repository.

### git commit -m
Creates a saved checkpoint with a message.

Example: git commit -m "add academy readme"

### git log --oneline --graph
Shows commit history in a short visual format.

### git restore
Discard unwanted local changes and returns a file to the last committed version.

Example: git restore README.md

### .gitignore
Tells Git which files or patterns to ignore.

Example:

*.log
.env

Before comitting, I should review my changes with:

git status
git diff
git diff --staged

This helps prevent bad commits and accidental mistakes.

## GitHub Connection

### Local Repository
A local repository is the Git project stored on my computer.

Example:
/home/juan/sdet-academy

### Remote Repository
A remote repository is the Git project stored on GitHub.

Example:
github.com/JuanCamilo012599/sdet-academy

### origin
origin is the default name Git uses for the remote repository.

### git remote -v
Shows the remote repositories connected to my local project.

Example:
git remote -v

### git remote add origin
Connects a local repository to a remote repository for the first time.

Example:
git remote add origin git@github.com:username/repo.git

### git remote set-url origin
Changes the URL of an existing remote

I used this when my origin was set to HTTPS and I wanted to switch it to SSH

Example:
git remote set-url origin git@github.com:JuanCamilo012599/sdet-academy.git

### SSH Authentication
SSH allows my computer to authenticate with GitHub using a key pair.

Private key: id_ed25519

Public key: id_ed25519.pub

Important:

The private key should never be shared.
The public key is safe to add to GitHub.

### ssh -T git@github.com
Test if my SSH connection on GitHub works.

### git push -u origin main
Pushes my local main branch to GitHub and sets it to track origin/main

### origin/main
origin/main represents the main branch that lives on GitHub

## GitHub Lesson

A professional Git workflow is:

1. Make changes locally
2. Review changes with git status and git diff
3. Commit changes locally
4. Push commits to GitHub

After the first push, I can usually use:

git push

## GitHub Workflow and Sync

### git pull
Downloads new commits from the remote repository and updates my local branch.

I should usually run this before starting work.

Example:

git pull

### git push
Uploads my local commits to the remote repository on GitHub

Example:
git push

### Local branch
The branch on my computer

Example:

main

### Remote branch
The branch on GitHub

Example: origin/main

### Up to date
When Git says my branch is up to date with origin/main, it means my local branch and GitHub are both synchronized

### Ahead of origin/main
When Git says my branch is ahead of origin/main, it means I have local commits that have not been pushed to GitHub yet

### Behind origin/main
When Git says my branch is behind origin/main, it means GitHub has commits that my local machine does not have yet

### Sync Workflow

Before working:

git pull

After working:

git status
git diff
git add .
git diff --staged
git commit -m "clear message"
git push

## Fetch vs Pull, and Handling Diverged Branches

### git fetch
Downloads new commits/branch info from the remote and updates your local copy of the remote-tracking branch 
Example: 
`origin/main` 
It does NOT touch your own local branch or working directory. Fully safe, no merge.

### git pull 
Runs `git fetch`, then tries to integrate those changes into your current local branch (merge or rebase, depending on config/flags)

Status meanings (`git status` after a fetch):

- **ahead**: your local branch has commits `origin/main` doesn't have yet.

- **behind**: `origin/main` has commits your local branch doesn't have yet — usually a clean fast-forward.

- **diverged**: both sides have commits the other doesn't have. This is about commit history shape only, decided before any merge is attempted.

- **Merge conflict**: happens when git tries to merge diverged histories and finds the same lines changed differently on both sides — it can't auto-pick, so it stops and asks you to.

Resolving a conflict:

1. `git status` — shows conflicted files as "both modified"

2. Open the file, find the markers:
`<<<<<<< HEAD` (your local version)
`=======` (divider) /
`>>>>>>> <commit-hash>` (incoming version)

3. Edit to the final content you want, delete all three marker lines

4. `git add <file>` — marks it resolved

5. `git commit` — completes the merge (opens editor with an auto-generated merge message)

6. `git push`.

## Branching in Git

### git branch
Lists every local branch, with `*` marking whichever one I'm currently working on

Example: where `HEAD` points

### git branch <name>
Creates a new branch pointing at my current commit, but does not move me onto it. I stay on whatever branch i'm currently at

### git switch <name>
moves `HEAD` onto the name branch, so my working directory now reflects that branch's files/history. Note:
(git checkout <name> does the same job — it's the older command, but it's overloaded with other unrelated uses, so switch is the newer, purpose-built one)


### Why branches exist???

So I can isolate in-progress work from `main.`. If I commit unfinished/broken work directly to `main`, anyone who pulls gets that broken code and is blocked until it's fixed - WORSE if `main` auto-deploys to production. A `branch` is a private space to commit freely until the work is ready to merge in


### git merge <branch>
Brings another branch's commits into my current branch. If my current branch (e.g. `main`) hasn't moved since the other branch was created, Git just slides the pointer forward -- That's called a fast-forward merge, no new commit needed. If both branches have separate commits since they split (diverged), Git creates an actual merge commit with two parents instead (Like the one from day-006)

### git branch -d <name>
Deletes a local branch, but only if it's already fully merged (safe default; refuses otherwise)
Note: `git branch -d` checks whether the branch's commits are reachable from its tracked upstream (or from HEAD if there's no upstream), it never checks against `main` directly.

#### Day 008 PR Practice — why git branch -d didn't warn me

1. Branch creation & push

I created day-008-pr-practice, committed locally
git push -u origin day-008-pr-practice
-u sets upstream tracking: local branch ↔ origin/day-008-pr-practice (identical commit history at this point)

2. Squash-merge on GitHub

PR merged via squash → creates one new commit on main
That new commit has the combined content but no parent link to my branch's original commits
Git sees my original commits and the new squashed commit as historically unrelated, even though the diff looks the same

3. Local branch delete

git branch -d day-008-pr-practice
-d asks exactly one question: "are this branch's commits reachable from its own upstream (origin/day-008-pr-practice)?"
Answer: yes — nothing changed there → Git considers it safe → deletes

4. The actual gap

-d never checks reachability from main
After a squash-merge, my commits are not reachable from main (main only has the new synthetic commit)
That check simply isn't part of -d's logic — so no warning, even though this is the case that matters

#### Core Take Away
-d's safety check answers: "is this preserved on its own upstream?"
What I actually need answered: "is this preserved on main?"
Squash-merge is the exact scenario where those two questions diverge — content is preserved, history/reachability is not.

### git branch -D <name>
Force-deletes regardless of merge status; can strand commits that are only reachable from that branch (effectively lose them unless you still remember the commit hash)

### git push -u origin <branch>
Pushes a branch to GitHub for the first time, and the `-u` sets up "tracking" so future plain `git push/git pull` on that branch know where to sync without needing the full `origin <branch>` spelled out

### git push origin --delete <branch>
Deletes a branch on GitHub. This is separate from `git branch -d` -- deleting locally does not delete it on GitHub, and vice versa; each side has to be told separately

### What's a pull request?
PR compares tha base of both Branches and is used as a second pair of eyes for review before it lands on MAIN.
it's used instead of plain merge because there could be other coder's that have to review the actual changes

### Commit message convention: 
it'll be the title of our commit, has to be precise and let us know exactly what happened there. 
Rule:  first line ≤50 characters, written in imperative mood (like a command — "add x," not "added x").

### Merge Strategies:
1. Merge commit — every commit from my branch stays exactly as-is, plus Git adds one new commit that ties the two histories together.
2. Squash and merge — all commits on my branch get combined into a single new commit on the base branch.
3. Rebase and merge — My branch's commits get replayed one-by-one directly onto the tip of the base branch, in order, with no merge commit at all. (not practiced yet)
