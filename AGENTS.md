# Global agent guidelines

Adapted from [Bcdo/claude-setup's global CLAUDE.md](https://github.com/Bcdo/claude-setup/blob/main/global/CLAUDE.md).

Use these defaults alongside project instructions; explicit user requests and more specific project guidance take precedence. Scale planning and verification to the task's complexity and risk.

## Before implementation

- Read the project's `CONTEXT.md` at the start of a session when it exists.
- State consequential assumptions and tradeoffs. When plausible interpretations would change scope or behavior, explain the ambiguity and ask before implementing the affected work; continue independent work where possible.
- Suggest a simpler approach when it meets the need, and explain concerns with an unnecessarily complex approach.

## Keep implementations simple

- Implement only the requested behavior with the smallest clear solution.
- Introduce abstractions, configuration, and extensibility when the current requirements justify them. Keep single-use logic direct.
- Handle realistic failure cases; avoid defensive machinery for states the system cannot reach.
- Review the solution for unnecessary complexity and simplify before delivery.

## Keep changes focused

- Make every changed line traceable to the request. Preserve surrounding code, comments, formatting, and working structure unless the task requires changing them.
- Follow the repository's existing style and conventions.
- Remove imports, variables, and functions made unused by your changes. Mention relevant pre-existing dead code without removing it unless requested.

## Verify the outcome

- Define observable success criteria before making changes. For multi-step work, give a brief plan that pairs each step with its verification.
- For a bug fix, reproduce the failure with a focused regression test when practical, then verify the fix. For validation changes, cover invalid inputs. For refactors, check behavior before and after.
- Run the repository's existing tests and linters relevant to the code changed before reporting completion. Use proportionate checks for trivial or documentation-only edits.
- Continue until the success criteria are verified or a concrete blocker prevents progress. Report what was checked and any checks that could not run.

## Tooling and collaboration

- Default to `bun` for JavaScript and TypeScript (`bun install`, `bun add`, `bun run`) unless the project specifies another package manager.
- Use the `dotnet` CLI for .NET builds, tests, and package management; keep workflows independent of a particular IDE.
- Ask before introducing a new dependency unless the user has already authorized it.
- Favor named TypeScript exports.
- Discover formatting and linting tools from repository configuration and use them; keep the existing toolchain.
- Create commits only when requested. Use Conventional Commit prefixes such as `feat:`, `fix:`, and `chore:` when committing.
