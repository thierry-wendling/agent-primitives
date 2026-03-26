---
name: rule-creation
description: Best practices for creating effective, maintainable, and properly scoped Cursor rules
---
# Rule Creation Guidelines

When creating new Cursor rules in `.cursor/rules`, follow these best practices to ensure rules are effective, maintainable, and properly scoped.

## Rule Structure

### File Format
- Use **MDC format** (`.mdc` extension) with frontmatter metadata
- Include `description` field for "Apply Intelligently" rules
- Set `alwaysApply: true` only when rule should apply to every chat session
- Use `globs` pattern for file-specific rules

### Frontmatter Example
```yaml
---
description: Clear description of when this rule applies
alwaysApply: false
globs: ["**/*.py", "**/*.ts"]  # Optional, for file-specific rules
---
```

## Best Practices

### 1. Keep Rules Focused and Concise
- **Keep rules under 500 lines** - Split large rules into multiple, composable rules
- Each rule should address a single concern or domain
- Use clear, actionable language - avoid vague guidance
- Write rules like clear internal documentation

### 2. Provide Concrete Examples
- Include specific code examples or patterns
- Reference existing files using `@filename.ext` syntax
- Show both good and bad examples when helpful
- Link to relevant documentation or standards

### 3. Scope Rules Appropriately
- **Always Apply**: Only for rules that should be in every chat context (e.g., coding standards)
- **Apply Intelligently**: Use when rule is relevant based on description and context
- **Apply to Specific Files**: Use globs pattern for file-type specific rules
- **Apply Manually**: For specialized rules that are @-mentioned explicitly

### 4. Make Rules Actionable
- Use imperative language ("Use X", "Avoid Y", "Always Z")
- Provide specific, testable guidance
- Include checklists or step-by-step instructions when appropriate
- Avoid ambiguous statements that could be interpreted multiple ways

### 5. Organize with Nested Rules
- Place rules in `.cursor/rules` subdirectories for domain-specific guidance
- Nested rules automatically attach when files in their directory are referenced
- Use this for backend/frontend/service-specific rules

## Rule Types and When to Use Them

### Always Apply Rules
Use for:
- Project-wide coding standards
- Architecture decisions that apply everywhere
- Critical conventions that must always be followed

Example: `alwaysApply: true` for coding standards, branch naming conventions

### Apply Intelligently Rules
Use for:
- Domain-specific knowledge (e.g., ML model patterns, API design)
- Workflow automation (e.g., "When asked to analyze the app...")
- Template generation (e.g., "When creating Express services...")

Example: `alwaysApply: false` with descriptive `description` field

### File-Specific Rules
Use for:
- Language-specific conventions (e.g., Python, TypeScript)
- File-type patterns (e.g., component templates, service templates)
- Directory-specific standards

Example: `globs: ["**/*.py"]` for Python-specific rules

## Content Guidelines

### Structure
1. **Clear title** describing the rule's purpose
2. **Introduction** explaining when and why to use this rule
3. **Main content** organized with headers and bullet points
4. **Examples** showing concrete implementations
5. **References** to related files or documentation

### Writing Style
- Be specific: "Use snake_case for function names" not "Use good naming"
- Be actionable: "Always include error handling" not "Consider error handling"
- Be consistent: Use the same terminology across related rules
- Be complete: Cover edge cases and exceptions

### Code Examples in Rules

**Good Rule Example:**
```markdown
When creating FastAPI endpoints:
- Use async/await for all I/O operations
- Include proper error handling with HTTPException
- Document request/response models with Pydantic
- Follow RESTful conventions for route naming
```

**Bad Rule Example:**
```markdown
Write good API code.
Make sure it's fast and handles errors.
```

## Rule Naming Conventions

- Use kebab-case: `rule-creation.mdc`, `api-design.mdc`
- Be descriptive: `branch-naming.mdc` not `naming.mdc`
- Group related rules with prefixes: `api-*.mdc`, `ml-*.mdc`
- Keep names concise but clear

## Testing Rules

Before finalizing a rule:
1. Verify it applies when expected (check rule type settings)
2. Test with actual chat scenarios
3. Ensure examples are accurate and up-to-date
4. Check that file references (`@filename`) work correctly
5. Confirm rule doesn't conflict with existing rules

## Common Pitfalls to Avoid

- **Too broad**: Rules that try to cover everything become ineffective
- **Too vague**: "Write good code" provides no actionable guidance
- **Outdated examples**: Keep code examples current with codebase
- **Conflicting guidance**: Ensure rules don't contradict each other
- **Missing context**: Rules should explain "why" not just "what"

## Reusing Rules

- Reference existing rules when creating new ones
- Extract common patterns into shared rules
- Use `@filename` to include relevant code examples
- Link to related rules in rule descriptions

## Maintenance

- Review rules periodically for accuracy
- Update examples when codebase patterns change
- Remove or consolidate redundant rules
- Keep rules synchronized with project documentation
