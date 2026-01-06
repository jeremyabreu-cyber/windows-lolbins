# rundll32

## Legitimate Administrative Use
`rundll32.exe` is a Windows utility used to execute exported functions from DLL files.

Legitimate use cases include:
- Invoking specific DLL functions required by Windows components
- Legacy control panel and system functionality
- Vendor software that still relies on DLL-based execution

While legitimate, direct interaction with `rundll32` by users or administrators is uncommon.

---

## Common Attacker Abuse Patterns
Attackers abuse `rundll32` to execute code without introducing new executables.

Common abuse patterns include:
- Executing malicious or weaponized DLLs
- Loading DLLs from user-writable directories
- Using obscure or undocumented DLL export functions
- Leveraging `rundll32` to bypass application allowlisting

Because the binary is trusted, execution often blends into normal system activity.

---

## Execution Characteristics
Suspicious `rundll32` activity may include:
- Unusual or malformed command-line arguments
- DLLs executed from non-standard paths (e.g., user profiles, temp directories)
- Execution shortly after document opening or script execution
- Parent processes such as Office applications, browsers, or scripting engines
- Lack of accompanying legitimate software activity

The DLL path and export function are often more important than the binary itself.

---

## Relevant Telemetry
Potential visibility includes:
- Process creation events (e.g., Event ID 4688)
- Full command-line logging
- Parent-child process relationships
- DLL file path and creation timestamps
- Subsequent process or network activity

Detection improves when DLL execution context is analyzed rather than binary name alone.

---

## Where Detection Breaks Down
Detection commonly fails when:
- `rundll32` is assumed to be system noise
- Command-line arguments are truncated or ignored
- Analysts focus on the binary name instead of the DLL path
- DLL execution is not correlated with file creation events
- Legitimate system usage masks malicious activity

Attackers rely on defenders trusting signed binaries too much.

---

## Analyst Reality Check
`rundll32` is just a launcher.
The real question is what it launched.

Key analyst questions:
- What DLL was executed and where did it come from?
- Is the DLL path consistent with legitimate software?
- What process spawned `rundll32`?
- What happened immediately after execution?

Trust the context, not the binary.
