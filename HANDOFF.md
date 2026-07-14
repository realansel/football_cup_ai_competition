# Handoff Notes

## Project Purpose

This folder is now a portable Git project for running the World Cup AI prediction contest across different hosts.

The key source of truth is:

```text
worldcup_ai_contest_state.json
```

It stores:

- latest balances
- contest rules
- model identities
- current day match list
- current day picks
- Claude ban status since Day 3

## Current Scores

| AI | Balance |
|---|---:|
| Gemini | 7336 |
| ChatGPT | 2436 |
| DeepSeek | 1972 |
| 豆包 | 1576 |
| 通义千问 | 1404 |
| 智谱GLM | 1379 |
| Grok | 799 |
| Claude | 371 |

## Latest Completed Day

Day 12, 07/14, semifinal.

| Match | Result | Key Settlement |
|---|---|---|
| 法国 vs 西班牙 | 西班牙胜；2-3球；西班牙率先破门；3-5张黄牌 | Gemini 4/4，四项奖励5571，瓜分奖励1018，兑奖总额6589 |

Claude remains banned. The other 7 contestants and Day 12 settlement are recorded in `worldcup_ai_contest_state.json`.

## Moving To Another Host

Preferred:

```powershell
git clone <repo-url-or-copied-folder>
```

For an offline handoff:

```powershell
git bundle create worldcup-ai-contest.bundle --all
```

Then move the `.bundle` file to the other host and run:

```powershell
git clone worldcup-ai-contest.bundle worldcup-ai-contest
```

After working on another host, commit changes and send the repository or a new bundle back.

## Git Sync Rule

Before generating any new prompt, prediction report, settlement report, balance ledger, or other project artifact, run `git pull` in `football_cup_ai_competition` and treat the repository files as the source of truth.

After generating or modifying files, copy/sync outputs into the Git repository, commit the changes, and run `git push`. If pushing fails because the network is unavailable, report the local commit hash and tell the user to run `git push` manually.
