# wmic

## Legitimate Administrative Use
`wmic.exe` (Windows Management Instrumentation Command-line) is used for querying and managing system information via WMI.

Legitimate uses historically included:
- Hardware and software inventory
- Remote system queries
- Process and service inspection
- Administrative scripting in older environments

In modern Windows environments, `wmic` is largely deprecated and replaced by PowerShell and modern management tooling.

---

## Common Attacker Abuse Patterns
Attackers abuse `wmic` primarily for execution and lateral movement, especially in legacy-heavy environments.

Common abuse patterns include:
- Remote command execution via WMI
- Process creation on remote hosts without interactive login
- Reconnaissance of system, user, and process information
- Blending malicious activity into administrative-style queries

Because WMI is designed for remote management, attackers can operate quietly without traditional authentication artifacts.

---

## Execution Characteristics
Suspicious `wmic` activity often includes:
- Remote execution targeting multiple hosts
- Commands executed by non-interactive or service accounts
- Use shortly after credential compromise
- Execution from unexpected systems (e.g., workstations initiating remote management)
- Lack of corresponding user logon activity

`wmic` activity is often subtle and easy to overlook.

---

## Relevant Telemetry
Potential visibility includes:
- Process creation events (e.g., Event ID 4688)
- WMI operational logs where enabled
- Remote process creation artifacts
- Account usage patterns inconsistent with interactive behavior
- Network connections associated with remote management activity

Detection often requires correlating process execution with authentication and network context.

---

## Where Detection Breaks Down
Detection commonly fails when:
- WMI activity is assumed to be legacy noise
- Remote execution is not differentiated from local use
- Authentication context is not reviewed
- Organizations lack visibility into WMI operational logs
- Analysts expect malware rather than management-style abuse

Attackers benefit from defenders underestimating legacy tooling.

---

## Analyst Reality Check
`wmic` is not flashy.
That is why it works.

Key analyst questions:
- Why is this system performing remote management actions?
- Does the account normally administer other hosts?
- Is there a corresponding change request or maintenance activity?
- What happened before and after this execution?

Legacy tools are still tools.
Attackers know this.

