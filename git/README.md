git gud @ git
-------------

Use `git status` whenever you are in trouble. Git will try to help you.


## Pulling

A default `git pull` consists of a `git fetch` and a `git merge`.  
This results in separate merge commits if fast-forwarding is impossible, thus tangling your `git log` further.  
Use `git rebase` instead of doing a merge to get a cleaner, more readable graph.  

`git rebase` simply takes commits that do not exist on the branch you rebase on (e.g. `master`) and "replays" them on top of the previous commits, appending the new commits to that branch's history.

## The nature of branches and commits

Branches are pointers to singular commits.  
Commits are a set of changes with a message (in simple terms) and pointers to parent commits (if any).  

Branch names and commit hashes can be used interchangably as long as they identify the same commit. Additionally, one may not need to use the full hash, the one found with `git log --oneline` should suffice.

Use `~N` to refer to the Nth commit behind the one specified before the operator.  
Use `^N` to refer to the Nth *parent* of the specified commit (numbered in a particular order).  
For both of these, the shorthands `~` and `^` may be used when N is 1 - and the operators can be combined in whatever way you please, as long as it corresponds to some path through your repo's history.

## Working with branches

**TODO:** branch and checkout and so on

## Acting on your sense of regret

`git revert` might not be the command you are looking for. It creates a new commit where the changes of *that particular commit* are undone.

`git reset` comes in three flavors and actually rewrites history back to the specified commit.
+ `--soft` only resets commits, leaving you with the changes made in them back in the staging area.
+ `--mixed` resets commits and their staged changes, leaving the files just as they are in your file system.
+ `--hard` is the one you probably will have to use. Resets your working directory, staging area *and* the commit(s) that have been made.

## Sharing your changes

`git add` adds the files matching your supplied expression to the staging area.  
`git commit` creates a commit with your staged changes.  
`git push` actually pushes the changes to the remote repo it is directed towards.  
*Please make sure to run a fetch + rebase/merge first, to not get rejected when pushing*

## Fixing conflicts

**They are inevitable.**  
It is bound to happen. Git is unable to automatically merge *all* sorts of intertwined changes to the same line in a file - and its creators do not trust it to do so. Git therefore asks *you*, the user, for assistance with the process of resolving such conlicts. Please be flattered by its humble request.

Now, here is the thing: They may look a little ugly and scary, but that is the intention. Let me illustrate:  
```
<<<<<<< HEAD (where you're at)
your changes
=======
their changes
>>>>>>> some branch or commit (where the conflicting change comes from)
```  
Nothing should be too scary about this, though. The strikingly weird arrows and lines are there to be just that - something that cannot possibly be acceptable code in a normal language (not counting things like [Fish](https://esolangs.org/wiki/Fish), obviously) and should immediately appear as *wrong* to just about anyone.

What to do with it?  
Simply remove the conflict markers and the changes you do not want to keep. Should be relatively straightforward.
