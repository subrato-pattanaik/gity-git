# Change a commit message

In this topic, we wil cover vaious ways/methods of rewriting or altering git history/commit before pushing the commit/history to remote. The git provide mainly three 3 ways/mechanism for storing history(means rewriting commit message) and saving changes (add changes to previous commit). The mechanism inculdes:

- Commit --amend
- git rebase
- git reflog

Lets see each of them in details.

### git commit --amend

The `git commit --amend` is the most convenient way of rewriting the **most recent commit**. It performs two operation.

- It lets you combine the staged changes with the previous commit. If you forget to add a stage file, then this command is useful.
- If we want, we can rewrite the commit history message with the new one. Sometimes we need to do it, if we did some typos or changed semantics of the commit message/history, then this command will let you to rewrite the commit history.

You can use any one of the following way of using `--amend` flag to edit the commit message.

```git
1. git commit --amend -m  "new message"
2. git commit --amend
3. git commit --amend --no-edit
```

The third command (amend flag with no editor option) allows us to add staged file in the previous commit without changing the commit message/history.

Some helpful commands

```
git log --oneline
```

### git rebase --interactive SHA^

This command allows to make changes/modify on the older commit(s) with interactive rebase. This create the freedom to correct errors, refine your work, while still maintaining the clean git history without leaving any messy trail.

```
git rebase -i SHA^
```

SHA^ represent the sha value of the commit which you want to add stage files in that commit.

Adding `edit` or `e` command will pause the rebase process/playback on the commit and it will allow you to make changes on the same commit using `git commit --amend`. Once we are satisfied with the commit we can run the following command to continue/play the rebase process.

```
git rebase --continue
```

_Remember, you should use the above commands only when all your commits is not yet pushed to the remote. If we want to change the commit which has been already pushed, then you need to add `--force` or `-f` flag when we push the commits to remote._

**WE'LL SEE THE LAST MECHANISM TO REWRITING OR ALTERTING HISTORY LATER**.
