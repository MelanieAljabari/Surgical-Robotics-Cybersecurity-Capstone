# Threat Intelligence Platform and Governance

## Asset-focused threat intelligence

The Delta 2 capstone described a Threat Intelligence Platform (TIP) to help analysts prioritize public threat information against a simulated healthcare asset inventory.

**Conceptual stack:** Next.js, Supabase/PostgreSQL, Vercel, and scheduled ingestion of CVE/CISA KEV/ransomware/vendor information.

The purpose of the TIP was not to replace a SIEM. It was to answer **which external threats might matter to the organization's assets**, while ARGUS/Sumo Logic addressed internal monitoring.

### Matching methods in the workbook

| Method | Relative confidence | Caveat |
| --- | --- | --- |
| Exact CPE identifier | High | Depends on accurate asset inventory |
| Vendor + product + version | High | Version normalization matters |
| Vendor + product | Medium | May overmatch unaffected versions |
| Keyword fallback | Low | Requires analyst review |

The team presentation included dashboard routes, proposed account controls, ingest logging, and a weekly reporting workflow. Claims about ingestion percentages or time savings in the slides should be treated as **project estimates** unless backed by test evidence.

## ISO 27001-aligned governance

The team deck presented policy work covering:

- Information Security Policy
- Backup, Recovery & Business Continuity Policy
- Detection & Response Policy
- Asset classification and control mapping
- Statement of Applicability concepts

The workbook emphasizes that a student team can document an ISO 27001-aligned management approach **without being ISO 27001 certified**. Planned controls must not be represented as implemented controls.

## Healthcare considerations

A realistic healthcare incident review would involve:

- Patient-safety and clinical downtime procedures
- Evidence preservation and incident communications
- HIPAA security and breach analysis when electronic protected health information is involved
- Device manufacturer and hospital responsibilities under applicable FDA requirements
- Recovery authorization and validation before returning equipment to clinical use

Regulatory obligations are fact-specific. This portfolio does not assert that a simulated event automatically triggers a specific notification deadline or that the modeled device has a particular FDA class.

## Practical takeaway

Detection, intelligence, and governance address different questions:

1. **ARGUS / monitoring:** What changed inside the environment?
2. **TIP:** What external threats are relevant to our assets?
3. **Governance:** Who owns the risk, who responds, and how is recovery controlled?
