# Push current branch to remote

Push the current branch to the remote repository.

## Instructions

1. Run `git status` to confirm the branch and check for unpushed commits
2. If the branch has no upstream, push with `-u` to set tracking:
   ```bash
   git push -u origin HEAD
   ```
3. If the branch already tracks a remote, push normally:
   ```bash
   git push
   ```
4. Report the result to the user

## Important

- Never force push unless explicitly asked
- Never push directly to `main` or `master` — warn the user if on those branches
