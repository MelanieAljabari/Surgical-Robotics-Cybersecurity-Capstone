# ARGUS Detection Architecture

## Design goal

The ARGUS capstone explored out-of-band monitoring: observe physical signals from a process independently of the monitored enterprise/OT network. If an agent inside the OT environment is compromised, an isolated sensor path may still report changes in physical conditions.

## Conceptual data flow

```text
Simulated clinical/OT system (Zone 1)
          |  physical effects only
          v
Independent ARGUS sensor station (Zone 2)
  LIS3MDL magnetometer | BME688 environment | SDR RF
          |
          v
Edge event logic / Raspberry Pi
          |
          | MQTT over TLS
          v
AWS IoT Core (Zone 3)
          |
          v
CloudWatch / storage --> Sumo Logic monitoring
                         --> Grafana visualization
                         --> SOC escalation design
```

The architecture diagram in the team presentation also described a separate `AGENT_EVENT` stream from Zone 1 and an `ARGUS_PHYSICAL` stream from Zone 2. The intended detection signal was a discrepancy when the agent stream became silent or unreliable but the independent sensor stream continued.

## Three sensor channels

| Sensor | Physical property | Demonstration proxy |
| --- | --- | --- |
| LIS3MDL magnetometer | Magnetic-field deviation | Magnet |
| BME688 | Environmental deviation | Heat source / blow-dryer |
| Software-defined radio | Radio carrier change | Walkie-talkie and RF shielding |

The team deck described a **2.0σ threshold** and **30-second compound window** as part of the event-detection design. A combined trigger is intended to reduce alerts from isolated sensor noise. These values are scenario settings, not medically validated thresholds.

## Demonstrated vs. proposed

**Evidence described in the team presentation:** Grafana sensor telemetry, threshold visualizations, and counts of sensor events; a planned five-minute attack demonstration using lab proxies.

**Architecture/design elements requiring separate verification before claiming deployment:** end-to-end production reliability, independent cellular connectivity, the precise timing of alert delivery, integration of all three sensors, automated paging, and recovery of a live surgical system.

The deck mentions `compound_pending = 2` in its sensor evidence. That supports partial multi-channel detection, **not proof that all three channels triggered simultaneously**.

## Integrity and AI-agent threat model

The capstone also considered tampering with an AI-assisted Watcher / Reasoner / Actor pipeline. Its threat model included changing `watcher_config.json` and poisoning `/rag/docs/` so that an agent might incorrectly downgrade a critical event. The proposed integrity countermeasure used SHA-256 reference hashes stored in S3 Object Lock and a periodic configuration check.

**Key insight:** Independent physical telemetry may reveal a discrepancy when a software agent's interpretation cannot be trusted. This does not prove the cause of a shutdown or replace endpoint, network, or forensic evidence.

## Operational limitations

- A physical sensor can indicate an equipment-state change, but cannot by itself prove ransomware or file encryption.
- Environmental/RF signatures are highly dependent on site configuration and interference.
- A 30-second window trades sensitivity against false-positive control.
- An out-of-band design needs its own power, communications, integrity, and failure monitoring.
- Clinical use would require extensive validation, safety review, and vendor/hospital authorization.
