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

But beware, these actions are irreversible.

:page_with_curl: **Disclaimer**

This guide is born of experience, with no claims to theoretical purity. Take it with a grain of salt, a dash of humor, and the understanding that Git can be a fickle beast.
``` ````
