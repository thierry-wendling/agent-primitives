# Commit staged changes

Review changes and create a conventional commit.

## Instructions

1. Run `git status` to see all modified, staged, and untracked files
2. Run `git diff` to review the actual changes (both staged and unstaged)
3. Analyze the changes to determine the commit type and scope
4. Stage relevant files (use `git add -A` unless only specific files should be committed)
5. Write a commit message following the project's git conventions
6. Commit using a HEREDOC for proper formatting:

```bash
git commit -m "$(cat <<'EOF'
type(scope): subject line

Optional body explaining why.

Optional footer.
EOF
)"
```

## Important

- Summarize the **why**, not the what
- Do not commit files that contain secrets (`.env`, credentials, etc.)
- If changes span multiple concerns, split them into separate atomic commits automatically
