# schtasks

## Legitimate Administrative Use
The `schtasks` utility is used by administrators to create, modify, and manage scheduled tasks for:
- System maintenance
- Patch execution
- Log rotation and cleanup
- Backup jobs
- Startup and recurring automation

Scheduled tasks are common on both servers and workstations, especially in enterprise environments.

---

## Common Attacker Abuse Patterns
Attackers abuse `schtasks` primarily for persistence and delayed execution.

Common techniques include:
- Creating tasks that execute at system startup or user logon
- Using task names that resemble legitimate Windows or vendor tasks
- Scheduling one-time execution shortly after compromise
- Executing scripts or LOLBins rather than dropping new binaries

Persistence via scheduled tasks allows attackers to survive reboots with minimal visibility.

---

## Execution Characteristics
Suspicious scheduled task activity may include:
- Task creation shortly after initial access
- Task names mimicking system or security software
- Execution of scripts, command interpreters, or remote resources
- Tasks created by unexpected users or service accounts
- Tasks created outside of normal maintenance windows

The timing and context of task creation is often more important than the command itself.

---

## Relevant Telemetry
Potential visibility includes:
- Scheduled task creation events (e.g., Event ID 4698)
- Task modification and deletion events
- Process creation logs associated with task execution
- User and account context for task creation
- Task execution frequency and triggers

Task abuse is often only visible when creation and execution events are correlated.

---

## Where Detection Breaks Down
Detection commonly fails when:
- Task creation is considered routine background noise
- Task names appear legitimate at a glance
- Administrators frequently create tasks manually
- Monitoring focuses on execution rather than creation
- Persistence mechanisms are not reviewed during triage

Attackers rely on defenders ignoring scheduled task metadata.

---

## Analyst Reality Check
Scheduled tasks are persistence mechanisms, not alerts.

Key analyst questions include:
- Who created the task and why?
- When was it created relative to other suspicious activity?
- What executes, and under what account?
- Does the task align with documented administrative workflows?

Persistence often looks boring.
That is why it works.
