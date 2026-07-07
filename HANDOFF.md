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
| Gemini | 1375 |
| ChatGPT | 1217 |
| 智谱GLM | 1062 |
| 通义千问 | 744 |
| Grok | 642 |
| 豆包 | 592 |
| Claude | 371 |
| DeepSeek | 336 |

## Latest Completed Day

Day 7, 07/07, 1/8 finals.

| Match | Result | Key Settlement |
|---|---|---|
| 葡萄牙 vs 西班牙 | 葡萄牙 0-1 西班牙 | 西班牙、C罗0球 |
| 美国 vs 比利时 | 美国 1-4 比利时 | 比利时、没有点球大战 |

Claude remains banned. The other 7 contestants and Day 7 settlements are recorded in `worldcup_ai_contest_state.json`.

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
