# Detection Gaps in Living-off-the-Land Techniques

Living-off-the-land attacks succeed not because defenders lack tools,
but because attackers exploit trust, context, and operational assumptions.

This document highlights common detection gaps that allow LOLBin abuse
to persist undetected in Windows environments.

---

## Trusted Binary Bias
Signed Windows binaries are often implicitly trusted.
Alerts focus on *what* executed rather than *why* it executed.

Attackers rely on defenders assuming:
- “It’s a Microsoft binary”
- “Admins use this all the time”
- “There’s no malware file”

---

## Context Loss
Many detections operate on single events.

Without context, defenders miss:
- Parent-child process relationships
- User role and expected behavior
- Timing relative to other suspicious actions

LOLBins are rarely malicious in isolation.
They become malicious in sequence.

---

## Baseline Blindness
Organizations often lack:
- Clear baselines for administrative behavior
- Documentation of expected tooling usage
- Ownership of legacy binaries

Attackers thrive where “normal” is undefined.

---

## Keyword-Based Detection
Simple keyword matching fails when:
- Commands are encoded or obfuscated
- Execution intent is hidden
- Legitimate admin activity creates noise

Attackers do not need to evade detection logic.
They only need to blend in.

---

## Alert Fatigue
Over-alerting on LOLBins causes:
- Analysts to ignore future alerts
- Legitimate threats to be dismissed as noise
- Persistence mechanisms to be overlooked

Attackers benefit from defenders being tired.

---

## Analyst Takeaway
Living-off-the-land detection is not a tooling problem.
It is a reasoning problem.

Effective defense requires:
- Behavioral understanding
- Contextual correlation
- Skepticism of assumptions
