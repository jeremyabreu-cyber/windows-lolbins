# PowerShell

## Legitimate Administrative Use
PowerShell is a core Windows automation and management framework used by system administrators for:
- System configuration and maintenance
- User and service management
- Patch validation and troubleshooting
- Ad-hoc one-liners during incident response

In modern enterprise environments, PowerShell usage is normal and expected, especially from IT and security staff.

---

## Common Attacker Abuse Patterns
Attackers abuse PowerShell because it is trusted, powerful, and ubiquitous.

Common abuse patterns include:
- Encoded commands (`-EncodedCommand`) to obscure intent
- In-memory execution to avoid disk artifacts
- Download-and-execute one-liners
- Living-off-the-land execution via parent processes such as `cmd.exe`, `wscript.exe`, or Office applications

PowerShell allows attackers to execute complex logic without introducing new binaries to the system.

---

## Execution Characteristics
Suspicious PowerShell activity often exhibits:
- Long or highly obfuscated command lines
- Use of `-nop`, `-w hidden`, or `-EncodedCommand`
- Execution from non-interactive contexts
- Unusual parent-child process relationships
- Execution by non-admin or service accounts outside expected baselines

These characteristics are contextual indicators, not definitive proof of malicious intent.

---

## Relevant Telemetry
Potential visibility into PowerShell abuse includes:
- Process creation events (e.g., Event ID 4688)
- Command-line logging where enabled
- PowerShell Script Block Logging (Event ID 4104)
- Parent process and user context
- Timing relative to user logons or other suspicious activity

PowerShell abuse is often detectable only when multiple telemetry sources are correlated.

---

## Where Detection Breaks Down
Detection commonly fails when:
- Script Block Logging is disabled or inconsistently deployed
- Encoded commands hide readable intent
- Administrators use PowerShell heavily, increasing baseline noise
- Detections rely solely on keyword matching
- Context such as user role and system purpose is ignored

Attackers benefit from blending into legitimate administrative behavior.

---

## Analyst Reality Check
PowerShell itself is not the threat.
Context is the threat.

Effective analysis focuses on:
- Who executed the command
- From where and why
- What occurred immediately before and after execution
- Whether the behavior aligns with known administrative workflows

Over-alerting on PowerShell leads to alert fatigue.
Under-contextualizing PowerShell leads to missed intrusions.

