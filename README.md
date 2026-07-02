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

Latest completed day before the current predictions: Day 2, 06/30, 1/16 finals.

Day 3, 07/03, has 7 active contestants and Claude is marked as banned for the day.
