# CyberMate AI — Cybersecurity Skills for Claude

**A reusable cybersecurity skill pack for Claude Code, with guided workflows for reconnaissance, web security reviews, vulnerability reports, SOC triage, log analysis, incident response, and defensive malware triage.**

## Quick start

### Option A — Claude Code (slash commands)

This is the supported way to use the slash commands in this repository.

1. Install [Claude Code](https://docs.anthropic.com/en/docs/claude-code/getting-started) and sign in.
2. Download this repository from GitHub using **Code → Download ZIP**.
3. Extract the ZIP file.
4. Open PowerShell or a terminal inside the extracted `cybermate-ai` folder.
5. Install the skills:

   **Windows PowerShell**
   ```powershell
   Set-ExecutionPolicy -Scope Process Bypass
   .\install.ps1
   ```

   **macOS / Linux**
   ```bash
   bash ./install.sh
   ```

6. Open a terminal in the project where you want to use Claude Code and run:
   ```bash
   claude
   ```
7. In the Claude Code prompt, type a slash command and press Enter. For example:
   ```text
   /recon example.com
   ```

   Claude loads the skill instructions and guides the workflow. It may ask you to confirm authorization and scope before proceeding.

### Option B — Claude Desktop (regular chat)

**Important:** This repository is built for Claude Code slash commands. Installing these folders does not add `/recon` commands to the normal Claude Desktop chat box.

You can still use the instructions in Claude Desktop manually:

1. Download the repository ZIP from GitHub and extract it.
2. Open the `.claude/skills/` folder.
3. Open the skill you want, for example `recon/SKILL.md`.
4. Copy its instructions into a Claude Desktop chat, or attach the `SKILL.md` file if file uploads are available.
5. Add your request after the instructions, for example: `Please guide me through an authorized passive reconnaissance plan for my domain example.com`.
6. Follow Claude's questions and provide only systems and evidence you are authorized to use.

Claude Desktop extensions are a separate format from Claude Code skills. This repository is not a `.dxt` desktop extension.

## Available commands

| Command | Purpose |
|---|---|
| `/recon <domain>` | Scope-first, passive reconnaissance planning |
| `/web-audit <URL or local path>` | Review supplied web app code/configuration or evidence |
| `/vuln-report` | Create a report from user-provided findings |
| `/log-analyze <file path>` | Summarize a supplied CSV/JSONL security log |
| `/incident-response` | Guide incident handling and evidence preservation |
| `/soc-investigate` | Triage supplied SOC alerts and events |
| `/malware-triage <file path>` | Defensive static triage; never execute suspicious files |
| `/cyber-learn <topic>` | Learn cybersecurity concepts with safe exercises |

## Example commands

Run these inside an active Claude Code session:

```text
/recon example.com
/web-audit ./my-web-project
/vuln-report
/log-analyze ./examples/sample-security-log.csv
/incident-response
/soc-investigate
/malware-triage ./suspicious-file.bin
/cyber-learn SQL injection
```

The examples are prompts for Claude, not a guarantee that external scans or tests will run. Claude can only use tools available in your environment and allowed by your permissions.

## What's included

- `.claude/skills/` — eight Claude Code skills (`SKILL.md` files)
- `scripts/log_summary.py` — read-only CSV/JSONL summary helper (Python standard library only)
- `scripts/validate_skills.py` — lightweight skill metadata validator
- `install.ps1` — Windows user-level installer
- `install.sh` — macOS/Linux user-level installer
- `docs/` — installation and safety guidance
- `examples/` — harmless sample security log

## Requirements

- Claude Code installed and authenticated for slash-command usage.
- Python 3.9+ only if you want to run the optional log helper or validator.
- No Python packages are required by the included scripts.
- External scanners, browser automation, API keys, and network services are not bundled.

## Validate the repository

From the repository root:

```bash
python scripts/validate_skills.py
python scripts/log_summary.py examples/sample-security-log.csv
```

## Safety and responsible use

Use these workflows only on systems you own or have explicit permission to assess. Confirm scope and permitted methods before testing. The kit defaults to passive research, local code review, and analysis of user-provided evidence. It does not authorize intrusive scanning, exploitation, credential attacks, evasion, persistence, data theft, or destructive actions.

AI-generated findings are not proof. Verify evidence, account for false positives, and follow your organization's security procedures and applicable laws.

## License

MIT — see [LICENSE](LICENSE).
