# Incident Response Exercise: Simulated GitHub Token Exposure

## Exercise summary

The Delta 2 capstone presentation included a **simulated SEV-1 GitHub personal access token (PAT) exposure**. The scenario considered how a token with repository and workflow permissions could lead to unauthorized code changes, CI/CD compromise, or secret exposure.

**This was a training exercise, not a confirmed real-world breach.** No real token or secret is included in this repository.

## Team roles recorded in the presentation

The deck assigned an Incident Commander, Lead Handler, Support Handler, Communications Lead, and Technical Lead. **Melanie Aljabari was listed as Communications Lead**, with responsibilities for timestamping actions and notifying stakeholders.

## Response priorities

1. Confirm the report, severity, and incident ownership.
2. Revoke the exposed credential and verify it no longer authenticates.
3. Preserve relevant audit evidence and determine the exposure window.
4. Review repository, workflow, deploy-key, webhook, and CI/CD changes.
5. Rotate potentially exposed downstream credentials and assess their use.
6. Remove exposed secrets from active locations; assess history cleanup and coordinated remediation.
7. Restore only after verifying repository/workflow integrity.
8. Record decisions, stakeholder updates, lessons learned, and follow-up controls.

## Communications Lead responsibilities

- Maintain a timestamped incident timeline.
- Record confirmed facts separately from hypotheses.
- Coordinate concise status updates to technical and nontechnical stakeholders.
- Document who authorized containment and restoration decisions.
- Ensure handoffs and post-incident actions are captured.

## Controls emphasized

- Least-privilege, short-lived credentials
- Secret scanning and push protection
- CI/CD workflow review and branch protection
- Audit logging and evidence preservation
- Credential rotation and incident playbooks

## Professional relevance

This exercise directly connects prior emergency-response and medical-investigation experience with cybersecurity incident management: structured communication, precise timelines, cross-functional coordination, and evidence-based escalation.
