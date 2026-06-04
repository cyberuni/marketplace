# AGENTS.md

This file provides guidance to AI coding assistants when working with code in this repository.

## Repository Purpose

This repo is the **Cyberuni marketplace catalog** for Claude Code plugins. The single source of truth is `.claude-plugin/marketplace.json`, which lists plugin bundles that users install via the Claude Code plugin system.

## Adding or Updating Plugins

Each entry in `.claude-plugin/marketplace.json` must include:

- `name` — unique slug for the plugin bundle
- `source.source` — always `"url"` for public repos
- `source.url` — HTTPS git URL (not SSH — SSH requires auth and breaks CI)
- `description` — one-line human summary
- `skills` — array of relative skill paths within the source repo (e.g. `"./skills/find-awesome-skill"`)
- `category` — one of: `research`, `skills`, `setup`, `productivity`, `plugin-authoring`
- `homepage` and `repository` — both set to the GitHub repo URL
- `license` — SPDX identifier (e.g. `"MIT"`)

`strict: false` allows the plugin to install even when some skills are unavailable.

## Validation

After editing `marketplace.json`, verify JSON is valid:

```bash
npx --yes cyber-skills@0.7.0 audit validate
```

## Commit Discipline

**Auto-commit rule:** When a unit of work is complete and verified, commit it immediately — do not wait for the user to ask. Batching multiple units into one commit, or finishing all work before committing, are both violations of this rule.

**Unit of work:** one coherent, independently revertable change — one domain's refactor, one feature, one bugfix, one test suite expansion for one concern, one config change. Never two unrelated concerns in the same commit. A TDD red-green-refactor cycle alone is not a commit boundary; commit when the full intended change is complete and tests pass. If the working tree has unrelated changes, leave them unstaged — commit the current unit first, then continue.

- Conventional Commits: `feat:`, `fix:`, `refactor:`, `test:`, `docs:`, `chore:`
- One concern per commit; never batch unrelated changes
- Stage only files for this unit: `git add <files>`, then verify with `git diff --cached`
- Never use `git add .`, `git add -A`, or `git add -p` (interactive commands agents cannot run)
- Never commit with red tests; run validation commands first

### References

- **`commit-work` skill** — staging, splitting, and message writing when committing

