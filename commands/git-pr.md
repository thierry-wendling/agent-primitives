# Create a pull request

Push the branch and create a PR using the GitHub CLI.

## Instructions

1. Run these commands in parallel to understand the current state:
   - `git status` — check for uncommitted changes
   - `git log --oneline main..HEAD` — see all commits on this branch
   - `git diff main...HEAD --stat` — see all changed files vs base branch
2. If there are uncommitted changes, ask the user if they want to commit first
3. Push the branch if not already pushed:
   ```bash
   git push -u origin HEAD
   ```
4. Analyze ALL commits on the branch (not just the latest) to draft the PR
5. Create the PR following the project's git conventions for the title and description:
   ```bash
   gh pr create --title "type(scope): description" --body "$(cat <<'EOF'
   ## Summary
   - Bullet points explaining what and why

   ## Changes
   - Notable change 1
   - Notable change 2

   ## Test Plan
   - How to verify the changes

   ## Before Merge
   - [ ] Item to complete before merging
   EOF
   )"
   ```
6. Return the PR URL to the user
