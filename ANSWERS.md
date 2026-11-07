# Assignment 3 — Scenario Answers

## 1. Merge Conflict

The conflicted block was:
```text
<<<<<<< HEAD
Mess timings: 8:00 AM to 9:30 AM
=======
Mess timings: 7:00 AM to 8:30 AM
>>>>>>> warden-update
```

- `<<<<<<< HEAD` indicates the changes in the current branch (main).
- `=======` separates the two conflicting versions.
- `>>>>>>> warden-update` indicates the changes coming from the warden-update branch.
Git could not automatically decide which version to keep, so I manually resolved the conflict to:
`Mess timings: 7:15 AM to 9:00 AM`

## 2. Reverting vs Resetting a Shared Commit

If the wrong "Holiday tomorrow" notice has already been shared, `git revert` is the correct choice because it creates a new commit that undoes the changes while preserving the existing commit history.
`git reset` changes the commit history by moving the branch pointer backwards. This can cause problems for other people who have already pulled the shared commits.
Therefore, `git revert` is safer for shared repositories.

## 3. Difference Between Soft, Mixed and Hard Reset

| Reset Type | Commit Removed? | Changes Staged? | Changes in Working Files? |
|---|---|---|---|
| --soft | Yes | Yes | Yes |
| --mixed | Yes | No | Yes |
| --hard | Yes | No | No |

- **Soft reset:** Removes the commit but keeps changes staged.
- **Mixed reset:** Removes the commit and unstages changes, but keeps them in the working directory.
- **Hard reset:** Removes the commit and discards changes from the staging area and working directory.

## 4. Recovering Work Using Git Reflog

If I accidentally lose work using `git reset --hard`, I can recover it using Git reflog.
Steps:
1. Run `git reflog` to view the history of HEAD movements.
2. Find the commit hash of the lost work (Draft 3).
3. Copy the commit hash.
4. Run `git reset --hard <commit-hash>` to restore the repository to that commit.
5. Run `git log --oneline` and `git status` to verify the recovery.

In this assignment, I recovered Draft 3 using:
`git reset --hard fd7cc1e`

## 5. Git Stash vs Quick WIP Commit

**When Git Stash is better:**
- When I have unfinished work but need to switch branches quickly.
- When I don't want incomplete changes in the commit history.
- When I want to temporarily save changes and continue later.

**When a Quick WIP Commit is better:**
- When I want to permanently save a checkpoint.
- When the work is important and I want it recorded in Git history.
- When I want to share my unfinished progress with teammates.

**Conclusion:**
Git stash is useful for temporarily saving unfinished work, while a WIP (Work In Progress) commit is useful for keeping a permanent checkpoint in the project history.