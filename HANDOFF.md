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
| ChatGPT | 1153 |
| Gemini | 890 |
| 智谱GLM | 883 |
| 通义千问 | 872 |
| Grok | 604 |
| DeepSeek | 590 |
| 豆包 | 374 |
| Claude | 371 |

## Latest Completed Day

Day 8, 07/08, 1/8 finals.

| Match | Result | Key Settlement |
|---|---|---|
| 阿根廷 vs 埃及 | 阿根廷胜；4球及以上 | 阿根廷、4球及以上、梅西上半场否 |
| 瑞士 vs 哥伦比亚 | 瑞士胜；常规0球 | 瑞士、0-1球、无进球 |

Claude remains banned. The other 7 contestants and Day 8 settlements are recorded in `worldcup_ai_contest_state.json`.

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
