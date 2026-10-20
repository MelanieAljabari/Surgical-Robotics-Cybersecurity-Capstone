# Simulated Surgical Robotics Ransomware Scenario

## Context and objective

The Delta 2 training scenario modeled a hospital orthopedics program using a Stryker Mako-inspired robotic-assisted surgical workflow. The team considered the consequences of a cyberattack interrupting the availability of a simulated patient-specific planning/calibration artifact, `kinematic_cal.bin`, during a pre-procedure handoff.

**Important:** The named file and its claimed properties are **scenario constructs**. This documentation does not assert that real Mako devices use that filename or that the simulated sequence reflects proprietary clinical software.

## Hypothetical attack progression

| Stage | Scenario behavior | Defender concern |
| --- | --- | --- |
| Initial access | Credential phishing or exploitation of remote access | Protect identity and remote entry points |
| Persistence / discovery | Credential misuse, account enumeration, and expanded access | Detect unusual authentication and reconnaissance |
| OT access | Lateral movement toward a simulated clinical planning environment | Segmentation and privileged-access monitoring |
| Monitoring tampering | Proposed poisoning of agent policy files and adjustment of a detection threshold from 2.0σ to 8.0σ | Independent integrity verification and alerting |
| Disruption | Simulated encryption of a critical planning file, leading to workflow interruption | Operational continuity, response, and recovery |

The presentation referenced MITRE ATT&CK tactics such as Initial Access, Persistence, Discovery, Credential Access, Lateral Movement, Defense Evasion, and Impact. Mappings are analytical examples and should be validated against the current ATT&CK knowledge base before using them as production detection rules.

## Impact analysis

The presentation used **illustrative** estimates of $120,000–$300,000 per day in canceled cases and $1–$5 million in potential ransom demands. These figures were part of the training business case, **not measured losses or predictions**.

The primary lessons were that clinical technology availability is tied to patient scheduling, care delivery, safe recovery procedures, and coordinated incident response. Whether an event triggers FDA or HIPAA obligations depends on actual facts, device classification, reporting rules, and a formal assessment; a simulated outage does not automatically establish a reportable event.

## Defensive priorities

1. Protect identity and remote access with phishing-resistant authentication where feasible.
2. Segment enterprise IT and clinical / OT environments.
3. Preserve independently collected telemetry and monitor data gaps.
4. Detect configuration changes against verified baselines.
5. Maintain tested recovery procedures and incident communication plans.
6. Involve clinical leadership before any action that could affect patient care.

## Scope

This was a **classroom/lab scenario**, not a penetration test of a hospital or a Stryker device. No real patient information, proprietary device configuration, or live clinical system was analyzed for this report.
