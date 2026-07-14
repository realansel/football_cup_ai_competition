# World Cup AI Prediction Contest

This repository keeps the working files for the 2026 World Cup AI prediction contest.

## What Is Tracked

- `世界杯AI竞猜_每日提示词模板-1.md`: daily prompt template for AI contestants.
- `世界杯AI竞猜_预测_0630-1.html`: pre-match prediction image template.
- `世界杯AI竞猜_结算三榜_0630-4.html`: post-match settlement/ranking image template.
- `worldcup_ai_contest_state.json`: latest referee state, balances, rules, and current day picks.
- `outputs/`: user-facing generated pages and handoff notes.

Private exports such as `conversations.json`, `memories.json`, and `users.json` are intentionally ignored.

## Daily Handoff Workflow

1. Pull or copy the latest repository state onto the active host.
2. Read `worldcup_ai_contest_state.json` for current balances and current day status.
3. Use the prompt template to generate contestant prompts for the day.
4. Record contestant picks in `worldcup_ai_contest_state.json`.
5. Generate/update the daily prediction HTML in `outputs/`.
6. After results arrive, calculate settlements, update balances, then generate the settlement HTML.
7. Commit the updated state and outputs.

## Current Contest State

Latest completed day: Day 12, 07/14, semifinal.

Gemini leads with 7336 gold-ball points after the only 4/4 result of Day 12, followed by ChatGPT at 2436 and DeepSeek at 1972. Claude remains banned, while the other 7 contestants are active.

## Git Sync Rule

Before generating any new prompt, prediction report, settlement report, balance ledger, or other project artifact, run `git pull` in `football_cup_ai_competition` and treat the repository files as the source of truth.

After generating or modifying files, copy/sync outputs into the Git repository, commit the changes, and run `git push`. If pushing fails because the network is unavailable, report the local commit hash and tell the user to run `git push` manually.
