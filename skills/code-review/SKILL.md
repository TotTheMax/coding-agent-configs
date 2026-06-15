# Skill: Code Review

Use this skill when the user asks to review code, check code quality, or wants feedback on a PR or code changes.

## When to Use

- User asks "review this code" or "check my changes"
- User mentions PR review or code quality concerns
- User shares code snippets asking for improvement suggestions

## Instructions

1. Read the code changes or files the user wants reviewed
2. Check for:
   - Code style consistency with project conventions
   - Potential bugs or edge cases
   - Security concerns (hardcoded secrets, SQL injection, etc.)
   - Performance issues (unnecessary loops, missing caching)
   - Missing error handling
   - Test coverage gaps
3. Organize feedback by severity:
   - **Critical**: Must fix (bugs, security, data loss)
   - **Important**: Should fix (performance, missing error handling)
   - **Suggestion**: Nice to have (style, naming, minor refactoring)
4. Provide specific line references and suggested fixes
5. Summarize overall assessment at the end
