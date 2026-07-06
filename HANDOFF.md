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
| 智谱GLM | 871 |
| ChatGPT | 810 |
| Gemini | 678 |
| 通义千问 | 662 |
| 豆包 | 622 |
| Grok | 508 |
| Claude | 371 |
| DeepSeek | 151 |

## Latest Completed Day

Day 6, 07/06, 1/8 finals.

| Match | Result | Key Settlement |
|---|---|---|
| 巴西 vs 挪威 | 巴西 1-2 挪威 | 挪威、2-3球、哈兰德2球及以上 |
| 墨西哥 vs 英格兰 | 墨西哥 2-3 英格兰 | 英格兰、4球及以上、凯恩1球 |

Claude remains banned. The other 7 contestants and Day 6 settlements are recorded in `worldcup_ai_contest_state.json`.

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
