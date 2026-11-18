# AI Quick Scan

AI & Process Automation Quick Scan — Claude skill for auditing small and mid-size businesses: pre-call research, CEO call prep, maturity and process audit, AI use cases, client report.

## Install (Claude desktop app or claude.ai)

1. Open **Customize** in the left sidebar → **Plugins** tab.
2. Click **Add** → **Add marketplace**, choose the GitHub repository option.
3. Paste `https://github.com/kadesnikov/ai-quick-scan` (or `kadesnikov/ai-quick-scan`).
4. Open the new marketplace and click **Add** on the **ai-quick-scan** plugin.

The plugin is saved to your account and also shows up in Cowork and Claude Code.

## Install (Claude Code)

```
/plugin marketplace add kadesnikov/ai-quick-scan
/plugin install ai-quick-scan@ai-quick-scan
```

Update to the latest version:

```
/plugin marketplace update ai-quick-scan
```

## Use

Give Claude anything about a company — a photo of a sign, a website, notes, a call transcript — and ask for a quick scan. The skill detects the stage (research → call prep → audit → use cases → report).

## Update the skill

Edit `plugins/ai-quick-scan/skills/ai-quick-scan/SKILL.md`, bump `version` in `plugins/ai-quick-scan/.claude-plugin/plugin.json`, open a pull request. New industry modules and cases go into the "Industry modules" section.
