# Methodology

The working and reporting standard behind every writeup in this repo. It covers how I work during an engagement and
how I turn the record into a report. It is deliberately tool-agnostic.

**Contents:** [Before the engagement](#1-before-the-engagement) · [During the engagement](#2-during-the-engagement) ·
[Writing the report](#3-writing-the-report) · [Severity scale](#severity-scale) ·
[Before publishing](#4-before-publishing)

---

## 1. Before the engagement

- **Know the scope and the rules.** What is in scope, what is off-limits, what counts as success, and how the work is
  assessed (flags alone, or methodology and operational security too).
- **Know the starting position.** Assumed breach (credentials or access provided) or no access at all. This decides
  whether initial access is a finding.
- **Know whether you may publish.** Check the platform's writeup rules, or ask the organiser, before you start taking
  notes for a public report.

## 2. During the engagement

### The working loop

Every step follows the same loop: **enumerate → form a hypothesis → test it → record the result**, whether it worked
or not. The record is what the report is built from; if it isn't written down at the time, it didn't happen.

### Decision rules

1. **Treat access as a graph, not a list.** Every new credential or foothold is tested against everything reachable in
   scope. The most valuable paths are rarely visible from a single host.
2. **Identify the highest-value target early and work backwards.** Once you know what full compromise looks like, judge
   every move by whether it gets you closer.
3. **Time-box, then ask why.** When an approach stalls for about 15 minutes, stop and work out why it is failing before
   trying another tool. A reason ("this can't work from this kind of session") beats a fifth attempt.
4. **Use the access you already hold.** Before hunting for a new weakness, check what your existing privileges already
   allow.
5. **Prefer quiet and reversible actions.** Note anything that changes the environment (accounts, passwords, services,
   files) so it can be reported and reverted. In a real engagement, disruptive changes need approval first.

### Note-taking standard

- An operation log with a time offset per entry, covering every action, including failures.
- Evidence captured at the time it happens: screenshots or output showing the access gained.
- Every change made to the environment, and whether it was reverted.

## 3. Writing the report

### Write for three readers

| Reader | Needs | Section |
|---|---|---|
| Decision-maker | What happened, how bad it is, what to fix first | Executive summary |
| Engineer fixing it | What exactly is wrong, where, and how to fix it | Findings |
| Defender | What it looked like and how to spot it next time | Detection notes |

### Findings are root causes

A finding is a weakness, not a step in the attack. If one misconfiguration enabled three steps, it is one finding that
references all three. If several low-severity weaknesses only matter together, report the chain and rate the chain.

Behaviour that is by design but became dangerous after another failure (for example, what any administrator can
legitimately do) is recorded as a consequence of the finding that granted that access, not as a separate finding.

### Finding structure

Each finding has:

- **ID, title and severity**, with one line on why it got that rating.
- **Status:** *confirmed* (exploited during the engagement) or *potential* (identified but not exploited, with the
  reason).
- **MITRE ATT&CK** technique IDs.
- **Affected:** hosts, accounts or services.
- **Weakness:** what is wrong, stated as a configuration or design fact.
- **Impact:** what it allowed, in business terms as well as technical ones.
- **Remediation:** a quick stopgap and a root-cause fix.
- **Detection:** the signal a defender could have alerted on.

### Severity scale

Severity reflects impact and exploitability **in this environment**. CVSS v4.0 can be an input, but context decides
the rating.

| Rating | Meaning |
|---|---|
| **Critical** | Directly enables domain-wide or organisation-wide compromise |
| **High** | Enables privilege escalation, credential exposure or lateral movement to sensitive systems |
| **Medium** | Widens the attack surface or helps an attack, but needs another weakness to matter |
| **Low** | Limited impact, or defence-in-depth gaps |
| **Info** | Observations and strengths worth noting, no direct risk |

### MITRE ATT&CK mapping

Map each finding to the technique it enables. Use the most specific sub-technique that fits, and don't stretch a
mapping to fill a table. An exported [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator) layer can be
added to the report folder as a visual summary.

### Remediation

Order fixes by risk reduction, not by the order they were found. For each one, give a quick stopgap (what to do this
week) and a root-cause fix (what stops the class of problem coming back). After a compromise this deep, say what must
be rotated or rebuilt.

### Detection notes

For each finding, name the observable signal (an event type, a process relationship, a network pattern) a defender
could alert on, and say where it would be logged. Where a rule is included, credit its source and keep its licence
(for example, rules from [SigmaHQ](https://github.com/SigmaHQ/sigma) carry DRL 1.1).

### Writing style

- Past tense, plain language, active voice.
- Findings describe configurations and decisions, never people. No boasting, no mocking the target.
- No unsupported statistics. If you claim something is common, cite a source or say "in my experience".
- No raw tool output pasted as prose. Summarise it, and keep evidence short and annotated.
- Every severity has a reason; every recommendation is specific enough to act on.

## 4. Before publishing

- [ ] The platform or organiser allows public writeups of this content (retired, or permission given in writing).
- [ ] Addresses, host and domain names, usernames, flag values, passwords and hashes are removed or replaced.
- [ ] Screenshots are cropped and redacted, with nothing identifying left in window titles, prompts or browser tabs.
- [ ] Platform and range names are removed if the organiser asked for that.
- [ ] Internal notes, prompts and to-do comments are removed from the source file.
- [ ] Every finding has a severity reason, a fix and a detection note.
- [ ] The executive summary makes sense on its own.
