
# Surgical Robotics Cybersecurity Capstone

### ARGUS Industrial Threat Detection | Surgical Robotics (Stryker Mako scenario)

**Delta 2 Team Capstone | WMCAT / NextCISO Academy | 2026**  
**Portfolio focus:** Healthcare cybersecurity · Operational technology (OT) · Threat detection · Incident response · Threat intelligence · Governance

> **Training simulation:** This capstone modeled a ransomware incident involving a surgical robotics workflow. The `kinematic_cal.bin` file, attack path, financial estimates, and detection signatures are elements of the training scenario, **not verified descriptions of a deployed Stryker Mako system or an actual patient incident**. Sensor demonstrations used laboratory proxies rather than a live surgical robot.

## Project overview

The Delta 2 capstone explored a difficult healthcare security problem: **How can a hospital detect a disruptive attack when the affected clinical technology or its monitoring agent may already be compromised?**

Our scenario centered on ransomware interrupting a simulated patient-specific surgical planning/calibration workflow. We proposed an independent physical-monitoring path, **ARGUS**, to detect equipment-state changes even if the primary OT environment became unavailable. The project also incorporated an asset-focused Threat Intelligence Platform (TIP), a governance framework, and an incident-response exercise.

## Architecture at a glance

| Zone / component | Role |
| --- | --- |
| **Zone 1: Clinical / OT environment** | Simulated surgical planning workstation, control tower, imaging system, and agent appliance |
| **Zone 2: ARGUS out-of-band sensor station** | Raspberry Pi and physical sensors monitoring magnetic, environmental, and radio-frequency changes independently of Zone 1 |
| **Zone 3: Cloud monitoring** | AWS IoT Core, CloudWatch, Sumo Logic, Grafana, and alerting components in the capstone architecture |
| **Threat Intelligence Platform** | Next.js / Supabase / Vercel dashboard concept for mapping vulnerability and threat feeds to the simulated asset inventory |

The key design principle was **detection independence**: a separate physical telemetry stream could continue even when the monitored clinical environment or agent stopped reporting.

## Threat scenario

The training scenario modeled a multi-stage intrusion, beginning with credential compromise or remote access, followed by lateral movement, tampering with an AI-assisted monitoring configuration, and ransomware disruption of a simulated surgical planning file. The project mapped attacker behaviors to MITRE ATT&CK and considered patient-safety, operational continuity, and incident-response implications.

See [Threat Scenario](docs/threat-scenario.md).

## Detection engineering

The capstone explored three complementary sensor channels:

- **LIS3MDL magnetometer:** changes in magnetic-field signatures
- **BME688 environmental sensor:** temperature / humidity / gas-related deviations
- **Software-defined radio:** loss or change of a monitored RF carrier

The proposed compound-event logic required multiple sensor deviations within a shared observation window to reduce single-channel false positives. The team presentation includes Grafana sensor telemetry and a demonstration plan using magnets, heat, and radio proxies. These are **lab demonstrations**, not clinical validation.

See [Detection Architecture](docs/detection-architecture.md).

## Threat intelligence and governance

The project examined how to connect public CVE, CISA KEV, ransomware, and vendor information to a defined healthcare technology asset inventory. It also documented an ISO 27001-aligned governance approach with policies for information security, backup/recovery, and detection/response. This does **not** imply ISO certification.

See [Threat Intelligence & Governance](docs/threat-intelligence-and-governance.md).

## Incident-response exercise

The Delta 2 presentation included a **simulated GitHub personal access token exposure** and a response plan covering token revocation, investigation, secret rotation, containment, and prevention. **Melanie Aljabari was listed as Communications Lead**, responsible for timestamping actions and stakeholder notifications within the team exercise.

See [Incident Response Exercise](docs/incident-response-exercise.md).

## My contribution and professional relevance

**Melanie Aljabari | Delta 2 team member, Communications Lead (incident-response exercise)**

This team capstone gave me experience analyzing how cyber incidents can affect clinical operations and patient safety, documenting threat scenarios, connecting monitoring concepts to incident response, and communicating technical risks to stakeholders. It builds on my background in critical care medicine, medical investigation, and healthcare technology support.

This repository documents **collaborative coursework**. Architecture and demonstration results are attributed to the Delta 2 project; individual implementation ownership should not be inferred from the team deck.

## Documentation

- [Threat scenario and ATT&CK mapping](threat-scenario.md)
- [ARGUS detection architecture](detection-architecture.md)
- [Threat intelligence and governance](threat-intelligence-and-governance.md)
- [Incident-response exercise and my role](incident-response-exercise.md)
- [Evidence, limitations, and next steps](evidence-and-limitations.md)

## Tools and concepts covered

`AWS IoT Core` · `CloudWatch` · `Sumo Logic` · `Grafana` · `Raspberry Pi` · `MQTT / TLS` · `Python concepts` · `MITRE ATT&CK` · `Next.js` · `Supabase` · `Vercel` · `ISO 27001` · `Healthcare OT security`

## Source materials

Based on the Delta 2 **ARGUS Capstone Defense: Surgical Robotics** presentation and the WMCAT / NextCISO Academy **ARGUS Capstone Defense Workbook** (2026). The original presentation should be shared only after reviewing it for team permission, internal information, and credentials.

---

**Related work:** [Blue Team Security Investigations](https://github.com/melaniealjabari/Blue-Team-Security-Investigations) · [BlueHarbor SOC](https://github.com/melaniealjabari/BlueHarbor-SOC)
