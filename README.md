# Trending GitHub AI Repos

A Claude Code Routine that publishes a daily markdown brief of the hottest AI repositories on GitHub.

## What this does

Every day at 08:00 AM, Claude Code runs [`ROUTINE.md`](./ROUTINE.md). It hits the GitHub search API, ranks the trending repos, writes an "editor's take", and commits the result to [`outputs/`](./outputs/).

## Setup

1. Fork or clone this repo.
2. Connect it as the destination repo when you create the routine at [cloud.ai/code/routines](https://cloud.ai/code/routines).
3. Paste the contents of [`ROUTINE.md`](./ROUTINE.md) as the prompt.
4. Trigger: daily cron at `0 8 * * *`.
5. Save. First run happens at the next 08:00.

## How to read the output

- `outputs/trending-YYYY-MM-DD.md` — the daily brief
- Each file is append-only (the routine never modifies past runs)
- Git history = your research archive

## How to tune

- Widen / narrow topic filter → edit [`inputs/sources.md`](./inputs/sources.md)
- Change thresholds / counts → edit [`inputs/config.yml`](./inputs/config.yml)
- Change tone or format → edit [`.claude/CLAUDE.md`](./.claude/CLAUDE.md)

## Kill date

Review on **2026-05-15** (30 days post-launch): kill, tune, or promote to a real backend.
