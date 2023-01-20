# git
Git terminal commands

## git commit

To save your work and exit press Esc and then :wq (w for write and q for quit).

Alternatively, you could both save and exit by pressing Esc and then :x

To set another editor run export EDITOR=myFavoriteEdioron your terminal, where myFavoriteEdior can be vi, gedit, subl(for sublime) etc.

## Resolving merge conflicts

Generate a list of the files affected by the merge conflict. In this example, the file styleguide.md has a merge conflict.

$ git status
 # On branch branch-b
 # You have unmerged paths.
 #   (fix conflicts and run "git commit")
 #
 # Unmerged paths:
 #   (use "git add ..." to mark resolution)
 #
 # both modified:      styleguide.md
 #
 no changes added to commit (use "git add" and/or "git commit -a")
Open your favorite text editor, such as Visual Studio Code, and navigate to the file that has merge conflicts.

To see the beginning of the merge conflict in your file, search the file for the conflict marker <<<<<<<. When you open the file in your text editor, you'll see the changes from the HEAD or base branch after the line <<<<<<< HEAD. Next, you'll see =======, which divides your changes from the changes in the other branch, followed by >>>>>>> BRANCH-NAME. In this example, one person wrote "open an issue" in the base or HEAD branch and another person wrote "ask your question in IRC" in the compare branch or branch-a.

If you have questions, please
#<<<<<<< HEAD
open an issue
# =======
ask your question in IRC.
# >>>>>>> branch-a
Decide if you want to keep only your branch's changes, keep only the other branch's changes, or make a brand new change, which may incorporate changes from both branches. Delete the conflict markers <<<<<<<, =======, >>>>>>> and make the changes you want in the final merge. In this example, both changes are incorporated into the final merge:

If you have questions, please open an issue or ask in our IRC channel if it's more urgent.
Add or stage your changes.

$ git add .
Commit your changes with a comment.

$ git commit -m "Resolved merge conflict by incorporating both suggestions."
You can now merge the branches on the command line or push your changes to your remote repository on GitHub and merge your changes in a pull request.


Git show branch

git show-branch --list --topo-order

git log --graph --pretty=online --abbrev-commit


#Show git status

git status | grep deleted 

#Add only deleted files
git ls-files --deleted | xargs git add

git ls-files --deleted -- lib/foo | xargs git add

Search commits by commit message

git log --all --grep='Build 0051'

To search the actual content of commits through a repo's history, use:

git grep 'Build 0051' $(git rev-list --all)

Finally, as a last resort in case your commit is dangling and not connected to history at all, you can search the reflog itself with the -g flag (short for --walk-reflogs:

git log -g --grep='Build 0051'

Get commit by id
git cherry-pick <commit>

Git stash 

View saved stashes
Where WIP stands for work in progress

git stash list

To provide more context to stash than using just wip id it's possible to add name for stash

git stash save "stash comment"

Add stash using flags
- -u add also untracked files to stash
- -a add all files also ignored files

Applying stash
Popping stash removes it from stashes and applying to working branch

git stash pop 
git stash pop stash@{2}

Alternatively it's possible reapply the chenges to working branch and keep stash

git stash apply
git stash apply stash@{2}

To see stash changes

git stash show
git stash show stash@{4}

To view the full diff of a stah pass flag -p (--patch)

git stash show -p 
git stash show -p stash@{2}

Add just staged
git stash push --staged -m "comment"

Createing a branch from stash

git stash branch branch_name stash@{3}

Cleaning up your stash
git stash drop stash@{1}

Or delete all of stashes

git stash clear
 
 
Restore removed files from previous commits

git checkout <commit>~1 files_pathes



