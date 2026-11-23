# CTF and Red Team Writeups

**Red team and CTF engagements written up as professional assessment reports: what was wrong, why it mattered, how
to fix it, how a defender would spot it, and what didn't work along the way.**

> [!NOTE]
> All work here took place in sanctioned CTF and lab environments. A writeup is published only where the platform or
> organiser allows it, and identifying details (addresses, host and domain names, flag values, credentials) are
> removed. Nothing here describes real-world systems.

**Contents:** [Writeups](#writeups) · [How each report is structured](#how-each-report-is-structured) ·
[Principles](#principles) · [Building your own portfolio](#building-your-own-portfolio) · [Licence](#licence)

## Writeups

<!-- One row per writeup, newest first. Result = the outcome in one line, with a number where there is one. -->

| Engagement | Format | Environment | Result | Themes | Year |
|---|---|---|---|---|---|
| [Assumed-breach AD assessment](red-team/ad-domain-compromise/) | Adversarial simulation, assumed breach | 5 hosts, 3 subnets, Active Directory | 12/12 objectives, all 5 hosts, Domain Admin at 2 h 37 m | Identity, service accounts, segmentation | 2026 |

## How each report is structured

Every writeup follows the same [template](TEMPLATE.md), modelled on professional assessment reports rather than
walkthroughs:

1. **Summary table:** format, scope, starting position, result, time taken.
2. **Executive summary:** one page a non-technical reader can act on: outcome, root causes, priority fixes.
3. **Scope and rules:** what was in scope, the starting position, constraints, and how the work was assessed.
4. **Approach:** the decisions that shaped the engagement, not a list of tools.
5. **Attack path:** one diagram showing how the findings chained together.
6. **Findings:** each with severity and reasoning, MITRE ATT&CK mapping, weakness, impact, a quick fix and a
   root-cause fix, and detection notes.
7. **Dead ends and time lost:** what failed, how long it took, and what it taught.
8. **Retrospective:** what I would do differently next time.

Severity, evidence and writing standards are defined once in [METHODOLOGY.md](METHODOLOGY.md) and applied to every
report.

## Principles

- **Methodology over tooling.** Tools change every year; the reasoning behind each decision doesn't. Reports explain
  why a step was taken, not just which command ran.
- **Root causes over symptoms.** One misconfiguration that enabled three steps is one finding, not three.
- **Every finding has a fix and a detection.** An attack path is only useful to an organisation if it can be closed
  and watched for.
- **Failures are reported.** Dead ends and time lost are part of the record. Recognising a dead end quickly is a skill
  in its own right.
- **Severity is reasoned, not asserted.** Every rating says why, against a scale defined in advance.

## Building your own portfolio

If you're starting out and want to build something similar:

1. Read [METHODOLOGY.md](METHODOLOGY.md) for the working and reporting standard.
2. Copy [TEMPLATE.md](TEMPLATE.md) into a new folder for each engagement and work through the publishing checklist at
   the top before you push.
3. Check the platform's rules first. Most platforms allow writeups only for retired content, for example
   [Hack The Box](https://help.hackthebox.com/en/articles/5188925-streaming-writeups-walkthrough-guidelines) and
   [TryHackMe](https://tryhackme.com/legal/acceptable-use-policy). For internal or employer events, ask the
   organisers: ranges are often reused, and a public solution spoils them for the next cohort.
4. If you want freedom to publish, build your own lab. [GOAD](https://github.com/Orange-Cyberdefense/GOAD) is an
   open-source Active Directory lab anyone can rebuild.

Reading that shaped this repo:

- [Public penetration testing reports](https://github.com/juliocesarfort/public-pentesting-reports): real reports from
  security consultancies, the best way to learn professional tone.
- [How to write great pentesting reports](https://www.blackhillsinfosec.com/how-to-not-suck-at-reporting-or-how-to-write-great-pentesting-reports/)
  and [report writing do's and don'ts](https://www.blackhillsinfosec.com/dos-and-donts-of-pentest-report-writing/)
  from Black Hills Information Security.
- [Security assessment report cheat sheet](https://zeltser.com/security-assessment-report-cheat-sheet) and
  [executive summary tips](https://zeltser.com/executive-summary-for-security-assessment-report-tips) by Lenny Zeltser.
- [The DFIR Report template](https://github.com/The-DFIR-Report/DFIR-Artifacts/blob/main/REPORT%20TEMPLATE.md): the
  defender's view of an intrusion, useful for writing detection notes.
- [MITRE ATT&CK](https://attack.mitre.org/) and the [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator)
  for technique mapping.

## Licence

Everything in this repository, including any code or scripts, is licensed under
[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). No commercial use of any kind is permitted. See
[LICENSE.md](LICENSE.md).
