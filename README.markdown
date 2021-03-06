About
=====

`git-mass` executes specific `git` commands over a set of directories where each subdirectory is an independent Git repo.

Commands
========

List Module
-----------

List all subdirectories

    ./git-mass list
    
Checkout
--------

Switches all subdirectories to a specific branch. Example, which switches all subdirectories to `gl-0` branch:

    ./git-mass checkout gl-0   

Pull & Rebase
-------------

Updates the specific subdirectory with the most-recent changes (via `pull --rebase`).

    ./git-mass pull-rebase
   

Full Merge
----------
Executes a merge from a specified branch to target branch. Before merging, updates the specific subdirectory with the most-recent changes (via `pull --rebase`).

### Full Merge (without push)

	./git-mass full-merge -m "GL-0 Merge 'gl-0' to 'master'" gl-0 master

### Full Merge & Push

	./git-mass full-merge -p -m "GL-0 Merge 'gl-0' to 'master'" gl-0 master

Last Commit Date
---------------

Shows last commit dates on each subdirectory

    ./git-mass last-commit-date

Forward diff between two branches
---------------------------------

Shows whether a specific branch is behind another branch, so it can be merged.

    ./git-mass fwdiff dev master

Output:

    ./backend/> dev is behind master

Changed files between branches
------------------------------

Indicates which files have been changed between branches.

    ./git-mass namediff dev master

Internally, the `git diff --name-only` is used.

Cleanup unchanged branches
--------------------------
Remove feature branch that has no changes against master / production
branch.

    ./git-mass cleanup-unchanged-branches master dev

Suppose that module contains 'dev' branch which has
no changes against 'master'. In this case, it can be cleaned
and removed.

This command is useful when removing feature branches that have
been not used:

    ./git-mass cleanup-unchanged-branches master gl-0

Hard Reset
-----------

Hard-resets each subdirectory to the specific branch:

    ./git-mass reset-hard origin/master