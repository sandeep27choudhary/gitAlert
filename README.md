# :octocat: Sandeep27choudhary's Git Survival Guide :octocat:

Git is hard: screwing up is easy, and figuring out how to fix your mistakes is *fucking impossible*. Git documentation has this chicken and egg problem where you can't search for how to get yourself out of a mess unless you already know the name of the thing you need to know about in order to fix your problem.

So here are some bad situations I've gotten myself into, and how I eventually got myself out of them in plain English.

## :hourglass: Magic Time Machine

If you've royally screwed up and wish Git had a time machine:

```bash
git reflog
git reset HEAD@{index}
```

This is your lifeline for recovering lost changes or fixing disastrous messes.

:wrench: Quick Fixes

:pencil2: **Small Change After Commit**

Made a small mistake right after committing?

```bash
git add .
git commit --amend --no-edit
```

Voila! Your last commit is updated without a new one cluttering history.

:pencil: **Fixing Commit Message**

Regret your commit message?

```bash
git commit --amend
```

Follow the prompts to correct your mistake.

:twisted_rightwards_arrows: **Wrong Branch Commits**

Accidentally committed to the wrong branch?

```bash
git reset HEAD~ --soft
git stash
git checkout correct-branch
git stash pop
git add .
git commit -m "Your message here"
```

Your changes are safely relocated to the correct branch.

:rewind: **Undoing Changes**

:arrow_left: **Reverting Commit**

Need to undo a commit from a few commits back?

```bash
git log
git revert [commit-hash]
```

Git handles the reversal in a new commit.

:file_folder: **Undoing Changes to a File**

Made changes to a file you regret?

```bash
git log
git checkout [commit-hash] -- path/to/file
git commit -m "Undoing changes"
```

Old file version restored, no copy-pasting necessary.

:fire: **Discard Local Changes**

Want to throw away your local changes?

```bash
git checkout -- <file>
```

This command replaces the changes in your working directory with the last content in HEAD.

:leftwards_arrow_with_hook: **Reset Local Repository to a Previous Commit**

Need to reset your repository to a previous commit?

```bash
git reset --hard HEAD~1
```

This command will reset your HEAD to the previous commit, discarding any changes you made since that commit.

:arrows_counterclockwise: **Total Surrender**

When it all seems hopeless:

```bash
cd ..
sudo rm -r git-repo-dir
git clone https://github.com/some/repo.git git-repo-dir
```

A fresh start, courtesy of Eric V.

:warning: **Drastic Measures**

For truly catastrophic situations:

```bash
git fetch origin
git checkout master
git reset --hard origin/master
git clean -d --force
```

#### :white_check_mark: Useful Git Commands

#### :mag_right: Checking Status

Want to see which files have changed?

```bash
git status
```

This command provides an overview of modified, staged, and untracked files.

#### :bird: Creating a Branch

Starting a new feature or fixing a bug?

```bash
git checkout -b new-branch-name
```

This command creates a new branch and switches to it in one step.

#### :bookmark_tabs: Viewing Diffs

Curious about the changes you've made?

```bash
git diff
```

This command shows the differences between your working directory and the index (staging area).

#### :hourglass_flowing_sand: Stashing Changes

Need to temporarily set aside changes?

```bash
git stash
```

This command saves your modifications and reverts the working directory to match the HEAD commit.

#### :twisted_rightwards_arrows: Merging Branches

Ready to integrate changes from one branch to another?

```bash
git merge branch-name
```

This command combines changes from the specified branch into the current branch.

#### :arrows_counterclockwise: Rebasing Commits

Want a cleaner commit history?

```bash
git rebase branch-name
```

This command applies commits from the current branch onto the tip of another branch.

#### :file_folder: Removing Untracked Files

Cleaning up untracked files?

```bash
git clean -n
```

This command shows a preview of untracked files that would be removed. Add `-f` to execute the clean operation.

#### :mag_right: Searching Commit History

Looking for specific commits?

```bash
git log --grep="keyword"
```

This command filters commit history based on the specified keyword.

#### :arrows_counterclockwise: Cherry-Picking Commits

Need to pick specific commits from one branch to another?

```bash
git cherry-pick commit-hash
```

This command applies the changes introduced by the specified commits.

#### :twisted_rightwards_arrows: Interactive Rebase

Fine-tuning commit history?

```bash
git rebase -i HEAD~n
```

This command allows you to interactively rebase back to a specified number of commits.


But beware, these actions are irreversible.

:page_with_curl: **Disclaimer**

This guide is born of experience, with no claims to theoretical purity. Take it with a grain of salt, a dash of humor, and the understanding that Git can be a fickle beast.
``` ````
