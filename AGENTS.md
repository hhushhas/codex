# Hasan Shoaib's Protocol

- Projects Dir: `/Users/macmini/Desktop/Code/`.
- Browser: Helium.
- Prefer end-to-end verify; if blocked, say what's missing.
- Before adding a new dependency, check maintenance, recency, adoption, and obvious risk flags.
- Bugs: add regression test when it fits.
- Multi-agent repos: assume dirty worktrees; ignore unrelated changes unless they create real conflict or risk.

## Durable Sessions

- When a task spans multiple turns or may need resume, consider logging timestamped progress/clarifications in `scratchpad/<work>-session-log-YYYY-MM-DD.md`.
- Put reusable guidance in project `AGENTS.md`; treat "Make a note" / "I like this behaviour" as a strong signal to record it.

## Git Hygiene

- Push only on "ship it", usually to **master/main**; no branches/worktrees unless told.
- Stage only intended paths with `git add -p`; never `git add .`.
- No stash/reset/revert of others' work; no repo-wide formatting/renames/refactors unless asked.

## Research

- Search early, quote exact errors, prefer 2026–2024 sources when recency matters; use Context7 for official docs/API setup and web search for news, issues, forums, pricing, incidents, comparisons, and fallback research.

## Delegation

- Delegate separable research, code reading, logs, CI, testing, refactors, codegen, and bounded implementation in parallel when useful; track dependencies, avoid conflicts, and keep critical-path decisions local.
- Model split: gpt-5.5 high for review/suggestions/complex work; gpt-5.5 low by default; gpt 5.4 mini high only for read-only or computer-use support, never diagnosis/fix/review/deploy decisions.
- Review subagent output and verify important claims.

# Code Standards

- Write readable, modular, avoid noisy defensive checks.
- Preserve existing behavior unless instructed otherwise.
- Use consistent canonical names, early returns, inferred types, typed boundaries, type-safe state shapes, and focused functions/modules.
- Keep data flow explicit; avoid hidden coupling, surprising side effects, and speculative abstractions.
- Split files only when it improves structure.
- Preserve accessibility, security, and privacy; improve them when touching relevant code.

# Tools

- Package manager: `pnpm`; `npm` only for legacy projects.
- OrbStack: orbstack instead of docker.
- Skillbox: on-demand skill loading; use it when Hasan asks for a skill or when focused guidance would improve execution, especially for substantial migrations or unfamiliar work.
- AWS profiles: `q9labs`, `th`, `yahya` have IAM Admin. For IAM inline policy attachment, ask once up front and list policies that are needed or might be needed; after confirmation, attach those policies during the thread/execution without asking again.
- GitHub CLI: default `hhushhas`; alternate `msbilal01`; switch back after use.

# Handoff

Default: run the full gate (lint → typecheck → tests → CHANGELOG), stage scope only, commit conventional, then stop and report results. Push only on "ship it".

Ship it: push, watch CI, fix/re-push until required jobs are green, verify deploy/live revision when applicable, then report green run + live proof.
