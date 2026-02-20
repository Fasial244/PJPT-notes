# Cleaning & Reporting

After exploitation and post‑exploitation activities, ethical hackers must restore the environment to its original state and document their findings.

## Cleaning up

- **Remove malware and backdoors:** uninstall agents (e.g., Meterpreter), scheduled tasks, registry keys and persistence mechanisms installed during the test.
- **Delete created users and files:** remove any accounts or files created for exploitation.
- **Clear logs cautiously:** only remove your own artifacts; do not indiscriminately wipe logs unless agreed, as they may be needed by administrators.
- **Reset passwords:** change any passwords you compromised or created during credential stuffing or password spraying.
- **Restore services:** undo configuration changes (e.g., re‑enable firewalls or services) made during exploitation.

## Reporting

Documenting your actions and findings is as important as the technical work.  A professional report should include:

- **Executive summary:** high‑level overview for non‑technical stakeholders.
- **Methodology:** describe each phase – reconnaissance, scanning, exploitation, privilege escalation, lateral movement and cleanup.
- **Findings:** list vulnerabilities with severity ratings, evidence (screenshots or logs) and remediation advice.
- **Recommendations:** provide actionable steps to mitigate each issue.

Refer to the provided report template in `docs/labs/report` for structure and wording.
