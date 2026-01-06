# mshta

## Legitimate Administrative Use
`mshta.exe` is a Windows utility used to execute Microsoft HTML Application (HTA) files.

In modern enterprise environments, legitimate use is extremely rare.
HTAs were historically used for legacy GUI scripting and internal tools,
but most organizations no longer rely on them.

Any usage should be considered unusual and worth scrutiny.

---

## Common Attacker Abuse Patterns
Attackers abuse `mshta` to execute scripts while bypassing traditional application controls.

Common abuse patterns include:
- Executing remote HTA files hosted on external infrastructure
- Running inline JavaScript or VBScript
- Launching secondary payloads via trusted scripting engines
- Using `mshta` as a loader to avoid dropping binaries

Because `mshta` is signed by Microsoft, it is often trusted by default.

---

## Execution Characteristics
Suspicious `mshta` activity often exhibits:
- Execution from non-interactive contexts
- Remote URLs passed as arguments
- Script-based execution rather than local files
- Unusual parent processes such as Office applications or browsers
- Short-lived execution followed by secondary process creation

In most environments, *any* execution is an anomaly.

---

## Relevant Telemetry
Potential visibility includes:
- Process creation events (e.g., Event ID 4688)
- Command-line arguments showing URLs or inline scripts
- Parent-child process relationships
- Network connections shortly after execution
- User context and originating process

Detection is strongest when process execution is correlated with network activity.

---

## Where Detection Breaks Down
Detection commonly fails when:
- `mshta` is assumed to be deprecated and ignored
- Command-line arguments are not logged
- Execution is treated as a one-off anomaly
- Monitoring focuses on payloads instead of loaders
- Organizations lack a baseline for legacy binaries

Attackers exploit the assumption that “nobody uses this anymore.”

---

## Analyst Reality Check
`mshta` is not noisy.
That’s the problem.

Key analyst questions:
- Why is this binary executing at all?
- What spawned it?
- Did it pull remote content?
- What executed immediately after?

If you see `mshta` in a modern environment,
you are already late in the attack chain.
