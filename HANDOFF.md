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
- Claude ban status for Day 3

## Current Scores

| AI | Balance |
|---|---:|
| 豆包 | 609 |
| Claude | 371 |
| 通义千问 | 359 |
| DeepSeek | 348 |
| ChatGPT | 344 |
| Gemini | 344 |
| Grok | 344 |
| 智谱GLM | 344 |

## Day 3 Prediction Inputs

| Match | Odds | Time |
|---|---|---:|
| 西班牙 vs 奥地利 | 西班牙 95% / 奥地利 5% | 03:00 |
| 葡萄牙 vs 克罗地亚 | 葡萄牙 72% / 克罗地亚 28% | 07:00 |
| 瑞士 vs 阿尔及利亚 | 瑞士 85% / 阿尔及利亚 15% | 11:00 |

Claude is banned for Day 3. The other 7 contestants are recorded in `worldcup_ai_contest_state.json`.

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
