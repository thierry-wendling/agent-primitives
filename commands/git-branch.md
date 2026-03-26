# Create a new git branch

Create and checkout a new branch for the current task.

## Instructions

1. Ask the user what the branch is for if not clear from context
2. Determine the appropriate branch type based on the work being done
3. Generate a branch name following the project's git conventions
4. Create and checkout the branch from the current base branch (usually `main`)

## Example

```
git checkout main
git pull origin main
git checkout -b feat/add-user-auth
```
