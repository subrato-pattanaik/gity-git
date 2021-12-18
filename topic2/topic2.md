# Removing changes from the commit (undo commit)

The git also give us the ability to remove the changes from the commit. We use `git reset` to reset the commit and then remove the required changes and made a commit again. We can reset the commit with multiple flag and the most commonly used flag is `--soft`, `--hard` and `--mixed` (which is the default one).

### git reset --soft HEAD~1

This command will go one commit back and all the changes will be in **staged area** which is ready for the commit. We can also go two or more commit back to remove the changes by replacing `1` in `HEAD~1` with any number which we want to go behind.

### git reset --mixed HEAD~1

This command is similar to the previous one except that it will move all the changes in **unstaged area**.

### git reset --hard HEAD~1

This command we should never do this. This will remove the commit along with the changes from the working directory. We will lost the work that we did before. Please use this command cautiously.

Supposedly, we did hard reset the commit but later we want that commit back to our working directory. We use the same command to achieve this.

```
git reset --hard SHA
```

We can obtain the SHA value of the commit which has been reset hard using the following command.

```
git reflog
```

Git keeps track of updates to the tip of branches using a mechanism called reference logs, or "reflogs."

### Undo a commit which has already been pushed to the remote

Once a commit is pushed, you do NOT want to use git reset to undo it - because reset will rewrite the history tree, and anyone who has already pulled that branch will have a bad tree.

Instead, we'll use git revert to make a "revert commit" (like a merge commit), which will "undo" a specific commit. So the syntax is:

```
git revert SHA_Value_to undo
```
