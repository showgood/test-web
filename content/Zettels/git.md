+++
title = "git"
author = ["showgood"]
lastmod = 2020-04-18T12:14:48-04:00
draft = false
+++

## git log {#git-log}


### concise output {#concise-output}

--oneline


### limit number of commits {#limit-number-of-commits}

-n {number of commits}


## check if a file is under git control {#check-if-a-file-is-under-git-control}

```sh
git ls-files <file> --error-unmatch
```

<https://stackoverflow.com/questions/2405305/how-to-tell-if-a-file-is-git-tracked-by-shell-exit-code>


## hide untracked file for git status {#hide-untracked-file-for-git-status}

```bash
git status -uno
```


## git: Your branch and 'origin/master' have diverged {#git-your-branch-and-origin-master-have-diverged}

Tonight I hit this error with my emacs config repo.

What caused error was this:

-   I have a feature branch `helpful`
-   I created PR from `helpful` to `master`
-   I `squashed` PR on github
-   I **forgot** to sync my working copy with github repo(ie. `origin`)
-   I made some other changes(even though there is no conflict with the changes from `helpful` branch)
-   I committed those changes in my working copy
-   I attempted to push those changes to `origin`, then hit the error

I solved it by following solution&nbsp;[^fn:1] :

```sh
git fetch origin
git reset --hard origin/master
```

but later I realized it's not best way, there should be a better way because I
actually lost those changes I made in my local working copy.

I think what I should have done is first **undo the last commit** in my local working copy,
then do the steps from&nbsp;[^fn:1] which would save my local changes.


## how to undo last commit {#how-to-undo-last-commit}

Best answer I think is from here&nbsp;[^fn:2]

> Undoing a commit is a little scary if you don't know how it works. But it's actually amazingly easy if you do understand.
>
> Say you have this, where C is your HEAD and (F) is the state of your files.
>
>    (F)
> A-B-C
>     ↑
>   master
> You want to nuke commit C and never see it again. You do this:
>
> git reset --hard HEAD~1
> The result is:
>
>  (F)
> A-B
>   ↑
> master
> Now B is the HEAD. Because you used --hard, your files are reset to their state at commit B.
>
> Ah, but suppose commit C wasn't a disaster, but just a bit off. You want to undo the commit but keep your changes for a bit of editing before you do a better commit. Starting again from here, with C as your HEAD:
>
>    (F)
> A-B-C
>     ↑
>   master
> You can do this, leaving off the --hard:
>
> git reset HEAD~1
> In this case the result is:
>
>    (F)
> A-B-C
>   ↑
> master
> In both cases, HEAD is just a pointer to the latest commit. When you do a git reset HEAD~1, you tell Git to move the HEAD pointer back one commit. But (unless you use --hard) you leave your files as they were. So now git status shows the changes you had checked into C. You haven't lost a thing!
>
> For the lightest touch, you can even undo your commit but leave your files and your index:
>
> git reset --soft HEAD~1
> This not only leaves your files alone, it even leaves your index alone. When you do git status, you'll see that the same files are in the index as before. In fact, right after this command, you could do git commit and you'd be redoing the same commit you just had.
>
> One more thing: Suppose you destroy a commit as in the first example, but then discover you needed it after all? Tough luck, right?
>
> Nope, there's still a way to get it back. Type git reflog and you'll see a list of (partial) commit shas that you've moved around in. Find the commit you destroyed, and do this:
>
> git checkout -b someNewBranchName shaYouDestroyed
> You've now resurrected that commit. Commits don't actually get destroyed in Git for some 90 days, so you can usually go back and rescue one you didn't mean to get rid of.

[^fn:1]: <https://stackoverflow.com/questions/19864934/git-your-branch-and-origin-master-have-diverged-how-to-throw-away-local-com/19864980#19864980>
[^fn:2]: <https://stackoverflow.com/questions/927358/how-to-undo-the-most-recent-commits-in-git>
